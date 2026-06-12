---
title: "Can't find boot sector after upgrading to Ibex"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by mrund on 2008-11-10
I have a Dell Inspiron 6000 laptop that's been running WinXP and Ubuntu in parallel since the days of Feisty Fawn. I've updated regularly without any trouble.

Today I upgraded to Intrepid Ibex. The installation went smoothly except for some trouble with the gnome applets package. Sticky Notes didn't work anymore, but there didn't appear to be any trouble with the general running of the system. It restarted just fine after install, I worked with it for a bit, and then I turned it off cleanly using the new menu top right.

Now when I start the machine I get the lovely error message "No boot sector on internal hard drive. No bootable devices.". GRUB doesn't start.

When I boot from a fresh Ibex CD, it offers to install Ubuntu as if the machine were new from the factory. When running Ubuntu off the CD I can see the laptop's hard drive as an SCSI drive, but it can't be mounted.

Any suggestions?

---

### Post by Carl Hamlin on 2008-11-10
> **mrund said:**
> Any suggestions?

Not that it'll help now, but in my experience the upgrade path is always a good deal rockier than installing from CD. After a disastrous upgrade experience, I now always backup my data and install the new releases fresh from CD.

---

### Post by mrund on 2008-11-10
That will be very good to know six months from now.

---

### Post by caljohnsmith on 2008-11-10
If you have your Live CD, how about booting that, opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, to make sure Grub is properly installed to your MBR (Master Boot Record), do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all those commands too, reboot, and let me know if anything changes.

---

### Post by mrund on 2008-11-11
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00003442

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$ 


grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

grub> 


To my untrained eye this looks like I'm completely f*cked. :confused:

Pretty amazing that the installation managed to first work pretty well, then die so thoroughly upon a clean close-down that it *nuked the partition table*.

---

### Post by caljohnsmith on 2008-11-11
Yes, that's not a good sign at all that fdisk claims you have an invalid partition table. I would begin by running testdisk on it to see if it can find your lost partitions on the drive, but that assumes you aren't experiencing a hardware failure of some sort. If you have internet access from your Live CD, just do:
```
sudo apt-get install testdisk
sudo testdisk
```
[Note the following assumes you are running version 6.9, not 6.8]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition table.

If you don't have an internet connection from your Live CD, you could download and use the Ultimate Boot CD instead since it comes with testdisk. Just go to Disk Tools > Partition > Testdisk. Let me know how it goes.

---

### Post by mrund on 2008-11-11
The ailing machine does have internet access. But I got the following error message (in Swedish, so I'll have to paraphrase), "E: Could not find the testdisk package". I guess there's really nowhere for the system to store the package since the hard drive's farked?

Should I get Ultimate Boot CD instead?

---

### Post by caljohnsmith on 2008-11-11
I forgot to mention, before trying to download testdisk, first make sure the Universe repository is enabled in System > Admin > Software Sources; then you should be able to download and run testdisk. Also, here's a link for Ultimate Boot CD in case you need to use it instead:

[http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)

---

### Post by mrund on 2008-11-11
Here's the output of Testdisk's analyse:

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55


And the output of quick search:

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
P HPFS - NTFS             12   0  1  3453 254 63   55295730
L Linux                 3454   1  1  6789 254 63   53592777
L Linux Swap            6790   1  1  6935 254 63    2345427
P FAT32 LBA             6936   0  1  7294 254 63    5767335 [DellRestore]


I see here that Dell's weird little utility partition has somehow been set as primary boot partition. Which one should I set as boot? And how?

Here's the output of the "deeper search" option.

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
D HPFS - NTFS             12   0  1  3453 254 63   55295730
D HPFS - NTFS             12   0  1  4091 254 63   65545200
D HPFS - NTFS             12   0  1  6934 254 63  111217995
D HPFS - NTFS             12   0 10  3453 254 63   55295721
D Linux                 3454   1  1  6789 254 63   53592777
D Linux                 3454   2  1  6649 254 63   51343614
D Linux Swap            6650   1  1  6789 254 63    2249037
D Linux Swap            6790   1  1  6935 254 63    2345427
P FAT32 LBA             6936   0  1  7294 254 63    5767335 [DellRestore]

---

### Post by caljohnsmith on 2008-11-11
> **mrund said:**
> Here's the output of Testdisk's analyse:

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55


And the output of quick search:

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
P HPFS - NTFS             12   0  1  3453 254 63   55295730
L Linux                 3454   1  1  6789 254 63   53592777
L Linux Swap            6790   1  1  6935 254 63    2345427
P FAT32 LBA             6936   0  1  7294 254 63    5767335 [DellRestore]

```

There is no "deeper search" option. But I see here that Dell's weird little utility partition has somehow been set as primary boot partition. Which one should I set as boot?
Since none of the partitions above overlap, it looks like that must be your correct partition table, and you can safely use all those defaults above; if you want, you could change the HPFS/NTFS partition to the bootable one (the one with the asterisk *), and then set the first FAT16 as "P" for primary. That's not necessary, but makes more sense in case you at some point get rid of linux and restore a Windows MBR. Go ahead and write the above partition table, reboot, see if by chance you can boot the HDD, and if not, please post the new results of the following from your Live CD:
```
sudo fdisk -lu
```
Let me know how it goes.

---

### Post by mrund on 2008-11-11
Wow, man, you rule! That sort of worked!

Now the machine boots WinXP. No GRUB, though, so I can't boot Linux. I'm gonna see what happens if I make the Linux partition my boot partition.

---

### Post by caljohnsmith on 2008-11-11
I wouldn't make your Linux partition the boot partition, because most likely you don't have Grub installed to its boot sector and won't be able to boot it. I would recommend restoring Grub to your MBR with the Grub commands I gave in post #4, but it's up to you.

---

### Post by mrund on 2008-11-11
Oh, right, I forgot about that.

But in grub, both the FIND commands you suggested just make grub freeze up. Is there another way to get those numbers for where it should write the MBR?

---

### Post by caljohnsmith on 2008-11-11
Make Grub "freeze up"? Do you mean you get an error 15, or what does it say? That's not a good sign. But I noticed that you have since posted the "deeper search" screen from testdisk, and your Linux partition may be the one we didn't write to the partition table. How about first posting:
```
sudo fdisk -l
```
And for whichever is your Linux partition (probably sda5), how about posting:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt
```
And replace sda5 above if it should be different. If the mount command returns an error, then we most likely chose the wrong linux partition. Let me know what it says.

---

### Post by mrund on 2008-11-11
Grub freezes up = I hit enter and it ceases to accept input. Just a blinking cursor after the command.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29322931

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+   6  FAT16
/dev/sda2   *          13        3454    27647865    7  HPFS/NTFS
/dev/sda3            3455        6936    27969165    f  W95 Ext'd (LBA)
/dev/sda4            6937        7295     2883667+   c  W95 FAT32 (LBA)
/dev/sda5            3455        6790    26796388+  83  Linux
/dev/sda6            6791        6936     1172713+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-11-11
OK, looks like we unfortunately specified the wrong linux partition before, but since there's only two choices, I think we have a good chance of getting it right this time: :)
> **mrund said:**
> 
```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
[COLOR="Red"]*[/COLOR] HPFS - NTFS             12   0  1  3453 254 63   55295730
[COLOR="Red"]D[/COLOR] HPFS - NTFS             12   0  1  4091 254 63   65545200
[COLOR="Red"]D[/COLOR] HPFS - NTFS             12   0  1  6934 254 63  111217995
[COLOR="Red"]D[/COLOR] HPFS - NTFS             12   0 10  3453 254 63   55295721
[COLOR="Red"]D[/COLOR] Linux                 3454   1  1  6789 254 63   53592777
[COLOR="Red"]L[/COLOR] Linux                 3454   2  1  6649 254 63   51343614
[COLOR="Red"]L[/COLOR] Linux Swap            6650   1  1  6789 254 63    2249037
[COLOR="Red"]D[/COLOR] Linux Swap            6790   1  1  6935 254 63    2345427
[COLOR="Red"]P[/COLOR] FAT32 LBA             6936   0  1  7294 254 63    5767335 [DellRestore]
```
OK, fire up testdisk again, do the "deep search" again, and then using the up/down arrows to select each partition above, move the right/left arrows to set the partitions as I've shown above as highlighted in red. Also, for the linux partition I have marked as "L" above, select it, and press "P" to list the directory contents; if that shows the contents of your Ubuntu root directory, then we have the right linux partition this time. Once you are sure your partitions are marked exactly like what is shown above, go ahead and write your new partition table. Reboot, and from your Live CD try to mount the new Ubuntu partition, and also try running the Grub commands on it. Let me know how it goes or if you run into problems. :)

---

### Post by mrund on 2008-11-11
This is starting to look good. Mounting the drive went well. Here's the grub output:

grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Now I'm gonna try booting from the hard drive, so help me the FSM!

---

### Post by mrund on 2008-11-11
Didn't quite work out. GRUB loads just fine and allows me to boot WinXP, but when I try to boot Ubuntu I get the following error message:

Error 17: Cannot mount selected partition

Press any key to continue...

---

### Post by caljohnsmith on 2008-11-11
OK, that Grub error is usually very easy to fix; when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by mrund on 2008-11-12
Nope, I can't change "X" into zero, because the digits are already 0,5.

---

### Post by caljohnsmith on 2008-11-12
> **mrund said:**
> Nope, I can't change "X" into zero, because the digits are already 0,5.
OK, I assumed the "Y" would be correct, but I see it isn't; try using (hd0,4) and that should work.

---

### Post by mrund on 2008-11-14
Amazing, it does work! You have resurrected both my XP, my GRUB and my Ubuntu installation!

Though Ubuntu is acting pretty weird, taking ages to boot up, lacking those gnome applets and freezing up during power-down. I'm gonna try reinstalling a fresh Ibex over the existing crippled one.

---

### Post by caljohnsmith on 2008-11-14
That's great news; hopefully Intrepid will work OK on your machine if you decide to install it. Cheers and have fun. :)

---

