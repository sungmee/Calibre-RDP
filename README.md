# Calibre 电子书图形用户界面和服务端

可运行在 Web 浏览器中访问和管理的 Calibre X 应用 容器。这是 [aptalca/docker-rdp-calibre](https://github.com/aptalca/docker-rdp-calibre) 的 Fork 分支，主要在原来 基础上增加了 **文泉驿微米黑字体** ，以适应 Calire 图形界面的中文显示，并且翻译了说明文件。

## 安装：

在安装有 Docker 应用的系统平台上，您可以用下面的命令开始一个 Calibre 容器：

```shell
docker run -d --name=calibre -e APP_NAME="Calibre" -e WIDTH=1280 -e HEIGHT=720 -e USER_ID=1000 -e GROUP_ID=1000 -e EDGE=0 -e TZ=Asia/Hong_Kong -v /path/to/calibre:/config:rw -p XXXX:8080 -p YYYY:8081 sungmee/calibre-rdf
```

### 设置说明
- 变量 `APP_NAME` 为图形用户界面的标题名称，可以修改为您青睐的名字。
- 如果您想更改图形用户界面的分辨率，可以修改 `WIDTH` 和 `HEIGHT` 变量。
- 如果您想更改运行容器的用户和用户组，可以修改 `USER_ID` 和 `GROUP_ID` 变量，这在 Docker 宿主系统为 Linux 时非常有用，可在宿主机终端中用 `id` 命令获取。
- 如果您想获取 Calibre 的最新版本，请将 `EDGE` 变量更改为 `1`，容器每次重新启动时都会将 Calibre 更新为最新版本。
- 修改 `TZ` 变量为您的时区，参考 [List of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。
- 将变量 `/path/to/calibre` 替换为您需要的宿主系统文件夹。 这是 Calibre 的配置文件和库文件所在的位置，它们将在容器的更新，重新安装等后继续存在，使您的数据持久化。
- 将 `XXXX` 更改为您需要的端口，这是运行 Calibre 图形用户界面的端口。
- 将 `YYYY` 更改为您需要的端口，这是运行 Calibre 网络服务器的端口。
- *重要信息：首次启动图形用户界面时，请务必选择 `/config` 作为 Calibre 向导中的库的位置。
- Calibre 网络服务器可以通过在图形用户界面上的 `首选项/分享/通过网络分享` 选项卡设置和启用，注意 **端口必须设置为 `8081`**。

您可以通过 Web 浏览器访问 Calibre 的图形用户界面，链接为 http://您的域名或服务器IP:XXXX

您可以通过 Web浏览器访问 Calibre 的 Web 服务器，链接为：http://您的域名或服务器IP:YYYY

(替换 `XXXX` 和 `YYYY` 为您启动 Docker 容器时的设置)
