---
title: "Compaq Presario SR1165CL"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by Ag22 on 2013-06-15
I have an old Compaq Presario SR1265CL desktop that was given to me and I want to remove Windows XP and install Ubuntu. I have tried a few different Linux distributions and none will boot up when I try. I need some help figuring out what to do. Any help would be great.

---

### Post by fantab on 2013-06-16
Post the complete specifications of your PC.  And tell us what exactly happens when you try various distros. What are the error messages? Without this info how are we supposed to help you?

If I remember correctly, the PC you have, has 512MB RAM. Confirm this.

If it does has 512MB RAM then you should consider a RAM upgrade to atleast 1GB. With 1GB RAM you can run **[Xubuntu]("http://xubuntu.org/")** under optimal conditions. 
If you have less than 1GB RAM then Lubuntu is your best bet. Consider [**Lubuntu Alternate Install or Lubuntu Minimal Install**]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").

Both Xubuntu and Lubuntu need a lot less system resources than Ubuntu or Kubuntu need to run. Lubuntu is lighter than Xubuntu.

---

### Post by Ag22 on 2013-06-16
Machine Specs
CPU: 3200+ AMD Athion XP
CPU Speed: 2.20GHz, 512KB L2 cache, 400MHz Front-Side Bus
RAM: 512MB PC2700 DDR SDRAM
Hard Drive: 160GB 7200 RPM Ultra DMA

The error message I get says: Kernel requires x86-64 CPU, but only detects i686 CPU. 
When I tried a 32-bit boot it just says something about inserting a valid boot disk then press enter. 

I have tried lubuntu and it didn't work either. Not sure what is going wrong here, but I would really like to fix it. 

I will upgrade the RAM, but I just want to get windows off of the machine. 

Thanks for the help.

---

### Post by fantab on 2013-06-16
I am not sure if you got 64bit processors with only 512MB RAM... I have my doubts until someone clarifies. 

In all likelihood your PC supports only 32bit. You should download and install 32bit Ubuntu. Make sure your downloaded copy is not corrupt with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") and also make sure you have burned the .iso correctly/properly to the install disk.

If you had downloaded and burned Ubuntu correctly then, assuming you have a 32bit processor, the above message when you run 32bit Ubuntu may have something to with PAE/Non-PAE kernel. For detailed more info see [**HERE**]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html").

Edit: Refer to the following post if you indeed have non-pae cpu:

[http://ubuntuforums.org/showthread.php?t=2133887](http://ubuntuforums.org/showthread.php?t=2133887)

---

### Post by mörgæs on 2013-06-16
There's no PAE problem on AMD processors.
The Athlon XP is 32 bit and should be able to handle Lubuntu 13.04, but perhaps you need the alternate ISO for installing.
If your BIOS supports it best is to install from USB.

---

### Post by Ag22 on 2013-06-17
It does not allow me to boot from a usb.  The only choices I have are from the hard disk or a cd/dvd drive.

---

