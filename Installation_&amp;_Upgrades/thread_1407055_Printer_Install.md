---
title: "Printer Install"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by cnapolitano on 2010-02-14
I found a Linux driver for my Lexmark x2600.  Everytime I try to install it, it says I need CUPS 1.2 or higher.  I have tried sudo apt-get install cupsys and it says I have the current version.  I know there is a version 1.4.2 of CUPS.  How to I get this version through the terminal?  Any help will be appreciated.

Thanks

---

### Post by Yogotiss on 2010-02-14
Which version of Ubuntu is this?

---

### Post by sgosnell on 2010-02-14
cups and cupsys are not the same package.

---

### Post by cnapolitano on 2010-02-14
It's ubuntu 9.1.  I know they are different.  How to I install CUPS 1.4.1.  I am very new to Linux .  Any help would be appeciated

---

### Post by mionescu on 2010-02-14
If you have Ubuntu 9.10 (and not 9.1) then cups 1.4.1 should be already installed. You can double check by opening Synaptic from the System menu and search for cups.

---

### Post by Steel-Bunz on 2010-02-14
Ubuntu's official repositories will not upgrade to a newer version of a software within a version. For example, in 9.10, you have Firefox 3.5; you will not get Firefox 3.6 until you move on to the next release Lucid. Since you are using 9.10, you cups version should be 1.3.9-17 (Start Synaptic Package Manager and search CUPS), which is newer than 1.2 that you need.

Obviously, there are workarounds. You need to add different "Software Sources" (PPA repositories) which will provide you with newer version of a software compared to the official sources. I believe you need to search CUPS forums to get the PPA repository names...

Disclaimer: I don't know much about CUPS, but, I thought I could you some generic info. :) I hope I didn't waste your time.

---

### Post by mionescu on 2010-02-14
The version of cups in 9.10 (Karmic) is 1.4.1. See
[http://packages.ubuntu.com/karmic/cups](http://packages.ubuntu.com/karmic/cups)

---

### Post by Steel-Bunz on 2010-02-14
> **mionescu said:**
> The version of cups in 9.10 (Karmic) is 1.4.1. See
[http://packages.ubuntu.com/karmic/cups](http://packages.ubuntu.com/karmic/cups)

Sorry, my mistake.. :(

In fact, I was taking too long to type the reply and missed your post.. Glad to know that these forums are so active=D>

---

### Post by mionescu on 2010-02-14
> **Steel-Bunz said:**
> Sorry, my mistake.. :(

In fact, I was taking too long to type the reply and missed your post.. Glad to know that these forums are so active=D>

Don't worry about it. I just didn't want to confuse cnapolitano.

By the way, back to the original question. cnapolitano, can you explain the steps you performed and what was the error you received?

Did you download the drivers from
[http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=x2600&productCode=LEXMARK_X2600&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2600&searchid=1266203546197#2](http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=x2600&productCode=LEXMARK_X2600&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2600&searchid=1266203546197#2) ?

I noticed that they only provide a driver for 32 bits and not for 64 bits. Do you have the 64bits version of Ubuntu? If so, you might be out of luck. If you have the 32bits version, can you please describe what you did?

---

### Post by cnapolitano on 2010-02-15
Yes I am running the 32 bit version of Ubuntu.  When I go to install the Lexmark drivers that I downloaded from there site.  I go to install the driver and get this error: The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.  I go into Synaptic and search for CUPs and it says I have version 1.4.1-5ubuntu2.2.  So to me I do have a higher version or am I wrong.  Thanks for all the continued help

charlie

---

### Post by mionescu on 2010-02-15
I managed to install the driver on my computer. I do not have this printer so I can not really test it. I will describe next the steps I did in order to overpass the installer limitation. Again, these instructions come with no guarantee. I know it is an ugly hack but it seems it works. Lexmark should really update their installer.

Step 1.
Run the installer as you did already. When you see the error message that your version of cups does not meet CUPS requitement *DO NOT* press OK. Leave it like this for now. Otherwise the installer erases all the files we need to access in step 2.

Step 2. 
We want to find the deb file containing the driver and install it. The installer extracted the files somewhere in the /tmp folder. 
So open a terminal window (from the Utilities menu). Log in as a root  by typing the following command (otherwise I was not able to access the folder I need):
sudo su

and enter your password, if needed. Then change to the temporary folder:
cd /tmp

Now type 
ls

to see a list of folders. One of them should begin something like "selfgz#" where # is a number. In my case it was selfgz2777. Go into this directory. I typed
cd selfgz2777

Then type
cd pkg/files

to enter the folder where the deb file is. If you type 
ls

you should see a list of files and one of the should be "lexmark-inkjet-08-driver-1.0.1.i386.deb". Install it by
dpkg -i lexmark-inkjet-08-driver-1.0.1.i386.deb

Now the instalation should be complete. Close the terminal window, press OK in the Lexmark installer (this will erase all the temporary files), and try your printer. 

I hope it works.

---

### Post by sgosnell on 2010-02-15
I don't know why you're having your problem.  I'm running 9.10, and I downloaded the zip file from the Lexmark site, and installed it with no problems, at least until I reached the part where it wanted to connect the printer.  I have no such printer, so I had to abort the install from there, then remove the driver.  It would appear to be a configuration problem on your system, but I don't know where to start.  You might try running Synaptic and marking CUPS for reinstallation.

---

### Post by cnapolitano on 2010-02-15
I tried what you said to do and this is what i get: root@cnapolitano-desktop:/home/cnapolitano# cd /tmp
root@cnapolitano-desktop:/tmp# ls
keyring-auu3mM     pulse-FWqaR8DfVH3F  selfgz2636      tracelog
orbit-cnapolitano  seahorse-QPQRmQ     ssh-kWMaZo1508  virtual-cnapolitano.IVWCIz
root@cnapolitano-desktop:/tmp# cd selfgz2636
root@cnapolitano-desktop:/tmp/selfgz2636# cd pkg/files
root@cnapolitano-desktop:/tmp/selfgz2636/pkg/files# ls
jre1.6.0_07.bin  launcher.c                               lsbrowser    lxklpia.sh
launcher         lexmark-inkjet-08-driver-1.0-1.i386.deb  lsusbdevice
root@cnapolitano-desktop:/tmp/selfgz2636/pkg/files# dpkg -i lexmark-inkjet-08-driver-1.0.1.i386.deb
dpkg: error processing lexmark-inkjet-08-driver-1.0.1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lexmark-inkjet-08-driver-1.0.1.i386.deb
root@cnapolitano-desktop:/tmp/selfgz2636/pkg/files# dpkg -i lexmark-inkjet-08-driver-1.0.1.i386.deb
dpkg: error processing lexmark-inkjet-08-driver-1.0.1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lexmark-inkjet-08-driver-1.0.1.i386.deb
root@cnapolitano-desktop:/tmp/selfgz2636/pkg/files# ls
jre1.6.0_07.bin  launcher.c                               lsbrowser    lxklpia.sh
launcher         lexmark-inkjet-08-driver-1.0-1.i386.deb  lsusbdevice
root@cnapolitano-desktop:/tmp/selfgz2636/pkg/files# 

> **mionescu said:**
> I managed to install the driver on my computer. I do not have this printer so I can not really test it. I will describe next the steps I did in order to overpass the installer limitation. Again, these instructions come with no guarantee. I know it is an ugly hack but it seems it works. Lexmark should really update their installer.

Step 1.
Run the installer as you did already. When you see the error message that your version of cups does not meet CUPS requitement *DO NOT* press OK. Leave it like this for now. Otherwise the installer erases all the files we need to access in step 2.

Step 2. 
We want to find the deb file containing the driver and install it. The installer extracted the files somewhere in the /tmp folder. 
So open a terminal window (from the Utilities menu). Log in as a root  by typing the following command (otherwise I was not able to access the folder I need):
sudo su

and enter your password, if needed. Then change to the temporary folder:
cd /tmp

Now type 
ls

to see a list of folders. One of them should begin something like "selfgz#" where # is a number. In my case it was selfgz2777. Go into this directory. I typed
cd selfgz2777

Then type
cd pkg/files

to enter the folder where the deb file is. If you type 
ls

you should see a list of files and one of the should be "lexmark-inkjet-08-driver-1.0.1.i386.deb". Install it by
dpkg -i lexmark-inkjet-08-driver-1.0.1.i386.deb

Now the instalation should be complete. Close the terminal window, press OK in the Lexmark installer (this will erase all the temporary files), and try your printer. 

I hope it works.

---

### Post by cnapolitano on 2010-02-15
I tried reinstalling cups, downloading the driver and I am still getting the same error.  I did upgrade from 9.04 to 9.1 can that be the problem?


> **sgosnell said:**
> I don't know why you're having your problem.  I'm running 9.10, and I downloaded the zip file from the Lexmark site, and installed it with no problems, at least until I reached the part where it wanted to connect the printer.  I have no such printer, so I had to abort the install from there, then remove the driver.  It would appear to be a configuration problem on your system, but I don't know where to start.  You might try running Synaptic and marking CUPS for reinstallation.

---

### Post by mionescu on 2010-02-15
The error message you get is really strange. It seems that the file is there so dpkg should find it. Can you copy the deb file into your home folder? Once you are in the /pkg/files copy to file using
cp lexmark-inkjet-08-driver-1.0.1.i386.deb  /home/yourusername

and then try to install it from there by double-click on it from the file manager.

---

### Post by mionescu on 2010-02-15
I found another solution of the forum:
[http://swiss.ubuntuforums.org/showthread.php?t=1223710](http://swiss.ubuntuforums.org/showthread.php?t=1223710)

It might work for you as well.

---

### Post by cnapolitano on 2010-02-15
I will try both of these thanks

---

### Post by cnapolitano on 2010-02-15
This worked thank you so much for you help!

> **mionescu said:**
> The error message you get is really strange. It seems that the file is there so dpkg should find it. Can you copy the deb file into your home folder? Once you are in the /pkg/files copy to file using
cp lexmark-inkjet-08-driver-1.0.1.i386.deb  /home/yourusername

and then try to install it from there by double-click on it from the file manager.

---

### Post by sgosnell on 2010-02-15
I got no .deb file in my /tmp folder.  There were a lot of files from the Lexmark archive, but no .deb file.  Perhaps it was because of the immediate expansion of the .deb to the enclosed files, and I never got an error at all.

This was a strange drama, and I still don't know what the problem was.

---

### Post by cnapolitano on 2010-02-15
The problem was I could not install the Lexmark driver because it keep saying my version of cups was a lower version of 1.2

> **sgosnell said:**
> I got no .deb file in my /tmp folder.  There were a lot of files from the Lexmark archive, but no .deb file.  Perhaps it was because of the immediate expansion of the .deb to the enclosed files, and I never got an error at all.

This was a strange drama, and I still don't know what the problem was.

---

### Post by sgosnell on 2010-02-15
Sorry, to be more accurate, I still don't know what the **solution** to the problem was, or what caused it in the first place.

---

### Post by cnapolitano on 2010-02-16
To be honest I do not know what caused it either.  If I were to guess it was lexmark's drivers not detecting the current version of CUPS on my pc

> **sgosnell said:**
> Sorry, to be more accurate, I still don't know what the **solution** to the problem was, or what caused it in the first place.

---

### Post by sgosnell on 2010-02-16
Probably.  Lexmark isn't known for their Linux support, just for selling cheap printers.  A few years back I was tasked to buy ink cartridges for a Lexmark at the office at work, and found that I could buy a brand-new Lexmark cheaper than I could buy replacement ink cartridges.  I bought another printer, they're disposable.  I haven't bothered with Lexmark since.

---

