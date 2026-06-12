---
title: "linux won't load."
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by bitspheres on 2014-09-22
I have ubuntu 14.04 installed running xfwm4 desktop.  After recently being prompted to apply some updates linux will not boot.  After choosing the installation from grub2 nothing happens.

I have looked through some of the log messages but I don't see anything that looks like something definitive but I don't know what I am looking at.

I did see this in the boot.log that could be meaningful.

 * Starting configure network device security[74G[ OK ]
 * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 * Starting crash report submission daemon[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Restoring resolver state...       [80G 



Any help about what I should do would be appreciated.

---

### Post by yancek on 2014-09-22
Boot any Linux Live CD/flash drive and get online and search for bootinfoscript, download and run it and post the output here or go to the site below which explains using the boot-repair disk which output similar info but can also try to repair the bootloader.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bitspheres on 2014-09-22
Thank you, I will try it.

---

### Post by bitspheres on 2014-09-22
[http://paste.ubuntu.com/8405785/](http://paste.ubuntu.com/8405785/)

---

### Post by bitspheres on 2014-09-22
That fixed it.  Thank you @yancek.

---

### Post by yancek on 2014-09-22
The boot repair shows at the very end that Grub was reinstalled to the master boot record of your hard drive.  So either it was not installed there initially or was not installed properly.  If I understood your initial post, you had been using Ubuntu successfully for a period of time and did some updates.  Probably included in the updates was a new kernel and your grub did not get updated.  In the future you might keep an eye on what is being updated and if a new kernel is included, watch the output to see if update-grub is run.  If not run it manually.  Another thing for future reference, it you have more than one OS installed as you do, it is best to post that information initially.  Glad you got it working.

---

