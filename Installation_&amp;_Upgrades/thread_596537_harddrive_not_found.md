---
title: "harddrive not found"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Im3m on 2007-10-29
I have a WD1200BEVS 120GB harddrive and an Intel core dou processor 2GHz.

At the moment only the XP is installed wich isnt my favorite. 

Ubuntu 6.06 could boot from the CD, but i found no harddrives. I also tried installing suse and kubuntu but the hard drive was never detected and therefore of course the installation was not sucessfull.... 

I used gparted to patition the hd and had no problems with that.

can anyone help?

---

### Post by taurus on 2007-10-29
After booting from a LiveCD, open a terminal and post the output of this command here.

```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by Im3m on 2007-10-29
```
ubuntu@ubuntu:~$ sudo fdisk -l
Note: sector size is 2048 (not 512)

Disk /dev/sda: 1004 MB, 1004666880 bytes
219 heads, 56 sectors/track, 40 cylinders
Units = cylinders of 12264 * 2048 = 25116672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          40      981008    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 56) logical=(0, 1, 1)
ubuntu@ubuntu:~$

```

sda is my usb stick i used to copy the output

thanks for your quick reply

---

### Post by taurus on 2007-10-29
You said that gparted from the LiveCD found your internal harddrive.  Can you post a screenshot of that?

---

### Post by Im3m on 2007-10-29
the xp is runnig onthat drive, so i know that it is there and running. 

i made a screenshot in gparted. first mounted the usb stick with the automatic procedure offered. than in the terminal i moved to the stick /mnt/usblive and tried to move the screenshot
```
mv /root/gparted.jpg . 
```

i used ```
ls
```
to verify the sucessfull copy.   

somehow it did not work. i will try again. takes some time for rebooting

---

### Post by Im3m on 2007-10-29
i have to confess that i do not know how to get a screenshot
sorry

---

### Post by taurus on 2007-10-29
Applications -> Accessories -> Take Screenshot

---

### Post by Im3m on 2007-10-29
i used the live cd of gparted...

---

### Post by Im3m on 2007-10-29
i did not think that the gparted from the ubuntu live cd would work, too. i used the geparted live cd...
anyhow, here is the screenshot

---

### Post by taurus on 2007-10-29
Why don't you use gparted to format that unallocated partition to ext3.  Then, will see if the installer can detect that partition now.  It will be /dev/sda2.

p.s.  I assume you have XP on /dev/sda1!

---

### Post by Wollongong on 2007-10-29
It seems that Ubuntu 7.10 has problems with some intel disk controllers, although it might be a problem it has with Western Digital disk drives. I think the problem is likely to be that the disk controller is not supported properly.

See this thread: [http://ubuntuforums.org/showthread.php?t=586894](http://ubuntuforums.org/showthread.php?t=586894)

Could everyone with this problem please advise:
 [LIST]
[*]Brand and Model number of motherboard
[*]Brand (WD, Seagate etc), Type (SATA or IDE/PATA) and Model Number of disk
[/LIST]

If this is your first attempt at linux, I suggest you avoid Ubuntu given that it won't easily install. Even though I am a great fan of Ubuntu, I recommend you use Debian 4.0 "Etch". I have this installed and working on an Intel motherboard type D865 with Western Digital disk, which Ubuntu didn't recognise.

Once you are comfortable with Debian, you may be able to update to Ubuntu on the next release (April 2008). Because Ubuntu is based on Debian, you will find that most of what you learnt on Debian is still applicable.

All the best,

---

### Post by Im3m on 2007-10-29
well, gparted shows two "drives" the one i made a screenshot from was my usbstick again, the otherone was the cd with the ubuntu on it. the undetected hd has 120gb 
the gparted live cd boots a small linux system directly from the cd (similar to the ubuntu cd). it shows the three partitions i created. the first one is ntfs and has about 20 gb the second one i formated with reiserfs for the linux files while the third one is formated with fat bcause i thought both sytems could see it for data i want to use with both os.
the gparted live cd offers the possibility to take screenshots but i did not mange to save them on the usbdisc. 

so the gparted live cd detected the hd and was able to do the partitioning. i see in the xp that the size of my hd decresed to about 20 gb from the former 120. i think i need to load some special modules or so in the boot options to make the hd visible for ubuntu. unfounately i do not know how this works in detail and especially which bootoption i should specify.

---

