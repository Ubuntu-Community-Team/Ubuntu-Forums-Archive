---
title: "Need help with ubuntu"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Skipopis on 2010-03-07
I was running Ubuntu 9.04 without a hitch along came 9.10 and I upgraded and it started crashing and now it wont boot (Grub error 17). I am currently running Ubuntu 9.04 off of the disc, I have attempted to reinstall 9.04 and I get to the partition menu once in awhile and it does not recognize that i have 9.10 on my drive and will not let me overwrite. Can anyone help please.

---

### Post by raymondh on 2010-03-07
> **Skipopis said:**
> I was running Ubuntu 9.04 without a hitch along came 9.10 and I upgraded and it started crashing and now it wont boot (Grub error 17). I am currently running Ubuntu 9.04 off of the disc, I have attempted to reinstall 9.04 and I get to the partition menu once in awhile and it does not recognize that i have 9.10 on my drive and will not let me overwrite. Can anyone help please.

Since you plan to 'overwrite' karmic ..... a possible workaround is to use gparted from the liveCD to erase the existing ubuntu root and swap partitions leaving them unallocated.  When you  install, you hence install in largest, unallocated space.

Identify the existing root and swap (or /home).  You can use terminal and 

```
sudo fdisk -l
```

to help you identify which is ubuntu/linux.

As always, have a working/tested back-up of your files.

Regards.

---

### Post by Skipopis on 2010-03-08
Input/output error during read on /dev/sda


Read the terminal after sudo gparted

---

### Post by Skipopis on 2010-03-09
I'm still looking for help, please and thank-you

---

### Post by presence1960 on 2010-03-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Skipopis on 2010-03-09
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)



Sorry I  don't see a # sign on any toolbar

---

### Post by presence1960 on 2010-03-10
You don't have a valid partition table on your hard disk. If you have nothing to lose on that disk boot the Live CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
gksu gparted
``` Under Device in the menu bar select create partition table. Select an msdos type partition table. Click the green check mark to apply. Now try installing.

On the other hand if you have data you need on that disk you will have to use testdisk to try to recover your partition table and the data. I am not too familiar with that process. if this is what you need to do I would start a new thread with the title including the words "need to recover data using testdisk" to attract the attention of those who can help.

---

### Post by Skipopis on 2010-03-10
I don't see this message anywhere on the desktop. "try ubuntu without any changes

---

### Post by kansasnoob on 2010-03-10
From the live desktop try:

```
sudo fdisk /dev/sda
```

Then type **[COLOR="Red"]w[/COLOR]**.

---

### Post by Skipopis on 2010-03-10
Unable to open /dev/sda


is what my terminal reads

---

### Post by kansasnoob on 2010-03-10
I would then only know to use TestDisk but I'm hardly proficient with it. Look here:

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

Follow the steps for "Now let's assume we have lost our partition table and want to restore it." Basically you want to:

```
[  Quit  ]  [Search! ]  [ Write  ]
                       Write partition structure to disk
```

---

### Post by presence1960 on 2010-03-10
> **Skipopis said:**
> I don't see this message anywhere on the desktop. "try ubuntu without any changes

It does not say it on the desktop- read carefully again:

> You don't have a valid partition table on your hard disk. If you have nothing to lose on that disk **_boot the Live CD and choose "try ubuntu without any changes"_**,

Then when the desktop loads do this:

> when the desktop loads open a terminal and run ```
gksu gparted
```

---

### Post by Skipopis on 2010-03-11
Still looking for the right answer, thanx for the help thus far.

---

### Post by presence1960 on 2010-03-11
> **Skipopis said:**
> Still looking for the right answer, thanx for the help thus far.

you were given the right answer: you either need to use testdisk to recover your partition table (kansasnoob) or create a new partition table by booting the Live CD and using gparted (presence1960)

---

### Post by Skipopis on 2010-03-13
Thanx for the help thus far, but I'm still not in the clear can anyone get me up and running.

---

### Post by Skipopis on 2010-03-13
gparted wont work says I need to b root, testdisk don't work can't burn disk when I'm using only drive to run live disk

---

### Post by Skipopis on 2010-03-13
gksu gparted, terminal opens gparted says no devices detected

---

