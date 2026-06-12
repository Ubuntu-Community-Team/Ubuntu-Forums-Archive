---
title: "Ubuntu 8.0.4 install fails on Toshiba laptop: cd-rom mount fails"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by martinpg on 2008-08-12
Hi, I wonder if anyone can help with an installation problem. I am installing Ubuntu 8.0.4 onto an old Toshiba laptop Satellite Pro. Here's what happens:

1. Boot up with CD in drive
2. Select English and hit Enter
3. Install Ubuntu Server selected: hit Enter
4. Loading Linux Kernel progress bar
5. Choose language: select English and hit Enter
6. Choose country: select United States and hit Enter
7. Detect Keyboard layout: select No and hit Enter
8. Origin of keyboard: select USA and hit Enter
9. Keyboard layout: select USA and hit Enter
10. Detecting hardware to find CD-ROM drives is displayed with progress bar
11. No common CD-ROM drive was detected: Load CD-ROM drivers from floppy? select NO and hit Enter
12. No common CD-ROM drive was detected: Manually select a CD-ROM module and device? select YES and hit Enter
13. Module needed for accessing the CD-ROM: I have tried selecting both none and cdrom:
(a) If I select none, then I get prompted to specify a device (dev/something), but I do not know what might work (as prompted I switched to a console, and ran ls /dev but nothing in this list seems to work)
(b) If I select cdrom, then I get prompted to provide a driver, but I don't have a driver to provide.

I have also tried other installs such as Fedora 9 and Gentoo and they also seem to fail at this step.

It's frustrating that the initial boot succeeds in finding the CD-ROM drive, but then the installation process then loses sight of the drive!

Thanks for any help, Martin

---

### Post by Partyboi2 on 2008-08-12
At the main menu press F6 to add a boot option and try using
```
all_generic_ide
``` (add it to the end of the line)
Another option if you are not able to get past this, is to use something like [[COLOR=Blue]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html"), which does not require the use of the cdrom

---

### Post by martinpg on 2008-08-12
Wow - that was quick! As suggested I hit F6 and edited it so that the boot line reads:

/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz quiet -- all_generic_ide (all on one line)

However, I basically exactly the same screens. Is there something I can look at to see whether or not the CD-ROM drive is being found and if so as what device?

Thanks for your help, Martin

---

### Post by wpshooter on 2008-08-12
Have you tried to update the firmware of your CD-Rom drive to the latest version ?

---

### Post by martinpg on 2008-08-13
I am amazed at the responsiveness of this forum and thanks for offering advice. Forgive the naive question, but how do I update the firmware of the CD-ROM drive - that is, does it need me to have an OS installed first in order to do this?

I am pretty sure that the drive in question is a TEAC CD-224E, but I cannot track down any firmware for this drive (at least that isn't Windows-specific). Is there a good place to look for firmware?

Finally, and this may be relevant, this is actually the second CD-ROM drive I have tried - I had the same problems with the drive that came with the laptop (a Toshiba XM-1502B drive). Might there be some other reason why Ubuntu is not recognizing the drive?

Thanks, Martin

---

### Post by martinpg on 2008-08-13
Hi, in order to install Linux on the laptop, I tried the suggested approach of unetbootin as follows:

1. I booted the laptop using a Knoppix 5.1.1 live CD.
2. I downloaded unetbootin-linux-248 to the /ramdisk/home/knoppix directory.
3. chmodded the file to be executable.
4. I then ran ./unetbootin-linux-248

Unfortunately, I see an error immediately:
./unetbootin-linux-248: /lib/tls/libc.so.6: version 'GLIBC_2.4' not found (required by unetbootin-linux-248)

Does any one know what to do? Again, it's frustrating that the Knoppix seems to be able to run off the CD drive - it seems to be a problem with the installation routines that the Cd-ROm drive is inaccessible.

Thanks for any help, Martin

---

### Post by Partyboi2 on 2008-08-14
Does the laptop currently have an operating system install?

---

### Post by martinpg on 2008-08-14
Hi, the laptop originally had Windows 2000 installed, and more recently it has been running Fedora 4. However, in doing an upgrade of Fedora 4, I managed to corrupt the installation in such a way that I am no longer able to boot in as root (or any other user). After spending a day or two trying to rescue this installation, I though that I might just as well install a new version of Linux, Ubuntu, to get a feel for it. In short, I don't currently have installed a usable OS on the laptop.

Here is a brief summary of what I have tried:
(a) Installing Ubuntu 8, Fedora 9, and Gentoo from CD - all fail at the same point of the installation process when trying to access the CD after the initial installation screens (see above);
(b) Swapping out the original CD drive (Toshiba XM-1502B) and trying again with a different CD drive (TEAC CD-244E);
(c) Booting using Knoppix (5.1.1) and then running unetbootin (see above).
(d) Booting using Debian's floopy boot disk: this boots to the first screen, but fails shortly after when I hit enter at the first prompt.

I have done a fair amount of googling and searching forums too, and at this stage, I am little frustrated at this laptop! Thanks for any help, Martin

---

### Post by hyper_ch on 2008-08-14
here you find many ways to install it:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

I'm sure one of them works for you :)

---

### Post by martinpg on 2008-08-20
Thanks - in the end, I managed to get Debian Sarge installed via a Knoppix Live CD. It wasn't pretty, but at least I am up and running! Martin

---

### Post by Memorito on 2008-10-11
I am having pretty much the same problem.  This is an old system that does not support usb install.  It recognizes it enough to load the install cd but not enough to finish?  I don't get it.

---

