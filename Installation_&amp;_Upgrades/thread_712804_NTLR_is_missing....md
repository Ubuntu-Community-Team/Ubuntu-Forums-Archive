---
title: "NTLR is missing..."
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by shaloob on 2008-03-02
Hii,
I installed grub as specified in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) . 
But now when system boots grub got loaded n when ubuntu i clicked it says partition not found... n if Vista(which i already installed) is clicked it shows NTLR is missing...
PLZZZZ HELP ME.... I wanna get my windows back and also want to boot from ubuntu which i already installed....

---

### Post by shaloob on 2008-03-02
Plzzzzz Reply.......

---

### Post by Herman on 2008-03-02
:) Hello shaloob,
Here, go to this website: [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"), and read it and download a CD or a floppy disk image from there with NTLDR, NTDetect.com and boot.ini in it. That should bypass just about any Windows booting problem you can have. I don't know much about Vista but I guess it will work for Vista too, let me know if it doesn't.
The problem could either be your partition number has been accidentally changed somehow and you just need to edit boot.ini with the new partition number, or you changed the order or your hard disks and you need to use GRUB's map commands. In either of those two cases, NTLDR isn;t really missing.
There is a possibilty of NTLDR really being missing if you set up a Windows dual boot the default Microsoft way and have deleted your old Windows to install Ubuntu.  Windows copies it's boot loader files to the oldest installation, I don't know why.
Anyway, that CD or floppy disk download should help you for now.

Regards, Herman :)

---

### Post by Herman on 2008-03-02
Once you can boot maybe you'll feel a lot happier and you can then boot your Ubuntu Live CD again and send us a copy of 'sudo fdisk -lu' and the bottom half of your /boot/grub/menu.lst file from your Ubuntu installation.

Here's a link about how to use your Ubuntu Live CD to gain access to your Ubuntu system and get a few of the vital files that sometimes need to be edited in this way to get Ubuntu to boot, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") .
Hopefully you will be able to figure out how to do that from that web page. If you have trouble, as again here for more help. The idea is first to mount your Ubuntu system and then get a copy of your /boot/grub/menu.lst and post it here so someone can tell you how to fix it.

Who-ever helps you will also need your hard disk and partitioning details from the output of 'sudo fdisk -lu' from the Live CD,
```
sudo fdisk -lu
```P.S., you can also boot Ubuntu with [Super Grub Disk Webpage]("http://sgd.benjamin-butschko.de/") if you prefer, (and Super Grub Disk might even boot your Windows too), and get the /boot/grub/menu.lst information that way if it's easier for you.

---

### Post by shaloob on 2008-03-02
Thanx 4 ur reply boss.........

---

### Post by Deeee on 2008-03-02
This is the exact same problem im having at the moment, my harddrives are detected in a different order for the bootloader than from when im into the OS. drive 2 being drive 0 when im at grub, and back to being drive 2 when im in ubuntu. still havent fixed windows booting yet (doing that now) but to get ubuntu to boot, on the grub menu i ended up editing the option thingy and changing (hd2,2) to hd(0,2) and it booted fine

---

