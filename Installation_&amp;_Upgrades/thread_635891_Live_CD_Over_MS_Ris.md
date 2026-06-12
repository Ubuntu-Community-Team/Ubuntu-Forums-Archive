---
title: "Live CD Over MS Ris"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Ran.leibman on 2007-12-09
Hello Everyone !

I have an MS Ris Server.
I would like to be able to boot the K/X/Ubuntu form it.
For Installations and Booting Corrupted system.

I've established kickstarting RHEL from the ris, but no luck with ubuntu

Can anyone Help?
Thanks =)

---

### Post by kingtiger01 on 2008-07-17
if you figure it out, would you make a semi-easy Walk-through/tutorial. 

Me and my organization are setting up a RIS server for Live CD Boots on Client Systems.

Basically, a few Comps. sitting in a public lab, that will be set-up to boot from the network(ris server) and will boot a live CD image from the RIS server for Web viewing and email.

So any and all info is Welcomed on my behalf also!

(not trying to hijack your thread, just similar gains i guess)

---

### Post by Ran.leibman on 2008-07-17
Hey kingtiger01

I've Succeeded to do that, but knoppix is a better choice for that..

any way this is how I've done it: (Ubuntu 7.10 I386)

Nfs Server:
cp -R -p /path/to/ubuntucd /path/to/ubuntu/cd/data

At the RIS Server:

mkdir \\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\pxelinux.cfg\
copy DISC:\casper\vmlinuz \\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\
copy DISC:\casper\initrd.gz \\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\

Sif File: \\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\Ubuntu.sif

[OSChooser]
Description = "Ubuntu"
Help = "Ubuntu Live CD"
LaunchFile = "%INSTALLPATH%\%MACHINETYPE%\templates\pxelinux.0"
ImageType = Flat


Download [ftp://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/386/netboot.tar.gz](ftp://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/386/netboot.tar.gz)
Exctract netboot.tar.gz to \\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\
copy DOWNLOADDIR:\pxelinux.0 Setup\English\Images\Ubuntu\i386\templates\
copy DOWNLOADDIR:\default Setup\English\Images\Ubuntu\i386\templates\pxelinux.cfg\

\\ris\reminst\Setup\English\Images\Ubuntu\i386\templates\pxelinux.cfg\default: 

DISPLAY ubuntu-installer/i386/boot-screens/boot.txt

F1 ubuntu-installer/i386/boot-screens/f1.txt
F2 ubuntu-installer/i386/boot-screens/f2.txt
F3 ubuntu-installer/i386/boot-screens/f3.txt
F4 ubuntu-installer/i386/boot-screens/f4.txt
F5 ubuntu-installer/i386/boot-screens/f5.txt
F6 ubuntu-installer/i386/boot-screens/f6.txt
F7 ubuntu-installer/i386/boot-screens/f7.txt
F8 ubuntu-installer/i386/boot-screens/f8.txt
F9 ubuntu-installer/i386/boot-screens/f9.txt
F0 ubuntu-installer/i386/boot-screens/f10.txt

DEFAULT LiveDesktopCD

LABEL install
	kernel ubuntu-installer/i386/linux
	append vga=normal initrd=ubuntu-installer/i386/initrd.gz -- 
LABEL LiveDesktopCD
	kernel vmlinuz
	append initrd=initrd.gz boot=casper netboot=nfs nfsroot=ipofnfsserver:/path/to/ubuntu/cd/data --
LABEL linux
	kernel ubuntu-installer/i386/linux
	append vga=normal initrd=ubuntu-installer/i386/initrd.gz -- 
LABEL cli
	kernel ubuntu-installer/i386/linux
	append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=normal initrd=ubuntu-installer/i386/initrd.gz -- 

LABEL expert
	kernel ubuntu-installer/i386/linux
	append priority=low vga=normal initrd=ubuntu-installer/i386/initrd.gz -- 
LABEL cli-expert
	kernel ubuntu-installer/i386/linux
	append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=normal initrd=ubuntu-installer/i386/initrd.gz -- 

LABEL rescue
	kernel ubuntu-installer/i386/linux
	append vga=normal initrd=ubuntu-installer/i386/initrd.gz rescue/enable=true -- 

PROMPT 1
TIMEOUT 0


Enjoy =)

---

