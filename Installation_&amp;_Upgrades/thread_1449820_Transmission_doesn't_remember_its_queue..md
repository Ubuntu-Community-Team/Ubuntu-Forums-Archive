---
title: "Transmission doesn't remember its queue."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Resilldoux on 2010-04-08
Hi there,

It has occurred to me that everytime I reboot my Ubuntu server, Transmission doesn't remember its queue for some reason. Now, there's nothing wrong when I download and seed torrents, it's just that I'm forced not to reboot my server so it doesn't forget its queue. Note that I'm using the neat transmission-daemon because I'm running it on an Ubuntu server.

I installed Ubuntu Server 10.04 Beta 1 with the transmission-daemon (v1.92) and configured the settings script, as well as the /etc/init.d/transmission-daemon entry.

**/etc/transmission-daemon/settings.json**:
```
{
    "blocklist-enabled": 0,
    "download-dir": "/media/DATA-E/Resilldoux/My Downloads/Transmission/COMPLETE",
    "incomplete-dir": "/media/DATA-E/Resilldoux/My Downloads/Transmission/TEMP",
    "incomplete-dir-enabled": true,
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 1,
    "max-peers-global": 200,
    "peer-port": 51413,
    "pex-enabled": 1,
    "port-forwarding-enabled": 0,
    "rpc-enabled": 1,
    "rpc-authentication-required": 1,
    "rpc-password": "Elysium",
    "rpc-port": 9091,
    "rpc-username": "Resilldoux",
    "rpc-whitelist": "127.0.0.1,192.168.*.*",
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "trash-original-torrent-files": 1,
    "watch-dir": "/media/DATA-E/Resilldoux/My Downloads/Transmission",
    "watch-dir-enabled": 1
}
```**/etc/init.d/transmission-daemon**:
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          transmission-daemon
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop the transmission-daemon.
### END INIT INFO

TRANSMISSION_ARGS="-g /etc/transmission-daemon"
NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=debian-transmission
# FIXME: no pidfile support; forks, so --make-pidfile doesn't work either
#PIDFILE=/var/run/$NAME.pid
STOP_TIMEOUT=3

export PATH="${PATH:+$PATH:}/sbin"

[ -x $DAEMON ] || exit 0

[ -e /etc/default/$NAME ] && . /etc/default/$NAME

. /lib/lsb/init-functions

start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled, see /etc/default/${NAME})"
    else
        start-stop-daemon --start \
        --chuid $USER \
        --exec $DAEMON -- $TRANSMISSION_ARGS
    fi
}

case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        start_daemon
        log_end_msg 0
        ;;
    stop)
        log_daemon_msg "Stopping bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo
        log_end_msg 0
        ;;
    reload)
        log_daemon_msg "Reloading bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON \
            --oknodo --signal 1
        log_end_msg 0
        ;;
    restart|force-reload)
        log_daemon_msg "Restarting bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo
        start_daemon
        log_end_msg 0
        ;;
    *)
        echo "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart}"
        exit 2
        ;;
esac

exit 0

```So, note that I added the following line to make sure the transmission-daemon uses the right settings.json file:
```
TRANSMISSION_ARGS="-g /etc/transmission-daemon"
```...and edited these lines:
```
start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled, see /etc/default/${NAME})"
    else
        start-stop-daemon --start \
        --chuid $USER \
        --exec $DAEMON -- $OPTIONS
    fi
}
```...to these lines (So, note that $OPTIONS is changed to $TRANSMISSION_ARGS):
```
start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled, see /etc/default/${NAME})"
    else
        start-stop-daemon --start \
        --chuid $USER \
        --exec $DAEMON -- $TRANSMISSION_ARGS
    fi
}
```These edits were necessary because the lack of these edits prevented the transmission-daemon to actually use the settings in the/etc/transmission-daemon/settings.json file (and therefore prevented me to access the web interface). Personally, I thought that was kind of strange because isn't that file supposed to be the default settings file the daemon should be configured to automatically look for? Anyhow, I succeeded to create a work-around for that problem, but it still doesn't remember its queue whenever I reboot my server...

---

