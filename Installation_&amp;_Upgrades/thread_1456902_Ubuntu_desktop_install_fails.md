---
title: "Ubuntu desktop install fails"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by mjobrien on 2010-04-17
Hi all,

I have been trying for many hours to install Ubuntu 9.10, on a system that already had 9.10 installed on it at one point (so I know it should work!)  I am using an alternate install, from a USB thumb drive.  I use the alternate so I can encrypt the hd.  Everything goes smoothly until I am to select extra packages to be installed.  The only package I select is the ubuntu-desktop, and around 80% progress, or so, it fails.  I then try and complete the base install, and then login to the command prompt and install there:

sudo apt-get install ubuntu-desktop

It then requests the Ubuntu disc, which of course I don't have.  It has a landline internet connection.  Do I need to configure something to tell it to look to the mirrors to find the desktop?  Or, should it have been included in my iso image originally?  Any ideas would be very helpful!

Thanks so much!

---

### Post by mjobrien on 2010-04-18
So, in case anybody else has had this problem, or problems in general installing Ubuntu Alternate via USB, I found something that worked (for me).  So, I tried for many hours to make my USB stick bootable through another Ubuntu system, and also through Windows, and had great difficulty in both (trying to use Unetbootin, as well as Universal-USB-Installer).  I had mentioned that I had gotten it to work before, so I went back to the machine that successfully created the bootable USB stick.  And it worked.  So, in conclusion, I was able to create a good, bootable and installable USB version of Ubuntu 9.10 (the alternate .iso) by creating the USB stick on Red Hat, using Unetbootin.  For some reason, this same procedure failed on both Ubuntu and Windows.  Hope this helps others.

Cheers!

---

