---
title: "Wierd GRUB issue when migrating 9.10 upgrade to new hard drive"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by dcrooke on 2010-04-04
I've been using Ubuntu for a long time, and I consider myself pretty knowledgeable about it. However, I got tripped up yesterday when replacing the hard disk in my laptop (the old one had been dropped on its head once too often, and the SMART error prompts were making me nervous).

BTW, Dell has overstocked WD Scorpio Black drives, I got a 250GB one for $53 with free shipping :-) Didn't want to shell out for SSD.

Here is my usual procedure when migrating to a new drive, which has worked dozens of times on both server and laptop systems ... it got me thinking, is there a tool to automate this?

1. Boot from LiveCD or into single user mode

2. Attach new drive, e.g. with a USB adapter

3. Partition and format the new drive to taste (fdisk, mkswap, mke2fs -j, etc.)

4. Copy over Windows and Thinkpad maintenance partitions using dd (well, I no longer bother keeping a Windows one, but somebody might :-)

5. mount the old and new ext3 filesystems

6. Copy with something like this:

root#  [FONT="Courier New"]cd /old ; tar clfp - . | ( cd /new ; tar xvlpf - )[/FONT]

The reason I do this instead of dd is so I can resize and effectively defrag as its copying, and it's not much slower.

7. [FONT="Courier New"]grub-install --root-filesystem=/new /dev/sdb[/FONT]      

8. Shut down, switch out the drives and reboot


My current home laptop was installed with Ubuntu 7.x way back when, and upgraded using Synpatic Package manager to 9.10, and this trick did not work ... I got dropped to a grub-sh> prompt on boot.

After some online research, I found out why:

a. 7.x used the original GRUB

b. A new 9.10 install uses a beta of GRUB2, and that is what is on the 9.10 install CD (actual GRUB version is 1.97beta)

c. A Synaptic upgrade does *not* migrate you to GRUB2

d. Therefore, the GRUB2 version of grub-install could not find any of its meta-data files, and it silently failed.


Solution:

a. Obtain the original Super GRUB CD (*NOT* the GRUB2 version, the latest version of the old one ... I used SGCD 0.997 or something like that, dated October 2009)

b. This is a kinda funky tool ... its OS is GRUB itself, and its menus are done with hundreds of menu.lst files :-)

c. Follow the prompts for the "GRUB and Linux auto-repair"

d. You will get "error 6" because you are overwriting a newer version of the GRUB binaries with an older one.

---

