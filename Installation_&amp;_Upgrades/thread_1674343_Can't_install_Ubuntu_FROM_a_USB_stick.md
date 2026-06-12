---
title: "Can't install Ubuntu FROM a USB stick"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2011-01-23
Can you shed some light on this?

I have tried to use an Ubuntu .iso image on a USB stick to install Ubuntu onto a hard disk but I get errors during the installation process.  The image on the USB stick was created by using the USB Startup Creator with a file downloaded from "get Ubuntu" and checked with its md5sum.  The USB stick works fine as a Live CD when I choose the "try it out" option but when I choose the "install" option then it gets part way through the process and gives some procedure error followed by a numerical error.  Retries continue to produce errors.

What is really strange is that when I use the identical .iso file burned onto a CDROM the installation works perfectly.

I need to figure this one out because some of my target systems do not have CDROM drives.

This problem occurs with Ubuntu versions 9.04, 9.10, 10.04, and 10.10.

Any ideas?  Thanks.

quadproc

---

### Post by oldfred on 2011-01-24
Depending on what version you used, there were some bugs.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)


Since flash drives became larger & lower in cost, I did not want to have just one ISO per flash drive so I installed grub and loopmount as many as the flash drive will hold. That way I have several versions, and repair ISOs all on one flash drive.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by quadproc on 2011-01-24
> **oldfred said:**
> Depending on what version you used, there were some bugs.

Thanks for your reply but I think that I did not describe my problem well enough so here is another try at description:

I am able to make USB sticks that boot OK.  They bring up the selection screen which asks if I want to try out the version, or if I want to install it.  When I select "try" then things work fine although rather slowly, as expected.  When I select "install" then the system starts the installation process but soon reports an error in one of the routines such as 'get time zone' or 'partition the disk'.  Retrying the operation does not succeed, and the failure causes the entire installation to fail to proceed.

When I place the same .iso file on a CDROM and ask it to install then installation works fine, no errors, and the installation runs fine when I boot from the installation.

I am wondering if the system is somehow trying to write something to the USB stick and is not being allowed to do that for some unknown reason.


(URLs to interesting techniques omitted)

Thanks for the URLs.  Those are useful information and I will note it for possible future use.  I plan to get some more USB sticks tomorrow so I might try the techniques soon.

quadproc

---

### Post by garvinrick4 on 2011-01-24
You have tried using the Burned Cd to make the USB stick instead of .iso

---

### Post by quadproc on 2011-01-24
> **garvinrick4 said:**
> You have tried using the Burned Cd to make the USB stick instead of .iso
Not sure what you are saying, so here is more detail on what I did:

I download versions of Ubuntu to my system data disk and keep each version in its own directory, so each directory has a single .iso file in it.

I use Brasero to place the desired version onto a CDROM.

I use Startup Disk Creator to place the same version on a freshly partitioned USB stick.

Then when I try to do a system install from the USB stick, I get the problems mentioned previously but when I use the CDROM which contains the identical version, everything works fine.

I hope that helps to clarify.

quadproc

---

