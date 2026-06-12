---
title: "kickstart issues"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by sbsers on 2012-02-08
hello,
I am wondering if someone can help me understand what is happening with a network installation i am setting up and testing.

Background:
I am using WDS as my pxe server. I have followed instructions on various websites and am currently able to pxe boot a VM from the network and begin the ubuntu installation.

I have a kickstart file hosted on an internal website. the kickstart file contains these lines.
```

#Install OS instead of upgrade
install
#Use Web installation
url --url http://test-wds.wds.test/ubuntu

```
I can in the syslog that the server is downloading my kickstart file correctly.
```

Feb   7 22:45:55 kickseed: Downloading kickstart file from http://192.168.132.10/Kickstart/Ubuntu.cfg
Feb   7 22:45:55 kickseed: Reading kickstart file from /var/spool/kickseed/fetch/http/192.168.132.10/Kickstart/Ubuntu.cfg

```
I have verified in the shell that this is my file. A bit later in syslog i see this
```

Feb   7 22:45:55 preseed: successfully loaded preseed file from /var/spool/kickseed/parse/preseed.cfg

```
I have checked this file and it appears to have all teh correct settings from the kickstart file converted to a preseed file

So far everything looks good. the problem happens when the install tries to connect to the source.

As the install is going through the file i see it do netconfig and get a dhcp address. then i gets to the following (cutting off the dates since i'm typing this out manually)
```

INFO: Menu item 'choose-mirror' selected
anna-install: Queueing udeb apt-mirror-setup for later installation
choose-mirror DEBUG: command: wget -q http://gb.archive.ubuntu.com/ubuntu/dists/maverick/releaste -0 - | grep -E '^(Suite|Codename):'
choose-mirror INFO: mirror does not have any suite symlinks
choose-mirror DEBUG: command: wget -q  http://gb.archive.ubuntu.com/ubuntu/dists/maverick/releaste -0 - | grep  -E '^(Suite|Codename):'
choose-mirror: WARNING **: mirror does not support the specified release (maverick)
main-menu: wget: bad address 'bg.archive.ubuntu.com

```

my question, why is it trying to connect to an external resource? i specified an internal address and it appears to have parsed it but is not using it. What am i doing wrong?

(I am using the alternative install cd as my source)

---

### Post by sbsers on 2012-02-08
Bumping this since posts seem to get burried to page 3 around here quickly :)

---

### Post by LukeMP on 2012-03-24
Hello, did you get an answer to this? I was about to make a thread about the exact same issue, but before I did I searched to make sure it hadn't already been solved.

I am doing a PXE install on a totally isolated network, but I still see the same messages in the syslog as the OP. Is there any fix for this?

Any help is appreciated

---

