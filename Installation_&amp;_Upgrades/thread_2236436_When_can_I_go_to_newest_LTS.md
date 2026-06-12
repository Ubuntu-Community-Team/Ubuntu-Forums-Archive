---
title: "When can I go to newest LTS?"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2014-07-26
I am running 12.04 on a homebuilt AMD 64 bit machine. Runs fine, but I would like to go to 14.04. I understand it is out and I thought it would notify me through update manager so I could upgrade directly without stepping through all in-between versions. But no notification. I can download, wipe and install but would rather do it the easy way. Can I, and if so, when?

---

### Post by kansasnoob on 2014-07-26
Automated notifications of the Precise -> Trusty upgrade were delayed because I discovered and filed this bug on the 23rd:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

The 14.04.1 images are available here:

[http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)

---

### Post by grahammechanical on 2014-07-26
If you are going to upgrade then do whatever it takes to bring your 12.04 desktop to a default condition and change the video driver over to the open source video driver. Otherwise, the easy step of a one click to upgrade could become much more complicated when it is finished and you reboot to a black screen with a flashing cursor.

Ubuntu 14.04.1 has just been released and users of 12.04 should be getting an invitation to upgrade when they run Software Updater. But it seems that there is a slight delay. Be patient or do it the harder way.

[http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/)

[http://cdimage.ubuntu.com/trusty/daily-live/current/](http://cdimage.ubuntu.com/trusty/daily-live/current/)

Regards.

---

### Post by slooksterpsv on 2014-07-26
You should be able to run, from a terminal, update-manager -c - to check for a newer release. 14.04.1 is out now so it should prompt you to upgrade. I'm not sure if the servers are a bit hammered by people grabbing the updates, possible, so try what I suggested with the update-manager -c

---

### Post by stephenbbb on 2014-07-27
> **slooksterpsv said:**
> You should be able to run, from a terminal, update-manager -c - to check for a newer release. 14.04.1 is out now so it should prompt you to upgrade. I'm not sure if the servers are a bit hammered by people grabbing the updates, possible, so try what I suggested with the update-manager -c

update-manager -c 

gives that there are no updates. Things are blocked from the repo. The version i have now is the hardware support update for 12.04 and it is much worse than the old one. when I suspend there is no coming back. Have to unplug from the power and remove the battery and then restart. afraid Ubuntu is becoming like windows: after XP things kept getting worse.

---

### Post by kansasnoob on 2014-07-27
> **stephenbbb said:**
> update-manager -c 

gives that there are no updates. Things are blocked from the repo. The version i have now is the hardware support update for 12.04 and it is much worse than the old one. when I suspend there is no coming back. Have to unplug from the power and remove the battery and then restart. afraid Ubuntu is becoming like windows: after XP things kept getting worse.

Did you even read [post #2]("http://ubuntuforums.org/showthread.php?t=2236436&p=13083670#post13083670")?

---

