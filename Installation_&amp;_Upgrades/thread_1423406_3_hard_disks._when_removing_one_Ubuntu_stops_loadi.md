---
title: "3 hard disks. when removing one Ubuntu stops loading"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by botWi on 2010-03-06
I have 3 hard disk drives
one regular and two sata:
 Ubuntu / is installed on sata /dev/sda6
 Ubuntu /boot is installed on /dev/sda1

second sata hard disk /dev/sdb is empty
I have just reformatted it to ext3

third hard disk is /dev/sdc with some fat and ext3 partitions


if I shutdown computer, then plug out one of sdb/sdc or both of them
then after BIOS I see grub menu (as usual)

but if I hit any keyboard button the computer automatically reboots
without any messages

I tried hitting c,e,enter - reboot :(
I tried reinstalling grub like this:

$ grub
grub> find /grub/menu.lst
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.

---

### Post by amauk on 2010-03-06
It's possible that your disks are referenced in /etc/fstab as /dev/sda1, etc
rather than by their UUID
and removing one disk is re-ordering the disks

unplug the disk
Boot to a liveCD
double check that fstab is correct
amend as needed (make backup of fstab first)
reboot and see

---

### Post by botWi on 2010-03-06
What is the connection between grub and fstab?
am I missing something?

grub operates only with /boot
and fstab is not in /boot directory

---

### Post by presence1960 on 2010-03-06
we need a more clear picture of your setup & boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with all disks plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by botWi on 2010-03-08
well, guys
I have quoted this line in manu.lst:

#splashimage (hd2,5)/boot/grub/splashimages/97138-Sexy2.xpm.gz

and now everything is good!
why grub doesn't use uuid in this line?

---

