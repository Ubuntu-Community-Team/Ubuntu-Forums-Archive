---
title: "install ubuntu with loadlin"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by cristianommxp on 2005-05-27
Hi,

I have this PC:

- Pentium 100
- RAM 40MB
- HD 4GB
- CD-ROM Creative Quad Speed

Well, this PC doesn't boot by CD. The CD-ROM is an Creative and it's plugged on Sound Blaster ISA CARD.

So, the only form to install CD-DRIVE is using DOS drivers. I do this with some commands int AUTOEXE.BAT and CONFIG.SYS. 

Well, I can install CD-ROM just using MS-DOS. I install as "E:"

So, I have to use "loadlin.exe" to start Ubuntu Install CD. But I don't know how to do this.

What's the loadlin.exe command line to start Ubuntu CD Installation program directly from CD-ROM?


10ks,


Cristiano M. Magalhaes

---

### Post by kye on 2005-05-28
download and install the program from this site onto a floppy disk, it will look for a cd if you have one and give you and option to boot from it.


[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

---

### Post by cristianommxp on 2005-05-30
"Smart BootManager" doesn't support my CD-ROM driver.

I know "Smart BootManager". So, the only solution now is to install Linux by Loadlin.exe.

The question I post is abou "Loadlin.exe", just it.

Do you know how to install Linux Ubuntu with "Loadlin.exe"?

10ks.

Cristiano M. Magalhaes

---

### Post by savage on 2005-07-24
I am in a similar situation, and have been searching high and low for a solution. I have an old laptop without a cdrom or network device. I've found boot disk(s) that will allow me access to a USB cdrom. Starting the installation from dos sure would be helpful. Otherwise I'm guessing that I will have to remove the hard disk, partition it and use some of the guides or posts for installing linux from the hard disk.

These links were helpful for getting access to the USB cdrom drive under dos.

[http://www.stefan2000.com/darkehorse/PC/DOS/Drivers/USB/](http://www.stefan2000.com/darkehorse/PC/DOS/Drivers/USB/)
[http://www.theinquirer.net/?article=10215](http://www.theinquirer.net/?article=10215)

---

### Post by larsw on 2007-01-05
Hi all, 

stumbled over this rather old thread having the same problem, and just wanted to post my solution to use a USB DOS boot floppy disk to install Ubuntu on a Fujitsu Stylistic 3400 without internal CD-Rom and a Bios by no means supporting booting off a USB or PCMCIA drive. Smart Boot Manager does not do any good in that situation. So here is my very quick and dirty howto. Hope it helps someone. Will post it on other sites to maximize chances people discover.

NB: Why does Ubuntu not just ship with nicely usable floppy images for the same purpose? Anyhow, not doing so made me learn some things - call it a great day then :rolleyes: 

Regards
Lars

-------8<-------------8<------
Stylistic 3400 Ubuntu Install via FreeDos Boot Floppy with USB CD Support and external USB-DVD

Aim:
Install Ubuntu 6 on a Stylistic 3400 which can not boot from external USB or PCMCIA CD-ROM without going through the pain of a hdd/knoppix/dsl/foreign host installation.

The Stylistic is not the sole target of this method, but rather any outdated (er, better: older) hardware not supporting booting external devices should be designed to work with this method.


(I) Requirements

(I.i) Hardware

(a) A working external floppy drive (legacy system connector, not a USB floppy!) for the Stylistic 3400

(b) A working USB-DVD drive (or a CD-Drive if you have an installation CD, I had a DVD from c't magazine 25/2006)

(c) The Stylistic 3400 with an internal hard disk (or any other older PC hardware suffering the symptoms mentioned above)

(d) A working 1.44MB floppy disk. Be prepared to need more than one as these things are always damaged.

(e) A working PC to download some software (about a meg or two only) from the web


(I.ii) Software

(0) WinImage or another software that can write an .imz file to a floppy under your OS on the PC you will be using to prepare the boot floppy

(1) A "FreeDos" based boot floppy image 
(I used this: [http://www.fdos.org/bootdisks/autogen/FDSTD.144.imz](http://www.fdos.org/bootdisks/autogen/FDSTD.144.imz))

(2) DOS USB ASPI Drivers for CD-Roms from Panasonic 
(here: [http://panasonic.co.jp/pcc/products/drive/other/driver/f2h_usb.exe](http://panasonic.co.jp/pcc/products/drive/other/driver/f2h_usb.exe))

(3) DOS USB Storage/CD Driver from
(here: [http://www.driver.novac.co.jp/driver/hd351u/mhairudos.zip](http://www.driver.novac.co.jp/driver/hd351u/mhairudos.zip))

(4) Linld, a dos based linux loader
(here:[http://port.imtp.ilyichevsk.odessa.ua/linux/linld/linld.com](http://port.imtp.ilyichevsk.odessa.ua/linux/linld/linld.com))
Reason for not using "Loadlin": Loadlin even in version 1.6c had problems loading the large vmlinuz image of the ubuntu disk (loadlin error message "ran out of input data")
Linld.com can do it!

(5) The Ubuntu Install CD / DVD.



(II) Preparing the Boot Floppy

(a) use Winimage or the tool of your choice to write the fdd image from (1) to your lovely floppy disk

(b) extract the self-extracting archive f2h_usb.exe from (2)

(c) copy the files \f2h\usbaspi.sys and \f2h\usbcd.sys from the freshly created f2h subfolder to your floppy (root folder)

(d) extract the zip archive from (3)

(e) from the created unzip folder mhairudos, copy only the file di1000dd.sys to your floppy (root folder)

(f) edit the config.sys file on your floppy to look like
-------8<------ 
DOS=HIGH,UMB
DEVICE=FDOS\HIMEM.EXE
lastdrive=Z
rem The following line loads Panasonic's universal USB- controller driver
rem the /v switch makes it verbose
rem the /w switch makes it wait for you to connect your USB-CD-Rom and press enter
devicehigh=USBASPI.SYS /v /w
rem the following is an aspi mass storage driver for usb- connected HDs 
rem and compactflash memory cards
devicehigh=DI1000DD.SYS
rem The following one loads CD-ROM driver
devicehigh=USBCD.SYS /d:USBCD001
------->8------

(g) edit the autoexec.bat file on your floppy to look like
-------8<------ 
@ECHO OFF
CLS
ECHO Welcome to FreeDOS ([http://www.freedos.org)](http://www.freedos.org))!
LH \FDOS\SHSUCDX.EXE /d:USBCD001
------->8------

(h) done, your floppy is ready to be used. Should work on nearly any hardware and support not only external CD-Roms but also DVDs, HDDs, maybe even sticks!?!? 
What a great tool..... Wish we had had that 10 years ago!


(III) Booting the ubuntu installer

(a) connect the external FDD and CD drives to the Stylistic 3400

(b) insert the Ubuntu DVD (CD) and FDD

(c) boot the system off the floppy disk. It will ask you to connect your CD drive. Make sure it is spun up before pressing enter, otherwise it might not get detected. 
Note: If you are using a bus-powered drive, make sure you use both USB-Plugs on the Stylistic (the docking station port and the unit's own port) or an additional power supply unit for the USB CD drive. Mine regularly dropped out during the later package copy operations when using it with the USB data cable connected only (though on a different Laptop the same drive even burns CDs with power only provided through the data cable and the additional power-to-usb-cable unplugged) - assume this is because the USB 1.1 ports on the 3400 docking station do not provide enough amps for the DVD to work in heavy load situations.

(d) once the floppy boot is complete, type in the following commands to start the linux installation:
-------8<------{Space}
c:
cd install
a:\linld image=vmlinuz initrd=initrd.gz cl=root=/dev/ram
------->8------{Space}

(Note: C: is assumed the drive letter assigned to your external CD-ROM. If your hdd on the stylistic holds dos-recognized partitions, it might be d: or e: etc here. Look for the output of SHSUCDX.exe, it will tell you what letter has been assigned)

(e) there you go. Ubuntu installer will load

(f) after the language and keyboard settings have been made, the installer will look for the CD drive. It won't find the USB drive, so we have to tell it: 
- When asked whether you want to load cd drivers from a floppy, say no. 
- Next, you are asked to select manually from a list. Do so, and select "cdrom". 
- Next, it will ask you to specify the cd device. type in 
-------8<------ 
/dev/scd0
------->8------
and confirm with enter. This will give you access to the CD drive.

(g) From here on, piece of cake. Follow the installer and fill in whatever you need to do


TADA!
You just installed Ubuntu with a FREEDOS BASED USB BOOT FLOPPY. Incredible!

---

### Post by ilandson on 2007-07-23
I have been using the steps listed to load Ubuntu's ver 7.0 but I get a kernel panic error when i launch linld.
her is what I did.

c:
cd isolinux 
a:\linld image=bzlinuz initrd=initrdfs.gz cl=root=/dev/ram


I get the following error 

Kernel Panic: no init found. Trying to pass init= option to kernel

any Ideas

---

### Post by 0graham0 on 2007-08-11
This worked for me, using a Xubuntu 7.04 alternative install cd:

linld image=d:\install\vmlinuz initrd=d:\install\initrd.gz "cl=root=/dev/ram boot=install ramdisk_size=1048576 devfs=mount,dall"

If you are using a different cd just check the directory where vmlinuz and initrd are stored

---

### Post by Helygog on 2007-11-13
Thank you Lars for such a useful set of information.  I have successfully used your method to get Xubuntu 7.10 loaded on an old IBM Thinkpad 240 (no CD-ROM drive but an external bootable floppy drive).  I was able to use a USB CD drive and install with onlt two slight changes.

1.  Following your instructions to the letter I forgot to copy linld.com to the floppy!  D'oh!

2.  After some trial and error I used the following command to start the load from CD:

linld image=d:\install\vmlinuz initrd=d:\install\initrd.gz

I used the Xubuntu Alternate image CD fro i386.

Thanks again.  I had almost given up and was going to throw the laptop away!

John

---

### Post by 1956moonraker on 2008-04-14
Thank you all, esp. Lars, John & Graham for really useful stuff. My problem: trying to get Ubuntu 7.04 installed on a Compaq Evo N1015 laptop whose DVD/CD station is u/s. Followed above instructions/hints, and found a few new things: I got linld097.com from troglabit.com/files/linld, and found vmlinuz and initrd.gz on the Ubuntu 7.04 distribution CD under /casper. Also I copied linld097 to the floppy root, as John mentioned.
Armed with all this, I succeeded in getting through as far as starting up linld, with the external CD station showing up as c: - so far so good. But after a bit of chewing the cud, linld stalled with the message: "crc error -- System halted".
Suspecting that linld does a ramdisk check, I experimented a bit with the ramdisk_size parameter, as suggested above, but no joy. Anyway, how can I find out what my ramdisk size is from the DOS prompt? Am I even on the right track, or is there some other problem here?
Any suggestions?
Robin

---

### Post by lloeki on 2008-06-02
excellent! this worked for me to install hardy heron xubuntu alternate on an old machine with win95 rev A, so no usb, floppy drive dead, can't boot from CD and no bios netboot! insane...

I then set up samba on another machine, copy linld097.com from there and exit to msdos. unfortunately only the cd root is readable, all subdirs appearing empty, so can't reach kernel files! back into win95, copy vmlinuz and initrd.gz to c:, give that to linld and marvel at the kernel booting.

in the end for a PII 266 64Mb of ram it runs so much better than win95 and can do all the latest stuff so much more securely.

that's another win for linux ;)

---

### Post by Dirty Ol' Man on 2008-06-23
Greetin's,

I'm trying to install Ubuntu on an old laptop with no internal CD-ROM drive, and no BIOS support for USB boot.  Have tried following all of the recommendations in this thread to the letter, several other methods described here and there on the web, and numerous variations on all.  One major problem I had, which I haven't seen mentioned anywhere by anyone else, is that when I used MSCDEX, I could only access the root directory of the USB CD-ROM; trying to access files and subdirectories resulted in "File Not Found" errors.  I discovered, by trial and error, that using SHSUCDX solves that problem.

I'm still not able to run linld without it crashing, however.  Regardless of command line parameters, the system hard-locks, after a few seconds of CD-ROM access, and the only way to recover is to recycle power.  If I specify a VGA mode in the parameters, the video mode changes first, before hard-lock.  I've tried Hardy
desktop as well as alternate, with same results.  For confirmation I also tried an older Gutsy desktop CD-ROM which I have used to install Ubuntu on other PCs (the normal way) at least twice in the past.  Same result.

Any ideas or suggestions would be much appreciated.

                   Thanks,
                   Dirty Ol' Man

---

### Post by Dirty Ol' Man on 2008-06-23
PS:  I noticed some have mentioned linld.EXE.  The only linld I could find is linld.COM.  I wonder if that might make a difference.
Can anybody tell me where to find linld.EXE?

                           Thanks,
                           Dirty

---

### Post by Dirty Ol' Man on 2008-06-24
> **lloeki said:**
> unfortunately only the cd root is readable, all subdirs appearing empty, so can't reach kernel files! back into win95, copy vmlinuz and initrd.gz to c:, give that to linld and marvel at the kernel booting.


Oops!  I guess I didn't read your post carefully enough the first time.  I wrote yesterday that I was unable to read beyond the root, but hadn't seen any similar reports by anyone else.  Anyway, as I mentioned then, I found that by using SHSUCDX, instead of MSCDEX, I could recurse all subdirs and access all files (from DOS prompt), but linld crashed anyway.

Since I can now access the entire CD directory structure, I'll try copying it to the HD, and point linld to that, as you did.
Any other ideas welcome.

---

### Post by Dirty Ol' Man on 2008-06-24
> **Dirty Ol' Man said:**
> Since I can now access the entire CD directory structure, I'll try copying it to the HD, and point linld to that, as you did.

Ok, that didn't work either.  Linld still crashes.  Guess there's not much point trying a different CD drive.  I'm running out of ideas.  Any suggestions whatsoever welcome.

Dirty

---

### Post by themischiev on 2008-06-26
STYLISTIC 3400 HARDDRIVE IMAGE FOR DOWNLOAD?

I wonder if any of you have an image of the Fujitsu Stylistic 3400 hard drive that I could download, what happens is that I was trying to install an operating system in the unit but with no success.

---

