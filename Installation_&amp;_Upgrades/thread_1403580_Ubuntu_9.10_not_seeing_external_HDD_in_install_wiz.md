---
title: "Ubuntu 9.10 not seeing external HDD in install wizard"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by timcs on 2010-02-10
I have looked around on the forums for this but not been able to see a similar problem. Basically Ubuntu Live CD will see the external HDD to access and see files and folders but when on the install section , where you can choose the drive to install to, the only drive listed is the internal one.

This is a Dell inspiron 5100 laptop and I have installed ubuntu 9.10 onto two different pen drives that are 8gb in size but the HDD will not be listed 

Any ideas?

---

### Post by timcs on 2010-02-10
Forgot to mention that the external HDD is an enclosure allowing IDE drives to be fitted. I am wondering if the drive needs to be set to slave as it is currently master

---

### Post by darkod on 2010-02-10
If you click (just temporarily) on the Erase and use whole disk option, that enables the drop down list under it.
Is it not in that list? Usually you would be able to select it there and then use another option if you don't want to use the Erase and use whole disk option which would wipe the whole drive.
Another possibility is if the drive has been used in raid even for a short while. 9.10 can see raid meta data remains and in the installer doesn't show the disk.

Check with fdisk if it's named /dev/sdb to be sure, and you can check for raid data (and remove it) with:

sudo dmraid -E -r /dev/sdb (use the name of the disk if different)

If that was the problem and you don't plan to use raid, it doesn't hurt doing also:

sudo apt-get remove dmraid

PS. Be careful with the raid removal commands if you actually have raid on the internal hdds, it can destroy the array. They shouldn't be run, especially removal of the dmraid package.

---

### Post by timcs on 2010-02-10
> **darkod said:**
> If you click (just temporarily) on the Erase and use whole disk option, that enables the drop down list under it.
Is it not in that list? Usually you would be able to select it there and then use another option if you don't want to use the Erase and use whole disk option which would wipe the whole drive.
Another possibility is if the drive has been used in raid even for a short while. 9.10 can see raid meta data remains and in the installer doesn't show the disk.

Check with fdisk if it's named /dev/sdb to be sure, and you can check for raid data (and remove it) with:

sudo dmraid -E -r /dev/sdb (use the name of the disk if different)

If that was the problem and you don't plan to use raid, it doesn't hurt doing also:

sudo apt-get remove dmraid

PS. Be careful with the raid removal commands if you actually have raid on the internal hdds, it can destroy the array. They shouldn't be run, especially removal of the dmraid package.

darkod  - as you might have expected the slave option didn't cure it. however I went into gparted and this did find it, the drive is currently on a NFTS system. I used gparted to resize this and give an amount of free space.  

This drive does not get listed if I choose the option where you can select a drive to use. I haven't tried the Erase and use whole disk option would this work differently?

I will try your suggestion regarding the raid check and see if this is the problem - will let you know :D

---

### Post by timcs on 2010-02-10
I issued the raid command as suggested after finding which hdd device it was (as mentioned it was /dev/sdb) ,tried the install wizard again and it still is not listed .By the way ,it is the erase entire drive from the selection i use when choosing the drive.

Any further thoughts ?

---

### Post by darkod on 2010-02-10
Nothing I can think of at the moment. The most frequent issue with the installer not seeing a disk, but gparted and fdisk from live desktop can see it, is the raid issue.
It might not like the situation of a IDE disk connected with usb (I guess that's how it's connected), but this is only speculation.

---

### Post by timcs on 2010-02-11
> **darkod said:**
> Nothing I can think of at the moment. The most frequent issue with the installer not seeing a disk, but gparted and fdisk from live desktop can see it, is the raid issue.
It might not like the situation of a IDE disk connected with usb (I guess that's how it's connected), but this is only speculation.

okay darkod shame really I have a lot of spare IDE drives and would have liked to install to this drive.

I am sure I read somewhere that to install to a USB drive the internal HDD had to be disconnected as though it was some kind of conflict but as this is a laptop I am loathed to do this. I know laptop drives are fairly easy to get at but I prefer not to do this.

It does also seem odd that it is fine with usb pen drives but not usb hdds.

---

### Post by timcs on 2010-02-12
Just and update - I have this another go today and didn't switch on the USB HDD until after the GUI was up .

I ran you RAID command which reported that this drive was not on a RAID. I then ran the installation wizard from the administration menu instead of from the desktop (I presume this should not make a difference) and this then detected the drive :confused:

So the only difference is that the USB drive was not on until after the GUI was up and running and that I ran the install from the menu

---

### Post by darkod on 2010-02-12
> **timcs said:**
> Just and update - I have this another go today and didn't switch on the USB HDD until after the GUI was up .

I ran you RAID command which reported that this drive was not on a RAID. I then ran the installation wizard from the administration menu instead of from the desktop (I presume this should not make a difference) and this then detected the drive :confused:

So the only difference is that the USB drive was not on until after the GUI was up and running and that I ran the install from the menu

Selecting the option from the menu shouldn't make a difference. But plugging the drive after the desktop was loaded might be the reason it worked.
Well, I guess you sorted it out. Go for it now. :)

---

