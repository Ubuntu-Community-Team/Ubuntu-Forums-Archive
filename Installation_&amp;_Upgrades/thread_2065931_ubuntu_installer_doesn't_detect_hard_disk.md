---
title: "ubuntu installer doesn't detect hard disk"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by bentzi259 on 2012-10-03
hello , im pretty new on lynux and im having problems with the installation ,when i try to install the ubuntu it works all fine untill you need to choose in what hard drive you want to install it
the problem is that the ubuntu does not detect any hard drives on my computer....
iv tried everything:
change the bios setting
replace the sata cabels and ports
i was doing all fine but ubuntu just wont detect my hard disk
something weird is that when i connect the computer to a usb hard drive the ubuntu detect it all fine

pleas help im getting crazy !!!! 

my motherboard :gigabyte ga-b75m-d3h

---

### Post by Bucky Ball on 2012-10-03
Welcome. Your problem might be to do with UEFI disk. Do you have Windows installed already and if so which version?

If you have the hardware specs, make sure you are installing the 64bit version of Ubuntu.

You might like to read the second post on this thread:

[http://ubuntuforums.org/showthread.php?t=2065930&highlight=uefi](http://ubuntuforums.org/showthread.php?t=2065930&highlight=uefi)


PS: Its 'Linux', a merging of Linus (Torvalds, founder) and Unix. ;)

---

### Post by bentzi259 on 2012-10-03
look i dont think its this 

its work perfect on windows 7

in addition , when i press the "try ubuntu" botton it detect the hard disks just fine and even gives me acces to them .....

---

### Post by Bucky Ball on 2012-10-03
Neither condition applies to installing Ubuntu to the hard drive, which is when and where you are getting the error. ;)

If you open Gparted when booting from the LiveCD, how many partitions does it say you have on the disk you are wanting to install Ubuntu to? Attach a screenshot if you like ...

---

### Post by bentzi259 on 2012-10-03
this is the problem it doesn't show any partition !!

---

### Post by Bucky Ball on 2012-10-03
> **bentzi259 said:**
> 
in addition , when i press the "try ubuntu" botton it detect the hard disks just fine and even gives me acces to them .....

You say booting from the LiveCD and trying Ubuntu works fine and you can see them. I'm saying when you are at the LiveCD desktop from 'Try Ubuntu' launch Gparted (System>Administration>Gparted or Partition Editor from memory, I use Xubuntu) and see what it reports for the drive you want to install to. Or you can take a screenshot and attach it (Apps>Accessories>Screenshot). Avoid posting it in the body of the post. Also, open a terminal (Applications>Accessories>Terminal) and paste this in:
```

sudo blkid
```Post the result back here, thanks.  ;)

---

### Post by bentzi259 on 2012-10-03
No man it didn't work...
Look I succeed to upload a picture, you can see here that the hardware is detected on live cd but not on the installation
[http://www.f2h.co.il/5w402el2poit](http://www.f2h.co.il/5w402el2poit)

---

### Post by Bucky Ball on 2012-10-03
Sorry, that site is in a language I don't understand and I wouldn't know where to find the pic.

---

### Post by bentzi259 on 2012-10-04
look at the images:




[http://imageshack.us/a/img571/7107/screenshotfrom201210040.png](http://imageshack.us/a/img571/7107/screenshotfrom201210040.png)

[http://imageshack.us/a/img856/7107/screenshotfrom201210040.png](http://imageshack.us/a/img856/7107/screenshotfrom201210040.png)

[http://imageshack.us/a/img528/7107/screenshotfrom201210040.png](http://imageshack.us/a/img528/7107/screenshotfrom201210040.png)


[http://imageshack.us/a/img837/7107/screenshotfrom201210040.png](http://imageshack.us/a/img837/7107/screenshotfrom201210040.png)


from the last picture theres not where to continue and of course it detects them from the bios setting and from the boot menu and from the disk utility in ubuntu

im frustrated !!!!!!

---

### Post by egalua on 2012-10-04
I could have produced exactly the same images!

---

### Post by egalua on 2012-10-04
Well, here is the actual output of fdisk:

---------------------------------------
root@ubuntu:~# fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e287

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   82  Linux swap / Solaris
/dev/sda2         8390656   159942655    75776000   83  Linux
/dev/sda3       159942656   312498175    76277760   83  Linux
-------------------------------------------

As a last try, I resetted the MBR, but it didn't help... :(

---

### Post by egalua on 2012-10-04
I tried to change the hard disk: same result.

At the end, I tried with another distribution.
First, I tried with ubuntu 12.10 beta: same result.
Then I tried with opensuse and it installed without problems.

First conclusion: I think there is a bug in the installer (ubiquity) which affects _exactly_ my hardware configuration.

Second conclusion: I have to quit ubuntu for something else..... :(

---

### Post by egalua on 2012-10-04
I also tried ubuntu 11.10 and I got the same problem.

In this very moment, I am writing while linux mint debian edition is installing correctly.

Definetely, I think this problem is a bug of ubiquity.

Where, and how, can I submit this bug?

---

### Post by darkod on 2012-10-04
Did any of you try to see if there is raid meta data present on the disk? If a disk has been used in fakeraid (biod raid) before, it keeps the meta data since most people only disconnect it and don't destroy the array properly. I'm not sure if it keeps the meta data if you destroy the array using the raid settings.

Anyway, formatting doesn't help in this case, since the meta data is kept.

What you can do from live mode to see if you are affected, is run this for disk /dev/sda (or change with /dev/sdX if the disk is called differently):
sudo dmraid -E -r /dev/sda

If it asks you if you want to remove meta data, this was the issue. Confirm and the installer will see the disk.
If it has meta data it's ignored so that you don't install on existing raid array and destroy your data.

PS. Also, if UEFI device is offered for boot, that means your board is UEFI capable, and you have to think carefully what you enable in BIOS since UEFI works in different way, especially if you plan to dual boot. There are still issues to be solved for UEFI dual boot.
If you are happy with the old ways, just disable UEFI in BIOS if you have that option, and you're good to go. The setting for the sata mode should be AHCI, works much better than IDE.

---

### Post by egalua on 2012-10-04
Darkod, you are just right!!!!!

Thank you a lot.

I already was suspecting that the disk was used in raid because the boy at the computer store said that it could let me try the "twin" of the previous hard disk...
But knowing nothing about raid (but the definition) I didn't suspect it was relevant to this matter!

Thanks again.

About UEFI, I know it is still a somewhat a problem, but in my case I think I can ignore it: this computer is never going to see anything else than linux. May be it will be updated, sooner or later, but again with linux.

Regards

---

