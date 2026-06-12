---
title: "Help regarding unetbootin on XP"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by sosaited on 2010-01-19
Hi.

I am downloading Ubuntu 9.10, and was looking for some other way than burning the ISO to install it when I found Unetbootin.

I have already downloaded it, but I have just one confusion. When I select the type as Hard Disk at the bottom, I only have the option to select C: drive which is my windows partition. I have already made separate ext3 and swap partitions for Ubuntu to install in. So is this option just for temporary boot files, or the final destination for Ubuntu?

---

### Post by adam814 on 2010-01-19
UNetbootin is primarily geared towards making LiveUSB thumb drives from LiveCD images.  It's not meant to actually install Ubuntu into a hard drive partition as you'll end up with the Live version that takes forever to boot.

But you could use it to make a thumb drive to install from.

---

### Post by C.S.Cameron on 2010-01-20
You can extract the iso to a folder with Winrar and then run wubu.exe.
This will put Ubuntu on your hard disk.

---

### Post by mk1w86 on 2010-01-20
> I only have the option to select C: drive which is my windows partition.

You cannot see the ext3 partition because Windows cannot read it although you wouldn't want to install this way.

> You can extract the iso to a folder with Winrar and then run wubu.exe.


I would strongly advise you not to use Wubi because there have been a lot of problems and bugs with it in Ubuntu 9.10, you are much better off installing Ubuntu to its own partition as you are doing. ;)

Is there any reason why you can't burn a live CD?  Otherwise use a bootable flash drive created with Unetbootin as a poster above suggested. :D

---

### Post by snowpine on 2010-01-20
> **sosaited said:**
> When I select the type as Hard Disk at the bottom, I only have the option to select C: drive which is my windows partition. I have already made separate ext3 and swap partitions for Ubuntu to install in. So is this option just for temporary boot files, or the final destination for Ubuntu?

Temporary boot files. When Unetbootin is done doing it's thing, you should be able to reboot into the Ubuntu Live "CD" (without the CD). Then, you install Ubuntu to the new partition you've created. Once you've installed Ubuntu, you can run Unetbootin again (from Windows) to remove the temporary files.

I hope you have backed up everything important first. :)

---

### Post by adam814 on 2010-01-20
> **snowpine said:**
> Temporary boot files. When Unetbootin is done doing it's thing, you should be able to reboot into the Ubuntu Live "CD" (without the CD). Then, you install Ubuntu to the new partition you've created. Once you've installed Ubuntu, you can run Unetbootin again (from Windows) to remove the temporary files.

I hope you have backed up everything important first. :)


No, if you select the Windows C: drive it will overwrite parts of your Windows install.  You might have to check the "show all drives" box to get the flash to show up.  Also it should be formatted fat32 and not ext3 for Unetbootin in Windows to read it properly.

---

### Post by snowpine on 2010-01-20
A lot of uneducated answers in this thread. :(

Read the instructions: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> Features

UNetbootin can create a bootable Live USB drive, **or it can make a "frugal install" on your local hard disk if you don't have a USB drive.**

(emphasis added)

---

### Post by mk1w86 on 2010-01-20
> **snowpine said:**
> A lot of uneducated answers in this thread. :(

Read the instructions: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)



(emphasis added)

Sorry, I wasn't aware that you could do a Unetbooin install within a Windows installation, I always assumed it would require a separate partition so it would not interfere with Windows. :oops:

---

### Post by adam814 on 2010-01-20
> **mk1w86 said:**
> Sorry, I wasn't aware that you could do a Unetbooin install within a Windows installation, I always assumed it would require a separate partition so it would not interfere with Windows. :oops:
Ditto.  Good idea, I just wouldn't have thought so.

---

### Post by C.S.Cameron on 2010-01-20
Thanks Snowpine:
I haven't tried that feature in unetbootin before.
I think that option is much better in this case than just installing with wubi.

---

