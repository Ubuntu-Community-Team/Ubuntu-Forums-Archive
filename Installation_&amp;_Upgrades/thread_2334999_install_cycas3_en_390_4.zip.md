---
title: "install cycas3_en_390_4.zip"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by Timothy_Cota on 2016-08-24
I am running ubuntu 16:04 64 bit  on a Toshiba Tecra M10 s1001  with these specs:
         Intel duo core processor with 2.53 GHZ
         RAM  4G
         SSD 250G with 247 G free space

I want to install:    	 	 	 	   	 	 	 	   cycas3_en_390_4.zip
    I have tried using the software center but it is not recognized.
I have tried synaptic but I can't even get synaptic to recognize it.
I would like to try the terminal
                                               unktim

---

### Post by &amp;KyT$0P# on 2016-08-24
What is the program inside this zip file and where did you get the zip file?

---

### Post by howefield on 2016-08-24
Looks like the Windows version of a CAD application.

You need to extract the files from the .zip and if it is a Windows executable, you would only run it in Ubuntu via an application called Wine, try the [database at the Wine website]("https://appdb.winehq.org/") for possible details. 

If that is the case, any reason why you aren't using the Linux version that is available?

---

### Post by Timothy_Cota on 2016-08-24
The program inside the Zip file is cycas 3 a 2D CAD software.  I downloaded the linux version from C net.

---

### Post by Timothy_Cota on 2016-08-24
This is the linux version.  I extracted the files without any problem but can't do anything from there.  I downloaded from C net out of desperation after numerous attempts to download from the cycas site and getting a 404 error every time.  I will check on that version again.   How do I get rid of these files that were never installed?

---

### Post by &amp;KyT$0P# on 2016-08-24
> **Timothy_Cota said:**
> This is the linux version.  I extracted the files without any problem but can't do anything from there. 
If there is no INSTALL file (installation instructions) or readme of some sort in the extracted files, you probably just extract the zip as a subfolder of your home directory (or /opt for system-wide install) and run the executable?

> How do I get rid of these files that were never installed?
Just delete them?

---

### Post by howefield on 2016-08-25
> **Timothy_Cota said:**
> This is the linux version.  I extracted the files without any problem but can't do anything from there.  I downloaded from C net out of desperation after numerous attempts to download from the cycas site and getting a 404 error every time.  I will check on that version again.   How do I get rid of these files that were never installed?

The reason I said it looks like the Windows version is that the file name for the Windows version, ie CYCAS3_EN_390_4.zip, which seems to be what you have.

The file name for the Linux version is.. : cycas39-en_3.90-5_i386.deb

The Linux version being a .deb package should install simply by double clicking it, assuming that all dependencies can be satisfied. Note it is also 32 bit.

---

### Post by Timothy_Cota on 2016-08-25
thanks.  I will see if I can find a .deb version.  The only .deb version of cycas  is i386.  I am running 16:04 AMD 64. could that be my problem?  
Both ubuntu software and gdebi claimed to have installed it but there is no icon and no evidence of anything but the package.

---

