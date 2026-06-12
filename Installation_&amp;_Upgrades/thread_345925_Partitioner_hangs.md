---
title: "Partitioner hangs"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by vivin_west on 2007-01-24
I have been using Ubuntu for a while,so I want to remove windows completely in my new system.The problem is whenever I run the installation procedure it runs the disk partioner.Here the system hangs. Iswthere anyway to install Ubuntu via terminal window without running the partitioner.

---

### Post by housam on 2007-01-25
Did you already removed windows from your machine ? did you reformated the partition ?
If not use the Gparted to do the job and to prepare your partitions before installing.

---

### Post by vivin_west on 2007-01-31
whenver I run Gparted the system hangs. I dont want to use windows.I dont mind if it is removed completely.Is there a way to install Ubuntu without running the Gnome partitioner?

---

### Post by housam on 2007-01-31
I would like to ask you about your pc specs. as maybe your RAM is below the required. If it is more than 256 Mb , then should be ok for the installation and during the installation try to use the 1st or 2nd options for partitioning.

---

### Post by vivin_west on 2007-02-01
My system has 256MB RAM. But what I am trying to tell is that I dont get the 1 or 2 options for partitioning.As soon as I click the forward button on step 4 while installation the Gnome partitioner program runs and then the system hangs.I hope I have made it clear. The partitioner program doesnt show me the options in the first place. So is there a command in terminal window where I can just proceed with installation.

---

### Post by housam on 2007-02-01
Ok, may I ask what version of ubuntu you trying to install ? is it a live CD or an Alternate CD ? Did you check the cd for any errors ? Did you burn it or get it from shipit ? and if you burn it , reburn it at the slowest speed available i.e. 4x or 2x using the default burning program as described in [How to burn a CD]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by anubhavrocks on 2007-02-01
Please try using the Alternate install CD 
[http://ftp.gui.uva.es/sites/ubuntu.com/releases/edgy/](http://ftp.gui.uva.es/sites/ubuntu.com/releases/edgy/)

---

### Post by vivin_west on 2007-02-01
It is Dapper
Live CD
from Shipit
I want to use only Dapper.I dont want to risk trying Edgy.I have not used it before.

---

### Post by vivin_west on 2007-02-01
I have checked CD for defects,there are none.I dont know if there is a problem in my system.My windows disk partitioner works fine.

---

### Post by devils_casper on 2007-02-01
hi vivin_west !

boot up from Ubuntu LiveCD and open terminal.
execute this
```

dd if=/dev/zero of=/dev/**hda** bs=521 count=1

```
if your harddisk is SATA, replace **hda** with **sda**.
this code will *wipe* your harddisk. no data, no partitions. installer will think that your harddisk is blank and brand new. try to install again.




Casper

---

### Post by vivin_west on 2007-02-01
I got this reply
dd: opening '/dev/hda'=read only file system

---

### Post by vivin_west on 2007-02-01
It is not possible to wipe out the hard disk through live cd.

---

### Post by devils_casper on 2007-02-01
Sorry ! my mistake. prefix 'sudo' before 'dd' command.





Casper

---

### Post by housam on 2007-02-01
> **vivin_west said:**
> It is not possible to wipe out the hard disk through live cd.

boot the live cd then sys. >> admin. >> Gnome partition editor  and try to delete the entire HDD.

---

### Post by housam on 2007-02-01
> **vivin_west said:**
> I have checked CD for defects,there are none.I dont know if there is a problem in my system.My windows disk partitioner works fine.

If windows disk partitioner works fine ( I assume it is the partition magic ), you can resize your partition to the minimum and create an unallocated space that the installer can detect and repartition it.

---

### Post by anubhavrocks on 2007-02-01
>>It is not possible to wipe out the hard disk through live cd.

sudo fdisk  /dev/hda

Be WARNED that you risk loosing all your data!!

---

### Post by devils_casper on 2007-02-01
[QUOTE=housam]If windows disk partitioner works fine ( I assume it is the partition magic ), you can resize your partition to the minimum and create an unallocated space that the installer can detect and repartition it.[/QUOTE]
i agree. but this will not clear MBR. 





Casper

---

### Post by housam on 2007-02-01
> **devils_casper said:**
> i agree. but this will not clear MBR. 





Casper

It is just to create a clean partition for installing ubuntu, then the other partitions can be dealt with through ubuntu.

---

### Post by vivin_west on 2007-02-01
sudo fdisk /dev/hda. can you tell me what to do next?

---

### Post by anubhavrocks on 2007-02-01
I suggest that you first run 

sudo parted

Make your changes  and then try running gparted.

If nothing works try using 

dd if=/dev/zero of=/dev/hda bs=512 count=1

---

### Post by vivin_west on 2007-02-01
I have done this
dd if=/dev/zero of=/dev/hda bs=512 count=1,but I get
hda is a read only file as messg. I cant load gnome editor.It gets stuck

---

### Post by anubhavrocks on 2007-02-01
the command should be

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1

You need superuser privilege to run it

---

