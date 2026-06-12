---
title: "HD not recognized"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by eventhorizonof on 2010-06-02
Hi, I have just tried to install 10.04 ubuntu and after clicking the desktop icon for install from the live CD (USB stick) it does not recognize the hard drive in the partition section of the installation. Any ideas? 

Its a Western digital HD 1TB SATA, previously used on a windows machine and removed to be used on this ubuntu machine. Is this the problem? Should I change the file system since it was NFTS?

Thanks

---

### Post by darkod on 2010-06-02
If it was ever used in raid, it would have raid metadata on the disk. Even formatting doesn't remove that. The fact that it's ntfs doesn't matter.

Boot into live mode, and in terminal do:

sudo dmraid -r -E /dev/sda

If that asks you to remove raid settings, that was the problem. Confirm and it should be fine.

---

### Post by eventhorizonof on 2010-06-02
After entering 

sudo dmraid -r -E /dva/sda :

it says

 no block devices found

---

### Post by oldfred on 2010-06-02
Was this a typo in the thread or in your command?
sudo dmraid -r -E /[COLOR=DarkRed]dva[/COLOR]/sda
sudo dmraid -r -E /dev/sda

I have also seen were systems were not set for IDE or compatibility or somesuch setting in BIOS. You may want to review the BIOS setttings you have for this drive.

---

### Post by eventhorizonof on 2010-06-03
the output was for  sudo dmraid -r -E /dev/sda

sorry typo on my part

The drive is not showing up in the bios     

where should i go from here?

---

### Post by dino99 on 2010-06-03
> **eventhorizonof said:**
> the output was for  sudo dmraid -r -E /dev/sda

sorry typo on my part

[COLOR="Red"]The drive is not showing up in the bios     
[/COLOR] [COLOR="Blue"]see WD manual installation[/COLOR]
where should i go from here?

you may need to set ahci settings ( see manual)

---

### Post by varunendra on 2010-06-03
Have you crosschecked whether the HDD is detected by BIOS?

(Go into BIOS & see if it is listed correctly there).

---

### Post by eventhorizonof on 2010-06-03
My HDD is not detected by bios. I cannot see it listed. I have a CD/DVD writer that IS detected by bios and it too is SATA. I have tried swapping SATA power cables and this does not solve it.

Here is my setup:

msi g41m4 MB
intel core 2 duo 3.06ghz
dual channel 4gb Gskill DDR2 RAM

---

### Post by darkod on 2010-06-03
> **eventhorizonof said:**
> My HDD is not detected by bios. I cannot see it listed. I have a CD/DVD writer that IS detected by bios and it too is SATA. I have tried swapping SATA power cables and this does not solve it.

Here is my setup:

msi g41m4 MB
intel core 2 duo 3.06ghz
dual channel 4gb Gskill DDR2 RAM

Put it back on the other machine and verify that the disk is working first of all. And you know that HDDs are not hot-swappable right? You have to shut down before connecting/disconnecting them.

If it works on the other machine, check the BIOS settings there and try to select same settings for the machine where you want to use the disk.

---

### Post by eventhorizonof on 2010-06-03
I am not the hot swapping type

I put the drive back in the windows machine and lo and behold it is NOT recognized even by the bios there. 

Is the hard drive dead?

I'm assuming I will have to buy a new HD.

---

### Post by varunendra on 2010-06-03
> **darkod said:**
> If it works on the other machine, check the BIOS settings there and try to select same settings for the machine where you want to use the disk.

Plus - you can try connecting it as the only SATA drive (do not connect the DVD R/w at all) with drive's jumper adjusted to set it to work at lower speed. Increasing the HDD detection time (delay) in BIOS may also help.
We are interested in any progress.

---

### Post by varunendra on 2010-06-03
> **eventhorizonof said:**
> I am not the hot swapping type

I put the drive back in the windows machine and lo and behold it is NOT recognized even by the bios there. 

Is the hard drive dead?

I'm assuming I will have to buy a new HD.

Do you hear some kind of knocking or screeching sound coming out of the disk when connected & powered on? Did you try the delay stuff in the BIOS?

---

### Post by dino99 on 2010-06-03
boot with [http://partedmagic.com/](http://partedmagic.com/), it might find it, then check partitions for errors

what the WD doc says about installing this hdd: how/where to plug it, optional settings, power needed (is your psu strong enough ?)

bios update ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by cascade9 on 2010-06-03
If the BIOS cant see the drive, nothign else will be able to either. 

If varunendras advice doesnt work (run the HDD only, not the HDD + optical, and increasing the detection time) then its probably never going to wrk on that computer...and sicne you tried connecting it to a different machine with no luck, the drive is probably dead :(

---

