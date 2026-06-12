---
title: "moving /home to a seperate partition and adding swap"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by darkshadow on 2006-11-10
Ok I just had my hard drive completely die in my laptop and got a new one and wanted to change some stuff including partition layout

on my old layout I had
hda1 as factory installed diagnostics
hda2 as a edgy install
hda3 as a dapper install

on my new one I plan on
hda1 edgy install
hda2 empty for testing new version when I feel like it
hda3 as /home
hda4 as 1.5gb swap so I can hibernate my laptop

I used a livecd to partition my new drive and copied my edgy backup onto the first partition. I then modified /boot/grub/menu.lst and /etc/fstab to know that the install moved to a different partition.

In the fstab I got rid of the uuid stuff since they were for the old hard drive and I don't know how to find the new ones.
I then booted my system to test it quickly and everything works perfect I proceded to boot the livecd again and move everything under /home to hda3 and add a new line in the fstab but when I try booting my laptop it freezes just as it starts loading gdm which is the exact time it looks in my home directory for the custom gdm theme.

Did I miss modifying something to move my /home?

Also when I setup this laptop I didn't want swap space since I have used computers for years with 1GB of ram and never used it. But will that is still true for normal usage I would like to hibernate and need to know how to add swap after installing.

---

### Post by an.echte.trilingue on 2006-11-10
I think you should try to start over on your install, it will be faster than trying to fix the 8 million things that could be wrong.

There are all kinds of things that could have been messed up, depending on how you did your backing up.  First off, if you used cp, your file permissions are probably shot.  Even if you used tar, the uids of the files might not be the same as the uids on your new install.  The next time you try this, you should put all the files on your home directory in a folder called /home/backups, do your install, then log into the console on CTRL=ALT=F1 and use mv to move the files back into the folder /home/<username>, then use "sudo chown -R <username>:<username> /home/<username>/*" to give the files to <username>.  

Also, this is why I find it is better to put themes that you install yourself  in their proper system folders (/etc/gdm/themes/ in the case of grm themes) and simply spend an hour re-customizing your computer in the event of a fresh install than to try to put everything in /home; it just seems to go faster.

As far as adding swap is concerned, I am pretty sure you can just create the partition and format it as swap and the system will detect and use it on start-up...

Good luck, though!

-mat

---

### Post by aysiu on 2006-11-10
[quote=darkshadow]I proceded to boot the livecd again and move everything under /home to hda3 and add a new line in the fstab[/quote] Are you sure you moved *everything*. The /home directory has a lot of hidden files and folders inside of it. What command or by what method did you "move everything"? > but when I try booting my laptop it freezes just as it starts loading gdm which is the exact time it looks in my home directory for the custom gdm theme. GDM themes are not usually stored in your /home directory. They're usually in /usr/share/gdm/themes

---

### Post by darkshadow on 2006-11-10
My backup command was using a livecd

dd if=/dev/hda2 | ssh -c blowfish username@192.168.0.9 "dd of=hda2.img"

to restore I mounted hda2.img on the remote computer and on the live cd I mounted that directory using sshfs on the laptop and did used this command to copy the files

cp -a sshmnt/* hda2mnt/

the -a is archive which preserves permissions, preserves links, and is recursive

during the restoring I was root on both systems so there was no chance of problems reading files due to lack of permissions.

my laptop works perfect as long as I leave my home directory on the root partition so file permissions are still right.

---

