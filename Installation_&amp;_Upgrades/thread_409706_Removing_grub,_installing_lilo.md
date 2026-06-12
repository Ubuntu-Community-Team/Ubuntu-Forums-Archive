---
title: "Removing grub, installing lilo?"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by matth1 on 2007-04-14
I have a problem with grub that i just can't seem to solve. Rather than spending another 3 days trying to fix it, I was wondering how I would go about removing grub and installing another boot loader, such as lilo.

---

### Post by taurus on 2007-04-14
I don't think you have to remove GRUB from MBR.  Just create a /etc/lilo.conf and then install it with

```
sudo lilo
```

---

### Post by matth1 on 2007-04-14
I used a text editor to create a lilo.conf file, then used sudo mv lilo.conf ~/etc

I believe this placed the lilo.conf in /etc

However using sudo lilo gave an error : sudo: lilo: command not found
Any hints?

---

### Post by confused57 on 2007-04-14
I've never used lilo, but this link should help:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

---

### Post by matth1 on 2007-04-14
Following that link... my fstab file looks very different.....

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

That is the entirety of my fstab file... that doesnt look right.

---

### Post by confused57 on 2007-04-14
> **matth1 said:**
> Following that link... my fstab file looks very different.....

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

That is the entirety of my fstab file... that doesnt look right.

That looks like the live cd fstab, can you boot into your Ubuntu install?

---

### Post by matth1 on 2007-04-14
No I can not.

---

### Post by confused57 on 2007-04-14
Did you see this section for installing lilo with the live cd?:
[http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD](http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD)

What problems are you having with grub booting your system?

---

### Post by Herman on 2007-04-14
Hello matth1,
I'm the author of the web page confused57 referred you to. As far as I know LiLo hasn't been updated to cope with the UUID numbers we have in our new /etc/fstab files these days, that's why we need to revert our fstab line for Ubuntu to the old style to use LiLo.

You are given a command to make a backup of your fstab file in that web page before editing the file. If you did that you should not have any major problem, all you need to do is mount your Ubuntu file system in your live CD and restore the backup you made of your /etc/fstab file. :D

This link will help you mount your Ubuntu file system in the Live CD,                                [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
Then all you need to do is this, ```
sudo cp /media/ubuntu/etc/fstab.backup /media/ubuntu/etc/fstab
``` After that your system should be back to normal even if something did go wrong. You will probably need to do that before you'll be able to boot, since the /etc/fstab file in needed by the system during boot-up. I don't think you'll be able to boot without it. In fact I'm sure you won't.

If you need specific help, (you have trouble mounting in the LiveCD), please post a copy of the output of 'sudo fdisk -lu' here and I can give you the exact commands to mount your system.
If you neglected to make a backup copy of your /etc/fstab file, we can probably make you one that will do the job well enough for you to cope, and you can copy that one into place and boot.

Regards, Herman :D

---

### Post by confused57 on 2007-04-15
Thanks Herman, that's good information to know that lilo can't handle the UUID method of identifying partitions.

---

### Post by Herman on 2007-04-15
Well, it couldn't last time I checked, which would have been the date that web-page was last edited, I think. 
Here's the feedback I got when running liloconfig,
```
 herman@rocky:~$ sudo liloconfig
       LILO, the LInux LOader, sets up your system to boot Linux directly
       from your hard disk, without the need for a boot floppy.
           
           WARNING!
               Your /etc/fstab configuration file gives device UUID=fded2ced-53ea-4dfa-bdb3-e4fd0b7a4fd3 as the root
               filesystem device. This doesn't look to me like an "ordinary" block
       device. Either your fstab is broken and you should fix it, or you are
       using hardware (such as a RAID array) which this simple configuration
       program does not handle. 
             
       You should either repair the situation or hand-roll your own
       /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
       again to retry the configuration process.
       Documentation for LILO can be found in /usr/share/doc/lilo/.
```
Regards, Herman :D

---

