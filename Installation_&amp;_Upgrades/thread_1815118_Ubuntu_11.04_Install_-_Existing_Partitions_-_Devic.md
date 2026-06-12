---
title: "Ubuntu 11.04 Install - Existing Partitions - Device For Boot Loader Installation"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by guimaster on 2011-07-30
Greetings,

 I have been dual booting XP and Ubuntu 10.04.

 XP has two partitions -> C: & D:

 Ubuntu has three partitions -> / & /home & /swap

 I want to install 11.04 on my Netbook without deleting my partition information. I just want to erase the 10.04 install on "/". The 11.04 install gives me an option that was never available in the past: "Device For Boot Loader Installation"

 Where should I install Grub? I just tried to install 11.04 & Grub in /dev/sda6 which is my "/" partition but that didn't work and I just get Grub errors on boot. Should I just install Grub into the default /dev/sda? Will I erase data if I do?

 Thanks

---

### Post by YesWeCan on 2011-07-30
You already had Grub installed to the MBR of your disk. So you should tell the 11.04 installer to put it at /dev/sda (which means the MBR area of sda).

Your existing Grub MBR boot code does not work with 11.04 Grub files. That's probably why you are getting errors.

If you have already installed 11.04 you just need to install Grub:
boot 11.04 live CD
[COLOR="Navy"]sudo mount /dev/sdan[/COLOR]  where n is the partition number of your Ubuntu root partition
[COLOR="Navy"]sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]


The whole thing is quite confusing. You would naturally expect to install the boot-loader to the Ubuntu partition. But that's not how it was designed. In fact, most of the Grub files are already in your Ubuntu partition in /boot/grub. But the way Grub works it needs two files installed right at the front of the disk, which consume about 50 sectors ahead of the first partition start. For advanced users who like living dangerously, it is possible to install one of the files to the start of a partition but this is discouraged and really the normal Ubuntu installer shouldn't let you do it.

---

### Post by guimaster on 2011-07-30
Thanks for the response. Your advice worked well.

 What didn't work well was changing my password with the 11.04 install. My encrypted /home directory was not accessible with the new password. So I reinstalled 11.04 again with the old password.

---

