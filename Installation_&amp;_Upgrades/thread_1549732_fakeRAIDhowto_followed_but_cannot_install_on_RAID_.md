---
title: "fakeRAIDhowto followed but cannot install on RAID 1 using desktop or alternate CD"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by mclad on 2010-08-10
System: Asus M2V-MX motherboard (circa 2006), AMD Athlon 64 dual core 3800+
RAM: 2 GB
Drives: 4 x 1 TB Western Digital Blue WD10EALS in 2 x fakeRAID 1 arrays
Array 1: VIA VT8237A SATA 2-Port Controller, 3 x NTFS primary partitions Win XP / Win 7 / Data, 1 x extended partition for Linux
Array 2: JMicron JMB363 SATA 2-Port Controller, 1 x NTFS data partition only
Other: nvidia 7600 GS video card, Initio PCI card capable of fakeRAId with 1 external + 1 internal SATA port, no drives attached
 
**Attempting to install to bootable VIA RAID 1 array**
 
I have read the [fakeRAIDhowto]("https://help.ubuntu.com/community/FakeRaidHowto"), which provided some good background but in the end not helpful as it does not address 10.04 and did not allow me to install.
 
I used the **live CD (amd64)** terminal session
 
sudo dmraid -ay
 
tells me that my RAID devices are already installed.
 
ls -l /dev/mapper
 
tells me that my RAID device is /dev/mapper/via_bfidghddbd
 
sudo gparted /dev/mapper/via_bfidghddbd
 
allowed me to partition my RAID 1 drives. My 3 NTFS primary paritions on the RAID array were recognised. I set up an extended partition with two logical drives approx 200 GB with ext4 file system and the last 6 GB linux-swap.
 
I then ran the ubiquity graphical installer which failed on step 3 or 4 I think with error message:
 
ubi-partman failed with exit code 10
 
or similar. I have not been able to work around this. I tried skipping this step (accepting the error, or whatever the option was), and at step 7 choosing the **advanced** option and selecting /dev/mapper/via_bfidghddbd for my root install, spits me straight back out to step 5 for some reason.
 
So i tried the **alternate CD (amd64)**
 
This tells me that one or more SATA raid configurations have been detected and asks me if i want to activate them, I choose yes.
 
Next I get progress bar with title "setting up the partitioner" and the next message box is **"[!!] Partition disks**. This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings" etc... BUT there are no partition shown and the only two options are:
 
Undo changes to partitions
Finish paritioning and write changes to disk
 
Neither of these get me anywhere. Selecting finish partitioning tells me "No root file system is defined, please fix from partitioning menu" and returns to the previous menu.
 
Undo changes to partitions gets me to a blue screen (!!) which I have to control-C to get back to the parition disks menu (with undo or finish options only again).
 
This time I choose to <Go Back> which again gets me a blue screen.
 
I'm stuck, please help!

---

### Post by ronparent on 2010-08-10
The basic problem is that gparted, as distributed, will not recognize raid or raid partitions. To get around this, I suggest booting to a live cd and installing from there. Before you start the install use the synaptics pakage manager to install kpartx for the session. After this the install should proceed normally. You may and will probably get a 'fatal error' on the grub install - this is fixable. Let us know how you make out. Good luck.

ps At last look the fakeRAID how to wasn't updated for an install to lucid.

---

### Post by mclad on 2010-08-11
No I am afraid that is not the problem. Or not the only problem. I booted the desktop CD

sudo apt-get install kpartx

then installed using ubiquity. The same thing happened namely:
> I then ran the ubiquity graphical installer which failed on step 4 (after asking for keyboard type) I think with error message:
 
ubi-partman failed with exit code 10
 
or similar. I have not been able to work around this. I tried skipping  this step (accepting the error, or whatever the option was), and at step  7 choosing the **advanced** option and selecting /dev/mapper/via_bfidghddbd for my root install, spits me straight back out to step 5 for some reason.

Next I decided to try something, I removed my initio SATA /eSATA card, and turned off my Jmicron RAID array disks, so only the VIA bootable RAID 1 array was connected.

And this time after asking for keyboard type I get the prepare disk space message!!!
HOORAY!

---

### Post by mclad on 2010-08-11
OK. So my install worked.
In the final menu I chose the advanced options and specified /dev/mapper/via_bfidghddbd to install grub to.
On restarting however, I was not presented with any options to boot XP or Win 7 but went straight into ubuntu. The wife is **not** going to like that ;)

How do I get the grub menu with boot choices?

I'm currenty downloading updates, as I want to have my drivers up to date before I put my initio PCI card and connect my Jmicron sata raid array, which will be the next job.

---

### Post by mclad on 2010-08-11
OK. I got the grub menu the second time I booted and I worked out how to default it to Win 7 to keep the wife happy.

I´ve reconnected my Jmicron RAID 1 array and rebooted but ubuntu does not want to recognise it. The mapper name also looks a bit weird:
```
madams@madams-desktop:~$ ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 59 2010-08-12 00:12 control
brw-rw---- 1 root disk 252,  6 2010-08-12 08:12 jmicron_JRAID-DATA      ?
brw-rw---- 1 root disk 252,  6 2010-08-12 00:12 jmicron_JRAID-DATA_______
brw-rw---- 1 root disk 252,  0 2010-08-12 00:12 via_bfidghddbd
brw-rw---- 1 root disk 252,  1 2010-08-12 00:12 via_bfidghddbd1
brw-rw---- 1 root disk 252,  2 2010-08-12 00:12 via_bfidghddbd2
brw-rw---- 1 root disk 252,  3 2010-08-12 00:12 via_bfidghddbd3
brw-rw---- 1 root disk 252,  4 2010-08-12 00:12 via_bfidghddbd5
brw-rw---- 1 root disk 252,  5 2010-08-12 00:12 via_bfidghddbd6
madams@madams-desktop:~$ sudo dmraid -ay
RAID set "jmicron_JRAID-DATA      " already active
RAID set "via_bfidghddbd" already active
RAID set "jmicron_JRAID-DATA      1" was not activated
RAID set "via_bfidghddbd1" already active
RAID set "via_bfidghddbd2" already active
RAID set "via_bfidghddbd3" already active
RAID set "via_bfidghddbd5" already active
RAID set "via_bfidghddbd6" already active
```

Where next? I am still very much a gnu/linux beginner but it feels good to be learning :)

---

### Post by iainmeikle on 2011-04-04
I found that simply ensuring that the name of the array (default being JRAID taking only 5 of the available 15 chars) in the bios filled the entire available space (all 15 chars) solved this problem for me using 10.10. Hope this helps.

---

### Post by ronparent on 2011-04-04
All the raid devices that have been successfully activated will appear in /dev/mapper. The bottom line is if the symbolic links appear there then the partition that appear are mountable even if the names look weid.

---

