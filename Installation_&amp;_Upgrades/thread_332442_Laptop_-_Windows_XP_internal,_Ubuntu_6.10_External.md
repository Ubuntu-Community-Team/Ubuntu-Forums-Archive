---
title: "Laptop - Windows XP internal, Ubuntu 6.10 External"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by opakedragon on 2007-01-06
ok this is my setup:

[INDENT]DELL INSPIRON 9300 - 60GB hdd - Windows XP Media Center
Seagate in External Encloser-  320GB hdd - Ubuntu[/INDENT]

So far today I have installed and wiped Ubuntu from my External like 7 times and Im getting tired of waiting for the installations. My Laptop BIOS has the option for (second only to CD boot) USB booting but when ever I go to load Ubuntu after a "successful" installation it always just sits there forever Im going to try one more time and let it sit there for an hour to see what happens as I do something else, but I doubt that will work.

After the second failure I tried the whole "deselect these three options: ... ... in System > ... > Preferences > Removable..." anyway that didnt work then I found the post on some forum (cant remember too tired) titled "SUCCESS - BREEZY loaded on external hardrive" turns out it was for a different version. 

I tried the tutorial at "http://help.ubuntu.com/community/BootFromUSB" but I could not understand how to create the Boot CD after the "Booting via grub" section because of the confusion that it caused me (my entering of the command yielded no "Possible files are: ldlinux.sys ...." from any of the 'grub> find /[tab]' commands I performed.

From what several different articles suggested that (as far as I could tell) because my grub (which I figured out today is a special commandline btw) wasn't being installed on my external but on my internal which would make sense because when selecting which partitions to mount the stupid thing kept making me select the FAT32 partition on my internal (sda2 or sda3), even though I was giving it a whole 250GB of ext3 (sdb1) and 5GB of linux-swap(sdb2) space, to be mounted with the installation.

Anyway what Im really asking, more pleading with anyone, is to please help me understand what it is I need to do, or just flat out give me the code to understand how it works later, as my head hurts after trying for.... (started at 3:00PMish and its 2:13AM now... so that makes...) just under 12 hours. I normally prefer to understand everything that I do as I am a second year Software Engineering Major in college but right now I don't need to know how it works just that it does.

This is the first day I had my external harddrive. I downloaded the ISO yesterday and burned it to a CD today before my External came in the mail. I have had no previous experience with Linux as my laptop's Internal hdd is too small to dual boot without deleting alot... all the time.

Worst case senarios I call up DELL to get the Windows XP Media Center Discs and Format my internal, but I really dont want to do that. Thanks for any help you can give.

---

### Post by foolsh on 2007-01-06
internal drive = /boot  <-- about 100 MB fat16 partition configured to boot and mounted as /boot
                       C:  


eternal drive = /
                      swap

if this makes any sense to you
 you'll need about a 100 MB boot partition on the internal drive
for linux to hold the info to access the external drive
atleast thats my option I don't have an eternal drive to test but this is what I would try

---

### Post by logos34 on 2007-01-06
> grub...wasn't being installed on my external but on my internal which would make sense 

yep, that's what's happening. Ubuntu is probably installing to the external but grub goes by default to the mbr of the first detected disk (your laptop drive).  To see how everything is partitioned: boot from the ubuntu livecd, open a terminal and type
> fdisk -l

Install ubuntu one more but this time unplug the power cable to the internal sata drive so grub will be forced to the external.  Then you can boot from your external drive and have a working os.

If windows ntfs is still there you don't need to format your laptop drive...grub just overwrote the windows bootloader.  Get the Windows MCE disk(s) from Dell and boot into the Windows recovery console and do 'fixmbr' to restore it.

[edit: if you don't want to wait for winMCE disks you could try using [Super Grub]("http://supergrub.forjamari.linex.org/index.php") to restore mbr.  At any rate, if windows is still on the main drive you can read the files from within linux, you'll just have to create a mount point for it and edit your fstab file.]

---

