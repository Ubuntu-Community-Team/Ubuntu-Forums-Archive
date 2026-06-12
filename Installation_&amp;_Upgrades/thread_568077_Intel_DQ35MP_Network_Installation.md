---
title: "Intel DQ35MP Network Installation"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by lonrot on 2007-10-05
Ubuntu x64 7.04

Hello, I've found the drivers here:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng)

But I don't know how to install them, please give me advice.

Thank you.

---

### Post by Pumalite on 2007-10-05
Try the Alternate CD. How do you get your broadband?

---

### Post by lonrot on 2007-10-05
> **Pumalite said:**
> Try the Alternate CD. How do you get your broadband?

But I found the driver, how can I install it?

---

### Post by Pumalite on 2007-10-05
Where you found the driver, there must be instructions. Make sure it's for Linux. How does it come packed?

---

### Post by lonrot on 2007-10-07
Hello, the package comes as:
.tar.gz

And the instructions are quite clear, but, I'm not very familiar with linux, and for me this is harder than a quantic formula. I would like to see this instructions for Ubuntu starters and not for Linux pros.

Here I quote the intructions:
> Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename
of the driver.

NOTE: For the build to work properly, the currently running kernel MUST
      match the version and configuration of the installed kernel sources.
      If you have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions.  For more
   information, see the ldistrib.txt file included in the driver tar.

5. Load the module using either the insmod or modprobe command:

     modprobe e1000

     insmod e1000

   Note that for 2.6 kernels the insmod command can be used if the full
   path to the driver module is specified.  For example:

     insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.ko

   With 2.6 based kernels also make sure that older e1000 drivers are 
   removed from the kernel, before loading the new module:

     rmmod e1000; modprobe e1000


6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>

7. Verify that the interface works.  Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the
   interface that is being tested:

     ping  <IP_address>	

---

### Post by Pumalite on 2007-10-07
Excellent instructions, but RPM's are not used in Ubuntu.

---

### Post by Pumalite on 2007-10-07
[http://ubuntuforums.org/showthread.php?t=569706](http://ubuntuforums.org/showthread.php?t=569706)

---

### Post by lonrot on 2007-10-07
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=569706](http://ubuntuforums.org/showthread.php?t=569706)

Damn, it's so hard to install software and learn how to do it without internet connection, I have to switch everytime I read your replies, okay I'll get back to ubuntu now and see if I can make it with the info you gave me, thanks!

---

### Post by lonrot on 2007-10-07
1) Pumalite, I downloaded the build-essential_11.1_amd64.deb , it asked me for the ubuntu cd, and it downloaded 5 of 6 files so the installation was a failure, any suggestions?

2) My Ubuntu version is 7.04 x64, (I wrongly stated x86 before) could that driver still work under 64bit architecture?

---

### Post by Pumalite on 2007-10-07
Why do you say that the installation of build-essential was a failure?
Post the output of:
sudo apt-get install build-essential

---

### Post by lonrot on 2007-10-07
Where can I download the full package?

---

### Post by lonrot on 2007-10-07
```
apt-get install essential-build
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
lonrot@lonrot-desktop:~$
```

---

### Post by lonrot on 2007-10-08
My bad, forgot the sudo part.

---

### Post by lonrot on 2007-10-08
```
lonrot@lonrot-desktop:~$ sudo apt-get install essential-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package essential-build
lonrot@lonrot-desktop:~$ sudo apt-get install essential-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package essential-build
```

---

### Post by Pumalite on 2007-10-08
Typo: not 'essential-build'

sudo apt-get install build-essential

---

### Post by lonrot on 2007-10-08
> **Pumalite said:**
> Typo: not 'essential-build'

sudo apt-get install build-essential

```
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_amd64.deb MD5Sum mismatch
```

---

### Post by Pumalite on 2007-10-08
I'm stumped. Somebody will chime in

---

