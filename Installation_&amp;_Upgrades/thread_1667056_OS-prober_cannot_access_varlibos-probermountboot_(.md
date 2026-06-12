---
title: "OS-prober: cannot access /var/lib/os-prober/mount/boot (different)"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by pwright2 on 2011-01-14
Yes, I know there are already a lot of these posted.  I've been reading them.  The solutions posted have not worked for me.  Well, OK, I haven't tried the 'reinstall GRUB 2' nuclear option.  But, really.

Like most, what I have is a computer (netbook really) running Win7 starter that I have installed Kubuntu 10.10 32 bit in a partition (sda7).  Unlike most of the other complainants, GRUB shows me the Win7 partition just fine.  Everything works.  So, all I really want to do is (1) give me more than 10 seconds to respond to the GRUB menu and (2) perhaps change from default Kubuntu to Default Windows.  Actually, one of the edit entries I found indicated that GRUB should be able to remember which I booted to last and default to that, which would be kind of nice.  Or even set the timeout to -1 so it always waits for me.

Anyhow, since I cannot get sudo update-grub to work, all of this is moot.  Everything seems to work until the end of the script where I get the dreaded "OS-prober: cannot access /var/lib/os-prober/mount/boot" message and GRUB's operation doesn't change.

So, the reason I'm posting is that every other thread I've read devolves into people saying that the SYSTEM partition has two folders /boot and /Boot and get rid of the /boot.  And this seems to work for many people ... but ... in my SYSTEM partition (sda2, the 100MB windows boot partition) there is only /Boot.  There is not, I repeat and emphasize NOT a /boot folder.  Yes, I'm looking at it with administrator privileges.  I use Krusader - root mode and show hidden files is turned on.  

OH.  Yes, I installed BURG.  It works fine but doesn't help my issues (although the brightly colored boot screen does catch my attention faster).  And I had the OS-prober problem before BURG.  I had hoped BURG would help.  

Any suggestions?  

-----Paul-----

---

### Post by pwright2 on 2011-01-20
No help here, huh?  Any suggestions as to where else to go ask?

---

### Post by Dr. Tyrell on 2011-01-21
The answer is ...
You must mount your second /boot in a proper path.
For instance, if currently running on /dev/sda1, you should mount /dev/sdb1 to somewhere....anywhere....like /mnt/

The prober only looks in mounted volumes.

For my lappy I have treble-boot, and so os-prober is a HUGE time saver.

My laptop:
/dev/sda1 = windoze (sorry, it's for wife)
/dev/sda2 = /boot
/dev/sda6 = /

/dev/sdb1 = /boot
/dev/sdb6 = /

/dev/sdc1 = /boot
/dev/sdc6 = /

In each of those installations I have created top-level dirs named 

/sdb-bsd_boot and /sdc-natty_boot 

mounted to their respective partition #1, their boot partitions.

I also have the respective partition #6 mounted to /sdb-bsd_root and /sdc-natty_root

VOILA

fyi, I've been doing this dual-booted for almost a year :)

The Doctor

---

### Post by Quackers on 2011-01-22
That would be if you have a separate /boot partition for your Linux system. You don't mount a Windows boot partition (or alter one) to fix a grub problem!

pwright2, please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

