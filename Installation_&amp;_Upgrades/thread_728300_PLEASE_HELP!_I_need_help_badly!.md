---
title: "PLEASE HELP! I need help badly!"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2008-03-18
So, wouldnt you guess it :) I decided to get rid of XP completely.

I have (had) two partitions on my 500gb drive. 300gb for XP, 200gb for Ubuntu. Well, I deleted the first partition (XP) and planned to use gParted to increase the size of my Ubuntu partition the full way so I only have one partition. gParted cannot scan anything now. I must have deleted the boot menu residing on the first partition, because now I get "no operating system found".

#1- all my stuff on my ubuntu partition is still safe, correct?

#2- how do I get Ubuntu to load up now? Is there some software I can use?

---

### Post by scragar on 2008-03-18
if you relaunch gparted you should be able to edit the "flags" on the ubuntu partition, make sure "boot" is ticked, and that it is unticked on all other partitions.

---

### Post by Pumalite on 2008-03-18
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by iheartubuntu on 2008-03-18
So I put in a LiveCD... all my stuff on my Ubuntu partition is there.

Ive relaunched gparted several times... it seems to hang while searching for partitions. I'll do what Puma recommends... I hope I can configure where GRUB goes?

---

### Post by iheartubuntu on 2008-03-18
I reinstalled GRUB and everything said "succeeded" but it actually didnt do anything after reboot. Im still getting the no operating system found.

---

### Post by Pumalite on 2008-03-18
Boot your Live CD and from the Terminal, post>
sudo fdisk -lu
Also, try to boot your Ubuntu with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by iheartubuntu on 2008-03-18
> **Pumalite said:**
> Boot your Live CD and from the Terminal, post>
sudo fdisk -lu

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63     9462284     4731111    b  W95 FAT32
/dev/sda3       669444615   971386289   150970837+  83  Linux
/dev/sda4       971386290   976768064     2690887+   5  Extended
/dev/sda5       971386353   976768064     2690856   82  Linux swap / Solaris

and also my Ubuntu is on (hd0,2)

---

### Post by Pumalite on 2008-03-18
Use Gparted and set the boot flag to sda3

---

### Post by iheartubuntu on 2008-03-18
gparted doesnt work anymore. It just sits and thinks while trying to scan all devices.

* I'll give supergrub a try.

---

### Post by iheartubuntu on 2008-03-18
Supergrub, didnt help either. :| I am able to use supergrub to boot into my Ubuntu and use it, but thats about it. It has a recovery option to fix my grub like the instructions in Pumas link (for using a live CD), but all grub does is the same thing, but text based. I get "success" messages that it fixed my grub, but nothing happens on reboot.

Well, using superbgrub, I am now in my Ubuntu partition, Ive opened up gparted and flagged my ubuntu as the boot. Now I'll reboot and see what this does for me. Adios!

---

### Post by iheartubuntu on 2008-03-18
Many thanks to Puma (yet again!) for suggesting Supergrub. It allowed me to boot into my Ubuntu partition, and then run gparted to select my Ubuntu linux as the boot. All works great now. THANK YOU!

For some strange reason, I was unable to fix things the normal way.

---

### Post by Pumalite on 2008-03-18
You are welcome. Good luck.

---

### Post by iheartubuntu on 2008-03-20
Not quite out of the woods just yet :) Gparted still doesnt work and Im trying to merge partition #1 with #3. #1 used to be my XP partition... its empty now... all 343GBs of it and My linux partition is almost full!

After running "sudo parted /dev/sda print" I get this....

> Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  343GB  343GB   primary   ext3              
 3      343GB   497GB  155GB   primary   ext3         boot 
 4      497GB   500GB  2755MB  extended                    
 5      497GB   500GB  2755MB  logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.  

Should I update fstab? Would this help? What would it do? How do I go about doing it? Thanks.

Running "cat /etc/fstab" I get this...
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e2806d33-4e1e-43b8-a144-b5d9badf6301 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=90229ff7-0e8c-4218-86ca-1b22cf8118a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

My goal is to get partitions #1 and 3 merged and get everything in working order again (like with gparted working hopefully). Many many thank yous for any tips!

---

### Post by iheartubuntu on 2008-03-20
bump

---

### Post by iheartubuntu on 2008-03-20
bump.

Any tips? Thanks

---

### Post by Pumalite on 2008-03-20
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screenshot
Use camera icon at the bottom

---

### Post by iheartubuntu on 2008-03-20
This is a photo of gparted within Ubuntu. the Gparted disc boots up, but it is stuck when scanning for devices. It never gets out out of that mode, so I can never see a screen like this to edit.

[IMG]http://www.shirtees.net/gparted.jpg[/IMG]

---

### Post by Pumalite on 2008-03-20
I'd be weary of trying to merge partitions with Ubuntu Gparted. See if you can get Gparted Live CD version 0.3.4-0 and try with that one.

---

### Post by iheartubuntu on 2008-03-20
> **Pumalite said:**
> I'd be weary of trying to merge partitions with Ubuntu Gparted. See if you can get Gparted Live CD version 0.3.4-0 and try with that one.

Yah, I agree... I cant do any operations in gparted if it requires use of the partition Im currently using. So I cant merge.

Up until this point Ive been trying version 10 of gparted 0.3.4-10 so I will give 0 a try. Thanx.

---

### Post by iheartubuntu on 2008-03-20
I just tried the older version of gparted and it didnt work for me either. I get into the disc, and then it "scans for all devices" and thats it. 15 minutes later it cant find anything.

Is there a way to manually merge my partitions? or a different partition managing disk? Ive already tried Qtparted (well, in Ubuntu - does qtparted have a seperate boot disk?) and in Ubuntu it cant even find my HD.

---

### Post by Pumalite on 2008-03-20
I think recuecd comes with a partitioner: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Post:
lshw
To get an idea of your machine.

---

### Post by iheartubuntu on 2008-03-21
The gparted in the System Rescue CD also got stuck search for all devices.

I wonder if I need to format that section? Its an empty EXT3 right now. I can see it here in Ubuntu, but I dont have "permissions to write" there. Reformatting didnt help. Maybe if I can somehow gain permission, I can at least make use of it.

---

