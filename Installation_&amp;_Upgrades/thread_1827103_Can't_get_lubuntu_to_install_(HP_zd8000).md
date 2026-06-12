---
title: "Can't get lubuntu to install (HP zd8000)"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by Z0Tex on 2011-08-17
Hello. I have an HP zd8000 laptop that was given to me from my father. I decided to make this my first linux machine. The laptop needed a new hard drive so I bought a new Western Digital 80GB drive and installed it. I asked a few of my friends which version of Linux would be a good choice for it and they pointed me in the direction of Lubuntu since I wanted to conserve some resources but still have a fully functioning laptop. The hardware specs are Pentium 4 3.2E cpu, 512 MB RAM, ATI mobility x300 64MB graphics, new (fresh out of the box) Western Digital 80GB HDD.

I downloaded the 32 bit .iso from [HERE]("http://phillw.net/lubuntu-11.04.iso") and used the Universal USB Installer 1.8.6.1 to create a bootable USB drive on an 8GB USB drive. I can get the laptop to boot from the drive and select English as the install language. When I start the install, I can see the Lubuntu loading screen with the logo and 5 "loading dots". After about 4 minutes of that, I get a quickly scrolling wall of text that looks like commands. When the text stops, there are a series of messages that indicate that there are no such files or directories.

For example:
chroot: can't execute "mktemp": No such file or directory
cp: can't stat "/root/var/cache/debconf/config.dat": No such file or directory
<some output omitted>
grep: /root/usr/share/i18n/SUPPORTED: No such file or directory
/scripts/casper-bottom/14locales: line65: can't create /root/etc/default/locale: non existant directory
etc...

It acts as though it has no place to install anything. The HDD is brand new, fresh out of the box. I can't even use the Run Lubuntu before installing option as it also fails with similar output as above.

A few days prior to this, my roommate gave me a USB drive he created with the same USB Installer that have Puppy on it. It ran as a live USB. We used to to test other components of the laoptop to make sure they were working. Everything but the wireless system worked. Apparantly Puppy has issues with Broadcom wireless sets. Note: when running Puppy from the live USB, the laptop had no HDD installed at all.

I also tried using the disk checker that is at the install Lubuntu screen and it also failed with very similar output as above^. The memory checker that is also included hangs up as soon as it is started. The hard drive checker in the BIOS works fine and passes with flying colors.

Does anyone have any suggestions or ideas as to what my problem(s) may be? If you need more information to help you solve my problem, let me know and I can post it up. Thanks in advance!

---

### Post by Z0Tex on 2011-08-17
Well, I never could figure out the usb drive issue. I finally just burned the .iso to a cd and ran it from there. lubuntu installed quickly without any issues at all from the cd. My laptop is up and running now. Thanks!

---

