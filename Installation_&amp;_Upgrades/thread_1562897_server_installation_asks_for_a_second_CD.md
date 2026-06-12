---
title: "server installation asks for a second CD"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by raxxal on 2010-08-28
I just download the serve CD, but at some point, the installation ask for a second CD, how do I get the rest of the CDs?  I think they  are 4. Is there any link available where I can download the DVD?

---

### Post by ptn107 on 2010-08-28
There is one server CD.

Ubuntu 10.04.1 LTS Server 32-bit: [_download_]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-server-i386.iso") or Ubuntu 10.04.1 LTS Server 64-bit: [_download_]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-server-amd64.iso")

---

### Post by MikesterH on 2010-08-28
I'm experiencing the same problem. I am installing the 32 bit 10.04.1 Server. However it is not actually prompting to insert a second disc - it's prompting for the disc thats actually already in the drive....

It keeps prompting me with:
[B]insert the disc labeled 'Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)'
[/B]
On the distro cd in there are two files which contain the text:
[B]Ubuntu-Server 10.04.1 LTS "Lucid Lynx" - Release i386 (20100816.2)
[/B]
These files are:
 /README.diskdefines
and
/.disk/info

I believe the error is caused by the _Lucid Lynx_ vs "Lucid Lynx" mismatch between the two.  I'm going to try editing these files, and reburning the disc with the modified files to see if that works - I will post the results.

---

### Post by MikesterH on 2010-08-29
Nope. Didnt Work. 

I extracted the contents of the .iso download to a 'extracted' folder on my desktop, and then modified and saved the two offending files. Then I used Nero to burn all of the files in my 'extracted' folder to a new CD. I realized that doing it this way would make my new CD unbootable... I was hoping to continue where I left off in the install, but that didn't pan out either - it still wouldn't recognize this as being the correct CD.

I'll look elsewhere. I was hoping for a quick, easy install. Not going to beat my head against a wall over this.

---

### Post by Sef on 2010-08-29
Did you check the disk to make sure that it is good?

---

### Post by MikesterH on 2010-08-29
> **Sef said:**
> Did you check the disk to make sure that it is good?
Yes.

---

### Post by MikesterH on 2010-08-29
:popcorn:

I did not get any error messages while installing the Ubuntu Server - it just got stuck in an endless "insert disc" loop at some point after installing the base system and setting up the first user account. However, while trying to install several other distros, I kept getting "block-device" error messages while alt+f3 and alt+f4'ing through the installs...I swapped out the cdrom drive with another - and now it appears that the Ubuntu Server install is going fine.

---

### Post by alfmarius on 2010-08-30
I can confirm this error. I tried to burn this cd 4-5 times (with 2 different lucid iso's) but all give this mistake. I also "burned" the iso onto a usb, but then the distro complains about not finding a cd in the cdrom.

mighty annoying this as i need to install a linux server yesterday and want to have ubuntu...

---

### Post by alfmarius on 2010-08-31
well, i'll be.... i changed the cdrom drive, and now it worked also for me. darn hardware..

---

### Post by keteP on 2010-09-11
Changed the cdrom cable from slave to master connector. This helped.

---

### Post by veggos on 2011-02-27
Hi,
I also noticed the use of underscores (_Lucid Lynx_) in the installation print out and thought that I could edit the iso image and replace the double quotes with underscores in the two files you mention above. I followed some of the instructions on this web page regarding installation CD customization.
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

I followed the instructions until and including "Copy the CD to your hard drive". Then changed double quotes to underscores, saved the files and humped to the last step of the guide: "Burning the CD, Building the ISO image, x86 and AMD64". This step makes sure that a bootable CD is created.
I inserted into the machine and started the installation process all over again. This time the installation proceeded without a hitch.
One detail though, instead of 'mkisofs' i used 'genisoimage' with the same command line switches. genisoimage was suggested by apt-get.

I had another problem not related to the disc issue but relating to  software raid. I started the server installation because I wanted to get a software RAID1 (mirroring) setup with my two identical and old 80GB drives. In one of the the last steps that the installation process asks for GRUB to be installed. I noticed that GRUB is installed in the both devices files (/dev/sda and /dev/sdb) corresponding to my two hard drives.  That would the desirable behavior for identical mirrored hard drives.  That also means that the master boot record in written in the _beginning_ of both the hard drives which in normal cases is fine. Nevertheless if one goes through the official help for software raid on Ubuntu 10.04 ([https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)), the instructions suggest that the swap file is positioned in the beginning!!!
The result was that I kept on getting some errors and a "grub rescue>" prompt and didn't know what to do.

I rebooted the machine, tried the rescue method of installation and tried to reinstall GRUB (after several steps you get the option) but I was getting fatal errors on the reinstallation! Anyway I followed the wise suggestion by this thread:
[https://lists.ubuntu.com/archives/ubuntu-server/2011-January/004950.html](https://lists.ubuntu.com/archives/ubuntu-server/2011-January/004950.html)
This thread suggest that one should have three RAID1 devices, one for boot, one for swap and one for "/" in this order. I followed this principle when setting up the partitions (I had to go through all the steps again, sigh) and now my RAID1 works like a charm.

---

