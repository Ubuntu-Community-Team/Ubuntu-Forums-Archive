---
title: "New Installation, getting Grub Error 22"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by bobisculous on 2011-08-30
Hey Folks,

Here's what I've got: I just built a new machine using all new parts, except for the HDD. Decided to salvage one from my old Linux machine that I haven't used in a while. 

This drive had both Linux 9.04 and Windows XP on it. I installed 11.04 using a Live USB and everything seemed to go smoothly. I opted to do a custom install (probably the reason for the issue) and deleted the partition with Linux 9.04 on it and recreated it (to format). I know the Windows XP will not boot on the new machine, I have no interest in doing so. Just didn't want to fiddle with finding all files on it and moving them over so I could delete/format the partition. 

Anyhow, the new install tried to put after restarting and am getting: 

GRUB Loading stage1.5. 
GRUB Loading, please wait...
Error 22

I think what happened is the new installation of Ubuntu did not create a new GRUB file and is looking for the original partition with Ubuntu 9.04 and not finding it. It went from sda3 to sda6 I believe.

Can I simply recreate a new GRUB boot loader from the live USB, or edit the current one and tell it only to look for the new install of Ubuntu and nevermind the XP partition (just treat it as some files on another partition)? Or should I move everything off the drive and reinstall from zero?

It's been a while since I have done Ubuntu full time, and hope this new computer and install gets me back.
Thanks much,
-Cameron

[edit]Realized I should have said "New Installation over old, grub error 22" instead. Sorry about that.

---

### Post by oldfred on 2011-08-30
Yes, you still have grub legacy in the MBR and it is still looking for the now missing old install.

You should have had the option to install the boot loader to the MBR when you did the partiitons. The default is to install to sda otherwise.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by bobisculous on 2011-08-31
You sir, are awesome.

Worked perfectly, and thank you very much for your fast help.

-Cameron

---

