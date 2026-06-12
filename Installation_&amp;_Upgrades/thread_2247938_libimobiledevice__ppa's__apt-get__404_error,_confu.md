---
title: "libimobiledevice / ppa's / apt-get : 404 error, confused"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by crackers_altitude on 2014-10-11
Ubuntu 14.04.1 LTS (trusty)

I want to try Rhythmbox with my iPhone - from what I gather, that means installing libimobiledevice. Essentially, I get a 404 error for the ppa attempts I have tried... I am also having trouble knowing what question to ask.

There are lots of pages on this topic that are outdated - e.g:

[http://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/](http://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/)
[http://askubuntu.com/questions/78535/how-to-install-libimobiledevice](http://askubuntu.com/questions/78535/how-to-install-libimobiledevice)
[https://launchpad.net/ubuntu/+source/libimobiledevice](https://launchpad.net/ubuntu/+source/libimobiledevice) <- is this the go-to source for libimobiledevice? where is the "how to install""? does "no registered releases" mean I am out of luck?

I am lacking in apt-get knowledge, though it seems it ought to be a forgiving installation. any pointers appreciated.

UPDATE:

found this:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

I guess I need to wait then?

UPDATE 2:

tried Banshee - works! found libimobiledevice:

lsof | grep libimobile
output:
/usr/lib/i386-linux-gnu/libimobiledevice.so.4.0.1

problem solved - sort of, would still be good to understand what is going on.

---

