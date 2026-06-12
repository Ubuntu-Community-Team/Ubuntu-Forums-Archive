---
title: "Two hard drives, let me ask you some advices for a fresh, clean, power installation"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by kvanoff on 2015-11-21
Hi all, this is my second post here, so i feel kind an obligé to salutations. 
My old computer left me some weeks ago so i decided to buy a new machine. This new machine has an hd 1TB, with the default windows installed on it. Now what i did when i unpacked the new pc it was to take my old hd with ubuntu and to link it to the new computer with an external usb support. So now i've got a dual boot, less or more (because from the ubuntu side not everything it is going well). My question is, how shall i manage this two hard drive (1hd 1TB, 2 hd 640GB) to have a single system on this pc? 
What would you do? Thanks in advance.

---

### Post by brian-mccumber on 2015-11-21
Well you're having problems with your Ubuntu install on the new computer because it is configured to the hardware from your old computer. If it was me I would overwrite Windows with Ubuntu and use the other drive as extra storage.

---

### Post by kvanoff on 2015-11-21
Yes, i would do that too, but first in the other hard drive there is already an existing installation of Ubuntu: how can i save those files who are in the hd before format it and leave him has /storage as you said?

---

### Post by brian-mccumber on 2015-11-21
Try to boot Ubuntu from the installation disk without installing it, then transfer your files to something else like a usb drive or even cd's/dvd's, then you can go back and put a fresh install on the hdd that will be configured to your new hardware. Booting from the disk first before installing will also tell you if your new hardware is compatible with Ubuntu.

---

### Post by Bashing-om on 2015-11-21
kvanoff; Hello;

One has to make sure that IDs on the hard drive match the new hardware,
1) UUIDs in /etc/dstab
2) (RE-)install grub ( from a liveUSB)
3) Boot the install to a terminal and revert all proprietary drivers to open source, then as required (RE-)install the drivers .

I would not expect it to be too big of a deal IF this new system is NOT UEFI and the old install is MBR. Even in the event of UEFI/MBR, being as how the installs are on separate hard drives, one should be able to work around the booting in the firmware ( bios) .

The kernel is smart - real smart - but
[INDENT][INDENT][INDENT]sometimes it needs a helping hand
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-11-21
If you don't want Windows

1) Put a fresh install of Ubuntu onto the 1 TB hard drive
2) Copy your data from the 640Gb hard drive on to the 1 TB hard drive
3) Now do what you like with the 640 GB hard drive

If you do want Windows

1) Use Windows utilities to create unallocated space on the 1 TB hard drive. There is plenty of it.
2) Use the Ubuntu live session & GParted to create an Ext4 partition out of the unallocated space
3) Use the Ubuntu live session to back up your data to the Ext4 partition on the 1 TB hard drive
4) Put in a fresh install of Ubuntu on the 640 GB hard drive
5) Transfer the data from the 1 TB hard drive to the 640 GB hard drive or leave it where it is and use that partition as a data partition for Ubuntu.

Regards.

---

### Post by kvanoff on 2015-11-21
thanks to all for the answers,
> 
Grahammechanical

If you don't want Windows

1) Put a fresh install of Ubuntu onto the 1 TB hard drive
2) Copy your data from the 640Gb hard drive on to the 1 TB hard drive
3) Now do what you like with the 640 GB hard drive


So, are you sure that from the new installation of ubuntu on the HD1TB i will be able to see and move the files that are on other hd?

---

### Post by kvanoff on 2015-11-22
Come on, please. What i meant was, if i make a new fresh installation of  ubuntu on the hd 1TB. From that installation will i be able to interact  with files that are on the other hard disk where there is another  ubuntu installation? Please let me know before i rty. Thanks.

---

### Post by Bashing-om on 2015-11-22
kvanoff; Hey:

I let my terminal do all the talking:
```

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~

```
where I am booting 5 'buntus and can access any and all of them .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

