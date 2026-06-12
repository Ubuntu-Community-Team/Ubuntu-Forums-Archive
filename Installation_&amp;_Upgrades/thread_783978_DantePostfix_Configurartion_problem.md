---
title: "Dante/Postfix Configurartion problem"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Crevu on 2008-05-06
hi guys,
trying to configure Postfix to use SASL for SMTP AUTH, but when i go to install libsasl2-2 and sasl2-bin i get this error that seems to be related to dante


Setting up dante-server (1.1.18-2.1) ...

Starting Dante SOCKS daemon: invoke-rc.d: initscript danted, action "start" failed.

dpkg: error processing dante-server (--configure):

 subprocess post-installation script returned error exit status 1

Errors were encountered while processing:

 dante-server


i realise that my danted.conf is probably configured very poorly, mind you, i can't find a decent tutorial to configure it properly.

any help would be greatly appreciated

---

### Post by Crevu on 2008-05-08
No one knows ey? meh, can't say i'm not surprised.
can anyone at least recommend a decent dante configuration tutorial then?

---

### Post by zoiks on 2008-05-29
I had the same trouble installing dante-server through the repositories. I would guess that the apt repository version is broken in some way.

But I had no difficulty installing it myself:

Download the tar-file from [ftp://ftp.inet.no/pub/socks/dante-1.1.19.tar.gz](ftp://ftp.inet.no/pub/socks/dante-1.1.19.tar.gz)

```
tar -zxvf dante-1.1.19.tar.gz
cd dante-1.1.19/
sudo apt-get install build-essential
./configure
make
sudo make install

```

I think my previous attempts to install dante-server left my /etc/init.d/ directory with a non-functional danted starter. (Points to a non-existent /usr/sbin/danted.) So I removed that, and created my own sockd starter file called "/etc/init.d/sockd":

```
#!/bin/bash

SOCKD="/usr/local/sbin/sockd"

case "$1" in
    start)
        echo "Starting sockd (dante)..."
        $SOCKD -D
        ;;
    stop)
        echo "Killing sockd (dante)..."
        killall $SOCKD
        ;;
    restart)
        echo "Killing sockd (dante)..."
        killall $SOCKD
        sleep 2
        echo "Starting sockd (dante)..."
        $SOCKD -D
        ;;
esac

```

and then

```
sudo update-rc.d sockd defaults

```

Yeah, kludgy but it works.

Now the configuration file, that's a different story. I'd share mine, but it's insecure so I wouldn't want people using it. For myself, I am firewalled off and can only connect using a port-forwarded ssh tunnel, so I'm OK. Anyway, you'll have to configure /etc/sockd.conf yourself.

---

