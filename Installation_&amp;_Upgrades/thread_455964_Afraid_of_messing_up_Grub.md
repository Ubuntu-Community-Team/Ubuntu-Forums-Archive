---
title: "Afraid of messing up Grub"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2007-05-27
I need to install win2k to run some programs. I mainly use Ubuntu but have to use win this time. I started the installation to  a fresh drive but win2k says it needs to write a file to my main boot disk which contains Ubuntu. I fear this will wipe out my Grub and so I will not be able to start Ubuntu. What should I do so that  I can have dual boot. I do not want to reinstall Ubuntu just to get back the  grub.

---

### Post by spd106 on 2007-05-28
I'm afraid there isn't much you can do to stop it. This docs page will help you configure the dualboot afterwards [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by docinthebox on 2007-05-28
Since you have win2k and Ubuntu on separate drives, if you don't want to mess with grub, you can dual-boot by using the boot menu of your BIOS to switch between booting from either drive.

Before you install win2k, just disconnect the Ubuntu drive.  This way, there's absolutely no way the win2k installation can mess up anything on the Ubuntu boot drive.

But in the long run, it's worthwhile to take an hour or two to learn grub to some detail, as it's indeed a very useful tool, both in multi-boot and in failure recovery situations.

---

