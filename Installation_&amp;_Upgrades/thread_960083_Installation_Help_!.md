---
title: "Installation Help !"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by amohan on 2008-10-27
My PC has 3 SATA Hard Disks
Disk 1. 500 GB With Vista on 1st Partition, 2nd for data  
Disk 2. 120 GB With 40 GB Free 1st Partition (free) Rest as 2nd Partition for data.
Dusk 3. 320 GB with Windows XP Pro on 1st Partition, 2nd for data

I want to install Ubuntu desktop on by drive No. 2.

Need help in doing the same as when I try and install from CD I get confused as to how to achieve the following -

Scene 1
From Bios, if I select Disk 2 as my boot disk, then Ubuntu should be able to boot in 1st 40 gb partition of this Disk 2 and rest of the partition and Disk 1 & 3 should be left alone as they are.

Scene 2
From Bios, if I select Disk 1 or Disk 3 as boot disk then system should boot in Vista or XP as desired with 2nd Partition of Disk 2 available for these Operating systems to store backup data on.

I'm a newbee to Ubnuntu so please help me in this problem !

Thanks,
Amohan

---

### Post by Herman on 2008-10-27
:) You need to look for the 'Advanced' button in step 7 of 7 , click it and then hit the down-arrow to the left of the 'Device for Boot Loader Installation' field.
Select (hd1) for number two hard disk's MBR.

Normally by default, if you didn't select (hd1), Ubuntu would install GRUB to (hd0), which would be your first hard disk, because GRUB begins counting at zero, that is why you should select (hd1), for second hard disk. 

If you do that successfully then you should be able to boot it from the BIOS without and problems, as you want.

If you would like to see some illustrations of what I'm talking about, click the following link and scroll down to illustration number 020, here's the link, [COLOR=#000000][/COLOR][Hardy Heron LTS / Windows XP Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html")

Regards, Herman  :)

---

### Post by amohan on 2008-10-29
Thanks Herman, as this is my weekend project, will let you know soon how far your help took me :-)

---

### Post by amohan on 2008-11-03
Thanks Herman!

Did as u suggested and alls working well.

---

