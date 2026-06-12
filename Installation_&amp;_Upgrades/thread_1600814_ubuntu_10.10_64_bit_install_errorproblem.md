---
title: "ubuntu 10.10 64 bit install error/problem"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by RastaManPower on 2010-10-19
hello guys i just downloaded ubuntu-10.10-desktop-amd64. i am using a 6GB usb stick to install the OS. i used the  universal usb installer from my windows 7 64bit and everything went well.
when i boot the pc the install loads but it wont load my harddisks. how come? i am using 2 sata hd than never gave me any problem
this is what i am not getting:
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_04_medium.jpg[/IMG]

---

### Post by sikander3786 on 2010-10-19
Seems like you are trying to install Ubuntu as guest in a virtual machine. Do you...?

---

### Post by RastaManPower on 2010-10-20
i am trying to do a regular install.. i just burned the image on a cd at slowest speed. insert cd in cdrom drive and press f8 at bios.. i load the cd. install starts normal but i get this message.
[IMG]http://i52.tinypic.com/2ekkeo3.png[/IMG]
i shrinked my windows partition and now i have 25 gb of unallocated space on the HD.




i just tryed to load ubuntu from live cd and use gparted. it says no devices detected.

---

### Post by RastaManPower on 2010-10-20
anyone have a solution for this. sorry if i post again but id like to fix this error cause i cant use the computer till i install the OS

---

### Post by dnewkirk on 2010-10-20
What are the settings in the bios? Are you using AHCI or IDE for the harddisks? This may have nothing to do with it, but that can prevent Ubuntu from seeing the drives.

---

### Post by RastaManPower on 2010-10-20
i tryed both ahci and ide. but doesnt work. i am using asus p7p55d-e lx motherboard.

---

### Post by sikander3786 on 2010-10-20
Please post the output of

```
sudo fdisk -l
```

from terminal of a live CD.

---

### Post by RastaManPower on 2010-10-20
tryed that... i get nothing at all
what can i do?

---

### Post by sikander3786 on 2010-10-21
> **RastaManPower said:**
> tryed that... i get nothing at all
what can i do?
Means that Ubuntu is not seeing your HDD at all.

Which HDD in specific? Which motherboard and SATA controller?

You've got 2 HDDs, are you using a RAID configuration?

---

### Post by RastaManPower on 2010-10-21
its a maxtor 320gb sata hd with windows 7 but with 27gb of unallocated space...motherboard is p7p66d/e lx. i have no clue about sata controller. and i cheked bios and i cant see any raid config
[IMG]http://www.glowfoto.com/static_image/21-040139L/4765/png/10/2010/img4/glowfoto[/IMG]

---

### Post by sikander3786 on 2010-10-21
> **RastaManPower said:**
> its a maxtor 320gb sata hd with windows 7 but with 27gb of unallocated space...motherboard is p7p66d/e lx. i have no clue about sata controller. and i cheked bios and i cant see any raid config
[IMG]http://www.glowfoto.com/static_image/21-040139L/4765/png/10/2010/img4/glowfoto[/IMG]
I am in a bit of hurry at the moment. Have to leave. Couldn't find your motherboard specs from Google. Can you post a link?

If you've got more than 1 sata controllers, try plugging the HDD in some other port. They will seem like 2 differently coloured groups of SATA ports on the motherboard. Plug the HDD in the other one and see if it works now. There have been some problems with some SATA controllers.

If not, please post a link to your motherboard specs so we can have a look at it.

Regards.

---

### Post by RastaManPower on 2010-10-21
ok i notused that my motherboard has 8 sata connectors or ports ,i dont know how they are called. 6 of them are blue and 2 of them are white. on the white ones ubuntu wont read my hds but on the blue ones yes. now i am using the blue ones and ubuntu can install but i am getting a weird F1 message after pc boot.how do i fix this F1 error? 

how do i set up this bios settings?
config sata as:ahci/ide/raid
jmicron esata/pata controller: enabled/disabled
marvell storage controller:disabled/idemode/ahci

motherboard model: asus p7p55d-e lx


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x353d494b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       35277   283258880    7  HPFS/NTFS
/dev/sda3           35277       38914    29206528    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdcfbdcfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS


Edit: this is what i was getting with the f1 error. Sata port 2 device error
      i fixed this error by disabling  sata auto monitoring on this port. is this the correct way to fix this error or its just a bypass?

now it seems i can install ubuntu.when booting ubuntu with the live cd it says that my Documents partition "disk failure is imminent"

---

### Post by sikander3786 on 2010-10-21
Load Bios defaults and see if the error goes away by itself.

> when booting ubuntu with the live cd it says that my Documents partition "disk failure is imminent"

It means that your HDD is failing. There have been reports where Ubuntu is false positive about those errors. You can boot into an Ubuntu Live CD and run fsck on your drive to see if the errors are true or false positive.

```
sudo fsck /dev/sd**X**
```

Where 'X' represents the drive you are going to check for errors. More information here.

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

You can also download the diagnostic tools from manufacturer's website and use them to test your HDD. I hope your HDD turns out to be in a good state.

---

### Post by RastaManPower on 2010-10-21
but i have been using this hd for long time and i never had a problem.. even in windows it sayd that it has some problems but it works fine....

---

### Post by sikander3786 on 2010-10-21
> even in windows it sayd that it has some problems but it works fine....

If thats the case, I think your HDD is really corrupted. If is not a false positive report by Ubuntu. Use some diagnostic tool to find out the damage.

---

