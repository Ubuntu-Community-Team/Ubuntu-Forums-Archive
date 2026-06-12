---
title: "Need to Move Grub from MBR to Partition"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by goedls on 2012-05-24
The company I work for is mandating laptop hard drive encryption and using Truecrypt. Currently I have a dual boot setup, Win 7 Ubuntu 12.04 and a data partition that I share between the two.  I can use Truecrypt but it does not support full disk encryption on multiboot systems.  My IT department will allow me to encrypt just the Windows and data partitions since I do not keep sensitive data on the Linux partition.  Truecrypt needs to use its own boot loader to sort things out at boot. Grub sits on the MBR so I need to know how to move Grub to the Linux Partition.

Alternatively it there another open source full disk encryption I can use that will work with multiboot systems?

---

### Post by grahammechanical on 2012-05-24
Install Grub Customizer

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

In the File menu it has an option to Install to MBR and it will then let you select where to install it whether sda or a partition. I think that this is true. I have never tried it myself. So I have never looked beyond the sda option.

I see this from that link

> Accessed via the main menu "File" option, GC allows the user to select a partition on which to perform operations.

Regards.

---

### Post by darkod on 2012-05-24
I think you can force it to install on a partition with -f. So, boot your ubuntu, and lets say you want to install on sda5, try something like:

sudo grub-install -f /dev/sda5

After that, remove the relation of grub2 with /dev/sda with:
sudo dpkg-reconfigure grub-pc

You select/deselect with Spacebar.

Note that when grub2 is on a partition an update/upgrade can break it, so you will need to reinstall it, this time from live mode probably.

---

### Post by goedls on 2012-05-25
Thanks darkod, that is how I did it.  

I did notdo this yet:
After that, remove the relation of grub2 with /dev/sda with:
sudo dpkg-reconfigure grub-pc

You select/deselect with Spacebar.

If I do an update-grub with out it will it overwrite the Truecrypt boot loader?

My Linux partition is mounted on /dev/sda6.  My concern had been that I have read Truecrypt will not load the Linux partition if it is on anything other than sda2.  

I did it anyway and it is all working fine.

---

### Post by darkod on 2012-05-25
I don't know all the specific details unfortunately.

I think the update-grub is not a problem. The problem is when there is an update of the grub-pc package, it knows where it's installed and tries to update there too. I think this is what you avoid with the dpkg-reconfigure.

You reconfigure grub-pc so that the only location it's aware of, is sda6.

---

