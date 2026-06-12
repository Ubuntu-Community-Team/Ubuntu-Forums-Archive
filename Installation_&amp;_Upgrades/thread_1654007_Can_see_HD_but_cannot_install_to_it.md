---
title: "Can see HD but cannot install to it"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by comprx on 2010-12-27
I have attempted this with 10.10 and 9.4 with the same results

I load ubuntu using a live CD select install and when I get to the step where it asks which drive/partition I want, the list is empty.

If I go into "places" the drive shows up. It also shows up in gparted. I think this has nothing to do with the drive its self because I have tried multiple drives.

My Hardware:
Super Micro X5DAL-TG2 MB [http://www.supermicro.com/products/motherboard/Xeon/E7505/X5DAL-TG2.cfm]("http://www.supermicro.com/products/motherboard/Xeon/E7505/X5DAL-TG2.cfm")
Super Micro DAC-ZCRINT RAID controller (tried with and without this) [http://www.supermicro.com/products/accessories/addon/DAC-ZCRINT.cfm]("http://www.supermicro.com/products/accessories/addon/DAC-ZCRINT.cfm")
Processor: 2.4ghz Xeon
2GB DDR RAM
the drive is an 80GB WD 

Ideas?

---

### Post by ronparent on 2010-12-28
Once the raid is activated in bios, it is likely that meta data was written to you disk. This would interfere with the drive being detected. You can try booting to the live cd with the nodmraid parameter written to the menu boot line. If this works and lets the installer see your disk you could go ahead and install. The problematic meta data should be erased to eliminate future problems.

---

### Post by comprx on 2010-12-28
Ok, I detached the HD went into the bios and turned off RAID functionality. I then grabbed a brand new HD and plugged it in. 

I am getting the same result.

BTW I tested a win7 disk and it cannot see the drive either.

Why can Gparted see it and Ubuntu "Places" but I cannot install to it? WFT mate?

---------------------------------------------------------------------------
EDIT: I tried again and it worked just fine. I didn't even have to select a nodmraid option (probably because I switched disks)

Now any idea on how to get it to work using the RAID controller?

---------------------------------------------------------------------------

---

### Post by phptek on 2010-12-28
Assuming the drive is formatted with an appropriate filesystem on it, a long shot but when mounted, is the mount point writable?

```

sudo chmod 777 /media/sdb1

```

Good luck
Russ

---

### Post by dabl on 2010-12-28
Try setting the SATA mode in BIOS to "Legacy IDE" or "compatibility".  If it sees the drive correctly, after you install the OS you can set the mode back to AHCI and it should work correctly.

---

### Post by comprx on 2010-12-28
OK Time for an update on what is going on.

As I said before in my edited post, I grabbed a drive that had not yet touched the machine and the ubuntu installer saw it and began installing. I spoke too soon however about my success, because it would not finish throwing this error:

"Bootloader Install Failed"
It also gives three options:
1. Choose a different device to install the bootloader on
2. Continue without installing the bootloader
3. Cancle the installation

I had it do this on three separate drives.

---

### Post by dabl on 2010-12-28
Make an "Alternate Install" CD, and try that (the installer is different), after you set the SATA mode as I said in the post above.

---

### Post by ronparent on 2010-12-29
```
"Bootloader Install Failed"
```

This is common especially with 10.04. When installing to a raid it generally occurs because you tried ti install to one of the component drive of the raid array. The boot loader has to be installed to the raid array boot loader (ie /dev/mapper/nvidia_abcdef - the first name kisted in /dev/mapper). It is easily fixed with a grub reinstall - [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2.

---

