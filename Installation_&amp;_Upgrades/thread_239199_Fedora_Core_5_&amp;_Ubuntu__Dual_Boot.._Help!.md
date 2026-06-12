---
title: "Fedora Core 5 &amp; Ubuntu : Dual Boot.. Help!"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Danny Boy on 2006-08-18
Hi guys, 

  I'm having a few problems. I installed FC5 and had to completely reformat my hard drive in order to install, needless to say I wasn't all that impressed. I quickly reformated and went back to Ubuntu. 

  I'm giving FC5 another chance it's installing on my desktop again as I type. I again had to reformat my entire HD, as FC 5's installer seems to not be able to partition my exsisting Ubuntu partition.

  Here's what I'm running: 

  [LIST]
[*]Pentium 4 1.7 Ghz
[*]  512 RAM
[*]  80 GB Hard drive
[/LIST]

What I'd really like to do is have both Ubuntu & FC5 share the same home partition. Is that possible? If not, I'd like to essentially split the HD down the middle giving 40GB to each OS. 

After the FC5 install, I'm going to try and install Ubuntu, last night when I tried to create additional partitons for Ubuntu separete from the FC5 install, the Ubuntu installer spit out all kinds of errors. 

If it helps any both distros us Grub for the boot loader.

Any suggestions? 

Thanks in advance, 
Dan

---

### Post by Phantom784 on 2006-08-18
You could have them share home directories by creating a third partition that is mounted on /home for both operating systems.  However, this may create problems since many configuration files are stored in /home.

---

### Post by Danny Boy on 2006-08-20
I was able to get both installed with realitive ease. I downloaded the gparted live CD, and partitioned my main partion with that. 

The only problem I have is I cannot make Grub "understand" how to boot both OS. I successfully edited the menu.list but Grub spits out an error when I tried to boot Ubuntu. 

So.. I formatted and reinstalled Ubuntu again. Any ideas on how to install FC5 and make Grub boot the ubuntu partition?

---

### Post by viranaso on 2006-08-20
As stated by Phantom784 you could make a separate partition for /home but there is a snag with sharing your personal files between multiple distros. Ubuntu gives the first user a UID of 1000 whereas Fedora starts at UID = 500. This means that files created by one distro appear to the other distro to belong to another user. If you create other users you can set the UID to whatever number you like, but I don't know whether one can change the first user without wrecking a few things.

Whichever distro you installed last is usually the one whose grub configuration is being used. I installed Ubuntu Dapper last and my menu.lst file contains these lines for the two distros:
[CODE]
default                 0
# Ubuntu installed on /dev/hda8
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
# linux installation on /dev/hda4.
title           Fedora Core 5 (2.6.15-1.2054_FC5) (on /dev/hda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=/1 rhgb quiet
initrd          /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot
[CODE]

You may need to edit the text for the "foreign" one, in this case Fedora.

---

