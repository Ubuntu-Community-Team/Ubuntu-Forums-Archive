---
title: "Installing Ubuntu Server on VMware on Windows XP"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by utahcon on 2008-02-01
I am trying to install Ubuntu Server 7.10 on VMware onto of Windows XP SP2.

During Install (after the Ubuntu Splash Screen) I get a screen that appears to be scanning hard drives [sda - sdx].

Eventually Ubuntu Server install will start, and it goes through pretty smoothly.

After the install is complete a reboot is required, and when it comes back up it continues to scan hard drives, that don't exist and it just keeps going, never actually boots into Ubuntu Server. I can provide screen shots, but they are pretty much just the OS looking for hard drives.  

Has anyone else run into this? I can't seem to find any answers on google or ubuntuforums. Thanks!

---

### Post by utahcon on 2008-02-05
I can expand on this issue.

I have now tested this a little more on Kubuntu (7.10) with VMware Server installed as well. It appears the problem happens when I have more than 1 SATA drive defined in VMware. 

It will give me the Ubuntu Install splash screen, then a black screen as it scans through tons of non existent HDDs.

Will it do that if I have a physical machine with 3 harddrives in it?

---

