---
title: "Installing ubuntu on dg965ry motherboard"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by computersolutions on 2006-10-14
I haven't seen much on installing ubuntu on the DG965ry motherboard this except for the page at

[http://www.oakcourt.dyndns.org/~andrew/wiki/index.php/DebianOnIntel965](http://www.oakcourt.dyndns.org/~andrew/wiki/index.php/DebianOnIntel965)
(which is blocked where i am in china..., so proxy it if you're in .cn land)

Here are my notes on installation - hope this will help someone.


Required items - 
One USB stick 512M or so
The offending hardware ;)
One install CD (Edgy preferably)
Existing windows or linux box with dd


Debian/Ubuntu has issues with the dg965ry motherboard  - BIOS, PATA etc.  Really needs bleeding edge kernel…  Highly recommend getting the edgy beta build for installation.

So… how to install

pata drivers not built into the kernel, only as a module, so have to  use usb drive to have cdrom contents or use a SATA cd rom.

I have a 512M USB key lying around, so…

Download dd for windows ([http://www.chrysocome.net/dd](http://www.chrysocome.net/dd))

dd if=ubuntu.iso \\.\G: bs=1M (g is my usb drive - use *your* usb drive letter, don't copy what I've written…)

wait a few minutes, and you have an iso image on the usb drive.

Put the cdrom install into the dg965ry computer.

Boot from the installer cd (remember F6,add  pci=nommconf if not edgy or it crashes)

get to the point where it asks where the cdrom drivers are.
then pop the usb key into the machine.

alt f2 in the installer

mount -t iso9660 /dev/sda1 /mnt/usb   (mount the usb as iso9660 because we cheated - it’s a hassle to make a bootable usb device imho)
cd /
ln -s /mnt/usb cdrom  (mount the usb stick as the cdrom)

alt f1 back to the installer, and continue on…

Easy when you know how ;)

Hopefully at some point the pata drivers get added to the cdrom, until then, this is the easiest way I found...

Lawrence / [www.computersolutions.cn](www.computersolutions.cn)

---

### Post by Darkwind00 on 2006-10-19
Thanks for the simpler method to get through install but I have run into an issue.  I am installing on a DG965RY board using a USB key and your instructions, but for some reason after partitioning and formating my SATA drive and setting the base username and password edgy hits a "Debootstrap Error Failed to determine the codename for the release."  Looking at the error messages I see a failed resolve for libnewt0.52 (ignored) and a couple of fall back messages to console-setup-udeb, but I cannot find and thing that indicate where to go from here.  I am using the Oct. 17, 2006 daily build for edgy and have checked the md5sum just encase.  Everything seems goot, but I cannot get past the failure at "Install the base system".

Any help would be appreciated.

Thanks in advance.

---

### Post by wahidrahman on 2006-11-09
Hi ..thanks for ur solution.
should i need to copy the whole cd into the USB?how much space the USB needed to copy.I have a USB drive of 128MB.is it possible to use that?

---

### Post by wahidrahman on 2006-11-26
hi...i have tried using 1GB flash drive to install...but after mount the usb stick as the cdrom when i switch another terminal using f1 command then there is no solution i have found.the same problem is occuring again.

---

### Post by {silver} on 2006-12-08
I just installed Ubuntu 6.10 using this motherboard. I followed the instructions to copy the iso to a usb flash drive.

However, there was no need to mount the drive manually. I turned the computer on with the Ubuntu CD in the drive and the usb hard drive with Ubuntu iso plugged in. Ubuntu automatically worked out that it needed to mount the usb drive and load drivers from it. It was almost like magic!

Now to get the graphics card working properly.

---

### Post by manuel.klimek on 2007-04-12
> **Darkwind00 said:**
> Thanks for the simpler method to get through install but I have run into an issue.  I am installing on a DG965RY board using a USB key and your instructions, but for some reason after partitioning and formating my SATA drive and setting the base username and password edgy hits a "Debootstrap Error Failed to determine the codename for the release."  Looking at the error messages I see a failed resolve for libnewt0.52 (ignored) and a couple of fall back messages to console-setup-udeb, but I cannot find and thing that indicate where to go from here.  I am using the Oct. 17, 2006 daily build for edgy and have checked the md5sum just encase.  Everything seems goot, but I cannot get past the failure at "Install the base system".

Any help would be appreciated.

Thanks in advance.

The problem is that if you mount the cd without the installer, the installer will not execute iso-scan postinst and will not set cdrom/codename etc. in the debconf database.
I solved this problem by choosing "validate cdrom" (something like this, one of the lower entries in the installer menu). Validation fails (since it is a changed image), but afterwards debconf is initialized correctly.

Hope that helps,
Manuel

---

### Post by amaramrahul on 2007-06-16
Hi,
I have a similar problem. I recently purchased the DG965RY motherboard and want to install ubuntu on it. I don't want to install the fiesty edition as I have not got very good feedback about it. Moreover I am using this as a server. So I feel the ubutnu 6.06 server edition (with 5 years support) is the best choice. And going through this thread, I feel installing ubuntu via USB is not a straight forward process.

Brooding over this further, it just struck me that as the problem is with the PATA drivers a network install should work fine. I have not yet tried it but gonna do it. In case anyone of you have tried it, please give your feedback.

Regards,
Rahul.

---

### Post by amaramrahul on 2007-06-20
I have posted a huge article on getting Ubuntu Dapper installed on DG965RY at [http://rahul.amaram.name/blog/2007/06/20/ubuntu-dapper-dg965ry](http://rahul.amaram.name/blog/2007/06/20/ubuntu-dapper-dg965ry) . This might be pretty useful.

Regards,
Rahul.

---

### Post by be4truth on 2007-06-26
I purchased the DG965ry 2 days ago and installed Feisty without any problem. Sound, graphic, DVD writer , gigabit lan - everything works out of the box.
The only thing that fails is that gparted LiveCD doesn't work anymore.
:D

---

### Post by be4truth on 2007-06-26
> **amaramrahul said:**
> I have posted a huge article on getting Ubuntu Dapper installed on DG965RY at [http://rahul.amaram.name/blog/2007/06/20/ubuntu-dapper-dg965ry](http://rahul.amaram.name/blog/2007/06/20/ubuntu-dapper-dg965ry) . This might be pretty useful.

Regards,
Rahul.

link is broken

---

### Post by amaramrahul on 2007-10-12
Sorry for the broken link ... here is the working link:

[http://rahul.amaram.name/blog/2007/06/25/ubuntu-dapper-dg965ry](http://rahul.amaram.name/blog/2007/06/25/ubuntu-dapper-dg965ry)

---

