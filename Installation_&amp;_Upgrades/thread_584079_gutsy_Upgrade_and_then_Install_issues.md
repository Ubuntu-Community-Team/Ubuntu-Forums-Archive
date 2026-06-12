---
title: "gutsy Upgrade and then Install issues"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by byronsalty on 2007-10-20
I've been using Ubuntu since 04 but I'm so frustrated with Gutsy that I'm preparing to give up and I'm currently downloading Fedora in case I can't get it to work soon. That's not a threat, I just have to have something running before work on Monday.

I had Feisty Fawn (fresh install) on my Dell Latitude D800 until Friday when I decided to upgrade. I made sure I had all the upgrades to Feisty first.Then I ran the update from the Upgade Manager. After all the downloads were complete, I got the message about some packages being deprecated. Then the installs started happening. I started seeing a lot of messages about packages not installing correctly but my only option was the "Cancel" button which canceled that package but the upgrade continued. The first few seemed like these might be something to do with the deprecated packages and not too important. After a while serious things like open-ssl failed and I noticed that I could no longer scp files during the install. I knew something was going horribly wrong. When the "upgrade" completed, I restarted and voila "Kernel Panic". 

Ok well I guess I'll re-install from scratch. I have my drive partitioned up so I won't lose anything important - it's just a pain to have to re-install and get everything to work properly again. (Like what? Well for one I spent a couple hours a month ago to install nvidia drivers so that I could finally get my laptop to work with projectors correctly.)

The install went normal enough - seemed like the Feisty install except when the reboot happened I ended up on the command line. That's odd. In the past I've had video issues or otherwise gdm issues and usually there's all kinds of error messages and "hey check so and so log" messages. Nothing. Well mostly nothing. All I get are these few lines before the login prompt:
```

Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/...) = sda4(8,4)
kinit: trying to resume from /dev/disk/by-uuid/...
kinit: No resume image, doing normal boot...

```
I looked around the /var/log directory but nothing stood out. I'm not really sure what I should be looking for in there anyway with this. sda4 is my CD drive, I believe, so I think it's just basically saying that the last boot was from the Live Install CD which isn't found the second time so time for the "normal boot".

I checked and the iso I got is indeed for the desktop version because this looks like a server's normal boot. 

I did try a manual restart of gdm: ```
sudo /etc/init.d/gdm restart
```
Which failed on the startup part. I don't think I checked the logs after that. 

I'm just frustrated after a failed upgrade and failed clean install.

---

### Post by byronsalty on 2007-10-24
Well I installed Kubuntu 7.10 and that's working for me. Not sure what's up with the Gnome versions but at least I have a working computer - even if I have to learn a new window manager.

---

### Post by waffen on 2007-11-08
Helllo,

check this:

[http://ubuntuforums.org/showthread.php?t=584692&highlight=kinit]("http://ubuntuforums.org/showthread.php?t=584692&highlight=kinit")

---

