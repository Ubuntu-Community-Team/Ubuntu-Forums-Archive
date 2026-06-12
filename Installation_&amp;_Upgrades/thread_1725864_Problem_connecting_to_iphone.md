---
title: "Problem connecting to iphone"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by _Aries_ on 2011-04-10
I have been trying to research this topic for a while now, trying to connect to my iphone iOS 4.2 (jb). 

I get this error when connecting it:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I've found some solutions to this and this is what I tried:

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

But whenever I do the apt-get dist-upgrade, I get this error:

Errors were encountered while processing:
 /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there a way to fix this? I think this is my problem. Im running Ubuntu 10.10, connecting to Banshee.

---

### Post by _Aries_ on 2011-04-10
no one knows?

---

### Post by wigout on 2011-05-07
I've been having this trouble too-

It had been working for me and then libimobiledevice failed to update.

I took these steps:
```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```which eventually gave this error:
```
Preparing to replace libimobiledevice1 1.0.4-1ubuntu1~maverick1  (using .../libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb) ...
Unpacking replacement libimobiledevice1 ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb (--unpack):
 trying to overwrite  '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi',  which is also in package libimobiledevice0 0.9.7-1ubuntu1

```I used synaptic to remove/uninstall libimobiledevice0
Then I used synaptic to upgrade/install libimobiledevice1

I haven't yet connected my ipad to double check that it works, but the upgrade error I had been receiving:

Let me know if that works for you,
wigout

---

