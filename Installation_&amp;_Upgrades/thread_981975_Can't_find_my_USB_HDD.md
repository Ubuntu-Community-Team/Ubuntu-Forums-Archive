---
title: "Can't find my USB HDD"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Roger Allott on 2008-11-14
Hi guys, total newbie to Ubuntu here!

What I'm trying to do is to install Ubuntu 8.10 to an external HDD so that the main HDD in my laptop (Fujitsu-Siemens Amilo Pi 2515) is dedicated to my usual OS (Windows Vista Home Premium).

I can run the Live CD and one of the things I like about Ubuntu over other Linux distros is the simplicity of installing via the "Create a USB startup disk" under the System > Administration options.

However, when the dialogue box comes up, there's nothing to select in the "Select the USB disk to use" list.

This seems odd, because when I insert the USB HDD into the computer Ubuntu recognises it and opens the file browser screens for each of the three partitioned segments.

Has anyone got any ideas as to how I can force the "Create a USB startup disk" box to notice that my USB HDD has been inserted?

---

### Post by razy60 on 2008-11-14
Don't know about forcing the connection but have you tried to set one of the partitions as fat32, then tried it. 
Also try unetbootin as it will give you the option of which distro to load and where to load it to, it seems to work best in windows, as a program that is.
couple of links for you.
[http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot](http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

hope it helps
Raz

---

### Post by Roger Allott on 2008-11-14
Thanks Raz. Yes, one of my partitioned segments is FAT32, as I previously installed openSUSE on it in an earlier incarnation.

To be clear in what my problem is, it's the dialogue box shown below that I've taken from pendrivelinux.com:

[IMG]http://www.pendrivelinux.com/wp-content/uploads/creating-usb-ubuntu.png[/IMG]

The problem I'm getting is that nothing is appearing at all in the "USB disk to use:" area.

---

### Post by taurus on 2008-11-14
From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Roger Allott on 2008-11-14
> **taurus said:**
> From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Here's the output:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x509ee0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda4           13567       19458    47314944    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2010    16145293+   7  HPFS/NTFS
/dev/sdb2            2011        8538    52436160    5  Extended
/dev/sdb3            8539        8610      578340   82  Linux swap / Solaris
/dev/sdb4   *        8611        9729     8988367+  83  Linux
/dev/sdb5            2011        8538    52436128+   7  HPFS/NTFS
```

Is that any help?

---

### Post by taurus on 2008-11-14
Is /dev/sdb (80GB) your external USB drive?

---

### Post by Roger Allott on 2008-11-14
> **taurus said:**
> Is /dev/sdb (80GB) your external USB drive?

Yes. The 160Gb is my internal HDD.

---

### Post by Roger Allott on 2008-11-15
As an alternative solution, what about if I just do a standard install and when it asks me which drive to install to I select one of the ones on my USB HDD?

BTW, I've already tried a more obvious option where I exchange the HDD in my USB drive with the internal HDD, but I can't because the USB one is a PATA connection and the internal one is SATA.

---

### Post by taurus on 2008-11-15
Looks to me like you already have a previous Linux distro and a couple of ntfs partitions on that external harddrive, /dev/sdb.

---

### Post by Roger Allott on 2008-11-15
> **taurus said:**
> Looks to me like you already have a previous Linux distro and a couple of ntfs partitions on that external harddrive, /dev/sdb.

Yes. Is that a problem? Does it explain why the "Create a USB startup disk" doesn't 'see' my external HDD? Should I reformat one of the partitions? If so, how do I do that?

I thought the Ubuntu install would reformat whatever disk was targeted as part of the process. Am I wrong in that assumption?

The previous Linux distro on /dev/sdb3 and /dev/sdb4 (no idea why there's two of them!) was for openSUSE, which I installed a couple of years ago but didn't like for connectivity reasons.

---

### Post by Roger Allott on 2008-11-15
Is there ANYONE out there who can help me with this problem?

It seems pretty damn basic that if you're offering an option on your O/S it might just be a good idea for it to work.

Microsoft might be prone to security breaches and be way expensive, but at least it WORKS!

---

### Post by gibbylinks on 2008-11-18
Did anyone find a solution to this ?

My USB key is not showing up in "Create A USB Startup Disk" either.

:(

---

### Post by Rohan Kapoor on 2008-11-18
> **Roger Allott said:**
> Here's the output:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x509ee0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda4           13567       19458    47314944    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2010    16145293+   7  HPFS/NTFS
/dev/sdb2            2011        8538    52436160    5  Extended
/dev/sdb3            8539        8610      578340   82  Linux swap / Solaris
/dev/sdb4   *        8611        9729     8988367+  83  Linux
/dev/sdb5            2011        8538    52436128+   7  HPFS/NTFS
```

Is that any help?

You know. I get the feeling that you have your drive mounted while doing this. Right click on drive and unmount. Try again and your drive should be visible!

---

### Post by Roger Allott on 2008-11-18
> **darth-vader said:**
> You know. I get the feeling that you have your drive mounted while doing this. Right click on drive and unmount. Try again and your drive should be visible!

Ummm.... ah ..... you might be right. Could someone please explain what mounting a disk means and why it's important for it not to be mounted when and why?

Or a link to a tutorial on the subject would be good too.

BTW, one of the main reasons I want to install to the external drive is so that I can load the drive into another old computer and run Ubuntu from there as an option. Is that a good idea or not? There are various reasons why I can't install Ubuntu directly onto the old computer, mainly to do with the fact that my CD/DVD player in it has given up the ghost and it can't boot from USB.

---

### Post by Rohan Kapoor on 2008-11-18
Mounting a disk (in windows) means giving it a drive letter. (In linux) it means accessing the files and folders stored on it in a directory. See: [http://kb.iu.edu/data/anqk.html](http://kb.iu.edu/data/anqk.html) The problem here is that you can't install an operating system while mounted. To unmount: right click on the usb hard disk on your desktop, select unmount volume. Then you should open the install wizard you are using and try again.

---

