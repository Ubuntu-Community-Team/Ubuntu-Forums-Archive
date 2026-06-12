---
title: "Grub2 dual boot to Win7 - wrond /DEV/SDAx"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by paulm2822 on 2010-05-11
I have a Dell ZINO HD and dual booted fine prior to 10.04.  Grubs seems to not identify the Win7 OS partition correctly.  According to Disk utility DEV/SDA1 is a DELL utility partition, DEV/SDA2 is the RECOVERY partition, DEV/SDA3 is my Win7 OS partition...and DEV/SDA5 is my Linux partition.  Ubuntu boots fine... but with GRUB using SDA2 (HD0,2) for win7 I cannot boot to it... is there a fix?

The following is in my GRUB.CFG file
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4c023c8d023c7e50
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

---

### Post by lechien73 on 2010-05-11
You could try booting into Ubuntu, opening a terminal window and typing:

```
sudo update-grub
```

That may fix it quickly and easily.

---

### Post by oldfred on 2010-05-11
We have seen several others where it seems to mix them up. Do you have an entry for sda3 and does that boot to your win7? 

We can always convert to a custom entry if need be.

---

### Post by paulm2822 on 2010-05-11
Dang... tried that... also tried to GKSUDO Gedit the Grub.CFG file to /dev/sdae * (Hd0,3)... grub-update puts everything back to /dev/sda2 & (Hd0,2).... ARGH!

---

### Post by paulm2822 on 2010-05-11
> **oldfred said:**
> We have seen several others where it seems to mix them up. Do you have an entry for sda3 and does that boot to your win7? 

We can always convert to a custom entry if need be.

Noob here... you mean like cut and paste a new menu entry with the correct SDA3 & Hd0,3? 

As of now there is no entry for this combination.

---

### Post by darkod on 2010-05-11
Are you sure /dev/sda2 is not the System Reserved partition win7 sometimes uses? Because if it is, /dev/sda2 is correct because the boot files are there, even though /dev/sda3 is the win7 system partition.

If you are right and /dev/sda2 is recovery partition, then you have another problem also because if grub2 is not locating win7 on /dev/sda3 it means it can't locate its boot files there. If they are messed up even manual pointing to that partition won't help you much.

Can you run the boot info script from my signature? There is short explanation how to run it on the webpage. Post the content of the created results.txt file. Otherwise we can only speculate, that file will help us speed up the process. :)

---

### Post by paulm2822 on 2010-05-12
Darkod.... done... I don't understand what I see...  Do I need to back up the files I need off of the HD (win7 & 10.04)and try to recover all from scratch if I can (the old f12 boot option)?

---

### Post by oldfred on 2010-05-12
when you upgraded it said to install grub to all drives but then presented a list of drives and partitions. You installed to every partition overwriting the windows boot part that is in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

While is is not techically a software bug, it is confusing instuctions. Please sign up and add to the bug report on launchpad.
Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by darkod on 2010-05-12
> **paulm2822 said:**
> Darkod.... done... I don't understand what I see...  Do I need to back up the files I need off of the HD (win7 & 10.04)and try to recover all from scratch if I can (the old f12 boot option)?

We were both right. /dev/sda2 is the recovery partition but the boot files on /dev/sda3 are missing and that's why win7 is not getting detected.

What I would do in this situation:
1. Use the first link oldfred provided to remove grub2 from both partitions /dev/sda2 and /dev/sda3. No need to remove it from the others for now, although it would be better.

2. Repair the win7 boot process as oldfred suggests. That will overwrite grub2 on the MBR so don't panic when the computer starts booting win7 directly. The main part is to get to that point.

3. Once win7 is fine, reinstall grub2 to the MBR by booting the ubuntu cd in live mode and executing:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart. That should allow you to boot ubuntu again. Note that win7 might still be missing from the boot menu, this is normal.

4. Boot the ubuntu from the hdd (not live mode from the cd) and execute:

sudo update-grub

After that the grub menu should be updated to include win7. When selecting an OS be careful that /dev/sda2 is your recovery partition, and /dev/sda3 your win7. The entries in the menu will be very similar.

That should sort everything out.

---

### Post by paulm2822 on 2010-05-12
darko & oldfred... Thanks... You are taxing these noob brain cells... but that what they are there for.  I've been around since DOS 3.2x but have grown lazy these years... time to dive in and learn again.  And yes the instructions were confusing I'll head to Launchpad when I get this all settled.  Thanks again!

Paul

---

### Post by paulm2822 on 2010-05-14
WOW...Just ran the testdisk and then the BootRec.exe/FixBoot  too correct /dev/sda2 and /dev/sda3 and that is all it has taken so far... appear to be back to normal.
:popcorn:
the Grub screen still works and I can still boot when needing to win7... You are CHAMPS!

---

