---
title: "Installing Ubuntu onto a Slave Drive"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by ShadowLife on 2010-11-07
So i am currently running Windows XP on my Master Drive, and i wanted to learn Linux. But since this PC is shared by other people, i cant just get rid of Windows, so i got a another HD. Can i download Ubuntu onto my Master Drive, and run the installation from my Master Drive and have it install onto my Slave Drive? Or... is there an easier way?

---

### Post by tkoco on 2010-11-07
> **ShadowLife said:**
> So i am currently running Windows XP on my Master Drive, and i wanted to learn Linux. But since this PC is shared by other people, i cant just get rid of Windows, so i got a another HD. Can i download Ubuntu onto my Master Drive, and run the installation from my Master Drive and have it install onto my Slave Drive? Or... is there an easier way?

If the system can boot from a CD or USB drive, you can use a "LiveCD" to boot up into Ubuntu Linux. The beauty of doing it this way is that windows is left untouched. When you are finished, do a reboot and remove the media. Then the system will come up in windows as if nothing had happened.

If the system has sufficient resources, you could run Ubuntu in a virtual machine. To windows, a virtual machine looks like a binary file. But when you run the virtual machine program, the file looks like a different machine - kind of a computer in a computer.

Hope this helps!

---

### Post by ShadowLife on 2010-11-07
So i download Ubuntu, make a live CD, and it will give me an option as to which HD i want the OS to install to?

---

### Post by tkoco on 2010-11-07
> **ShadowLife said:**
> So i download Ubuntu, make a live CD, and it will give me an option as to which HD i want the OS to install to?

Yes it does. But the primary boot harddrive will need GRUB installed on it to manage the boot up sequences. Just make sure you match up the version of Ubuntu to the hardware - 32 bit vs 64 bit.

---

### Post by ShadowLife on 2010-11-07
Aight ima install GRUB then Dl the Live Cd, and try this out 2morro. I will post and tell you how it went.
Thanks for the Help.

---

### Post by ShadowLife on 2010-11-08
Ok, i downloaded GRUB, but i dont see how I am supposed to install it.. Do i just drop the fold into a certain file on my PC?

---

### Post by efflandt on 2010-11-08
If your computer has the ability in BIOS to select which drive to boot from, you might want to put grub on your second drive, instead of default to mbr of your main hard drive, which would leave your main hard drive untouched.  Then others that use your computer would not be confused by the grub menu (WinXP would boot normally).  And usually using a specific key in the BIOS splash screen (often F12 or Esc) you could select to boot your second drive.

You don't need to download grub separately, that is included with the Ubuntu install CD.  To put grub on your 2nd drive with **Ubuntu 10.10** you would need to use manual partitioning and at the bottom of that page you can select where to put grub.  Unless you have mixed PATA and SATA drives, your second drive is typically /dev/sdb.

In **Ubuntu 10.04 or earlier**, if you want to put grub on a different drive, after the step where you enter your username and password, you have to pay attention to the **Advanced** button.  That button is used to tell it where to install grub.  But the whole installation changed for 10.10.

If you are uncertain of anything, you might want to post the output of **sudo fdisk -l** (small L) here, so we could see what is on which drive.  After you paste the output from that here, put code tags around it to maintain its formatting by highlighting it and clicking **#** at top of message window.

---

