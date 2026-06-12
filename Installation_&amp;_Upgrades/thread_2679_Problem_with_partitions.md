---
title: "Problem with partitions"
date: 2004-10-30
forum: Installation &amp; Upgrades
---

### Post by peake on 2004-10-30
I'm trying to create a reiserfs partition, but I'm always getting the following error: 
Stat of the device '/dev/ide/host0/bus0/target0/lun0/part3' failed
Anyone can help?

Thanks!

---

### Post by butters on 2004-10-30
In the installer or afterwards?  What command are you using?  What is the output of 'mount'?

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=peake]I'm trying to create a reiserfs partition, but I'm always getting the following error: 
Stat of the device '/dev/ide/host0/bus0/target0/lun0/part3' failed
Anyone can help?

Thanks![/QUOTE]


I suppuse your doing it after the installation due to the error message provided.  I would first like for you to have a look at your RAID settings.   THis is usually a RAID problem.  If no raid is available then I would encourage you to stop the Software Raid Services under Ubuntu.

Software Raid: mdadm

---

### Post by peake on 2004-10-30
This is during installation and I don't use any RAID at all.
 I managed to do my partitions  (NTFS FAT reiserfs SWAP) and formating using a live CD, but now the installer tells me : 
'The attempt to mount a file system with type reiserfs in IDE1 master partition #3 () at / failed'

I also tried to mount my third partition (reiserfs) but there is no mention of hda3 in /dev.

---

### Post by peake on 2004-10-31
If I give the ouput of dmesg and/or installer log will it help?

---

### Post by FLeiXiuS on 2004-10-31
[QUOTE=peake]If I give the ouput of dmesg and/or installer log will it help?[/QUOTE]

Logs are always helpful.

---

### Post by peake on 2004-10-31
I would like to saves logs on my FAT partition, but I can't mount it because there's no mention of /dev/hda2, is that normal? Does udev store them elsewhere?

---

### Post by az on 2004-10-31
Devfs means that there are no files in /dev other than the actual devices present.  This has many advantages, among saving ram if your filesystem is on a ramdisk - like the installer.

In devfs, the names are different.
for example, '/dev/ide/host0/bus0/target0/lun0/part3' is in your case hda3.

I assume that you tried to create your partitions beforehand, using a live cd.  Why dont you try to use the installer to format the filesystem on your hda3 ('/dev/ide/host0/bus0/target0/lun0/part3')
Just select format the partition as reiserfs and tell it to mount it as /.

If you have already done this with the installer, try proceeding with a ext3 filesystem, to rule out a hardware glitch.

Good luck!

---

### Post by peake on 2004-11-04
Well I tried to let the installer do the partitionning for me, and it didn't work either. So I tried to install Slackware 10 , no problem, then Fedora Core test 3, also no problems. 
Can this be an Ubuntu installer bug?

---

### Post by ventzo on 2005-07-24
[QUOTE=peake]Well I tried to let the installer do the partitionning for me, and it didn't work either. So I tried to install Slackware 10 , no problem, then Fedora Core test 3, also no problems. 
Can this be an Ubuntu installer bug?[/QUOTE]
 Hi everybody,
Sorry for my bad english. ;)
I have same problem.

My PC:
 
K6-2 400 MHz
3.2 HDD Seagate.
256 MB SDRAM

Yesterday I tryed to install Ubuntu 5.04 but when the install come to make partition all was bad.
When I tryed to make swap 172.7 MB and 3096.7 MB ext3 and when I tryed to save partitions  place I have same problem like "peake".

I don't know why this hapend but I was instaled beffore Slackware 10.1, Redhad, mandrake, debian, minislackware 0.04 and t.n.

If anyone have same problem like our "peake and me ventzo" please tell me how you fix it.

10x a lot.

---

### Post by ventzo on 2005-07-26
hi all,
I fix partitions problem.

With hdd Seagate program. Deleted all options and MBR and all it's OK. 

;) \\:D/

---

