---
title: "Modprobe: FATAL error inserting padlock_sha"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by john_mc on 2010-10-27
Hey all,

I am looking for some support on resolving a boot problem as I am still really a novice and Google/forums have not yielded a fix. I am learning Ubuntu to move away from windows and built a machine but need help quickly here as a friend is asking for help with his PC.

Ubuntu server 10.04 installed on my PC and looked the GUI which worked no problem. After an update the system halts at the following error no matter what Kernel I boot on or associated recovery mode.

Modprobe: FATAL error inserting padlock_sha (/lib/modules/2.6.32.25-generic-pae/kernel/drivers/cryptoo/padlock_sha.ko) No such device.

In looking around I see this was a bug (or feature) back in 2008 that can be resolve by blacklisting the module padlock_sa. However since I can't boot into the recovery mode or normally then I can't try this. Any suggestions?

A number of kernels are installed with respective recovery modes but nothing works when selecting a different version form the GRUB menu;
2.6.32.25
2.6.32.24
2.6.32.21

My plan is use a LiveCD 10.10 which I am using on my laptop to reinstalling the GRUB2 loader using the guide - HOWTO: Purge and Reinstall Grub 2 from the Live CD - ttp://ubuntuforums.org/showthread.php?t=1581099.
Bad idea?

Ultimately I want to move away from the server version install and run the version off the LiveCD but I need to back up all his data. A slave drive is curent;y present with windows but I can't see any files on the Ubunut drive - Windows is IDE and Ubuntu is on a SATA drive. Is there a way of getting my files from the Ubuntu server version that has an encrypted home folder?

It would be very much appreciated if someone could point me in the right direction as searching the net for an answer has hit a brick wall.

Thanks,
John

---

### Post by john_mc on 2010-10-29
Folks my error still persists and any advice is appreciated?

Going to work on it this weekend and heading towards saving the data as my friends wants windows back.

Thanks in advance
JMc

---

