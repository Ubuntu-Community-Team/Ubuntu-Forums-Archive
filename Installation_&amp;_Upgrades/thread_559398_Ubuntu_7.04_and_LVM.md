---
title: "Ubuntu 7.04 and LVM"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-09-25
I would like to describe my experience with installing Ubuntu with LVM and then ask some questions how to fix it ;-)

I tried the disk Ubuntu 7.04 desktop for AMD64, followed the description of [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)
I prepared the file system and tried to install, but the installation did not allow me to select a root partition. The selection window appeared as a one millimeter bar! After several tries I gave up and used my Ubuntu 6.06 alternate for AMD64 disk.

I was unable to overcome the problem to set-up the LVM at all. 
I gave up again, deleted the LVM partition and installed onto the free space.

I used for my NVIDIA GEforce 7600 a resolution of 1280x1024. It worked! Mouse, sound, ... everything seems to work. 

I decided to upgrade. The first choice was to upgrade to 6.10, ... done ! ok!

I upgraded to 7.04 and the monitor cannot show anything anymore. Even with switching to ALT-CTRL-F1 ~ F12, nothing than garbage.

Windows is still installed, so I booted XP, downloaded Ubuntu 7.04 alternate for AMD64 and started again to install, by first freeing up the space and try to use LVM. Again, I was unable to install LVM. To  create the lmvolume /dev/hdb3 failed all the time. 
I switched to console 2, and created with:
pvcreate /dev/hdb3  
switched back to the console 1 and continued to set-up the logical volumes, waiting for each volume about 3 minutes till the screen comes up again.

The system recognized my network cards eth0, eth1 and ra. The cable was connected to eth1.

After installation, the system reboots and I can choose the installed Ubuntu version. I chose the first one kernel generic.
The screen is garbage again!!!!

I reboot and use another version from Grub, this time the amd64 generic and it boots up with a screen, but NO mouse, NO sound.


QUESTIONS:

1. since I have a AMD CPU, it should work with a AMD64 kernel. Why was generic (without 64) installed at all?

2. How can I get mouse back, so that I can go the next step. BTW, is there no way to use keyboard only to go to the menues?

3. During the previous installation my sound card worked, now not anymore. How can I fix that?

4. How do I get the right / newest NVIDIA driver?

Thanks!

Bye

Ronald

---

### Post by riceyeh on 2007-09-25
I am not answering your question but asking you a question in *[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)* you mentioned. I am studying the article. In the *3.Finalizing the install* of the article, 'sudo chroot /target' is used. I wonder what '/target' is? Is it the system just installed? I doubt 'sudo chroot /target' will work. 

Regards,
Rice

---

### Post by ELMIT on 2007-09-28
Can anybody give me a hand on how to solve the problem?

bye

Ronald

---

### Post by ELMIT on 2007-10-17
I am still on the same spot. Has anybody an idea where to start to track down that problem?

When I boot I see many messages flying by with modules.dep not found.
Could that be the reason? How to fix that?

bye

Ronald

---

