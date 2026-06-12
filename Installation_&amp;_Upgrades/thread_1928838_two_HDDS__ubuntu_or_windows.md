---
title: "two HDDS:  ubuntu or windows"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by SeePU on 2012-02-20
I thought this configuration would be more common by now.

I know it wouldn't be on laptops but on desktops, I thought there would be more installs of this type.

Does anyone do this?

I've dual booted always with one drive but I want to try a dual hard drive configuration with Ubuntu and Windows on separate drives.

I think there are a few ways to do this but I am wondering what the options are.

The one I know is having the BIOS be set for which drive to boot from.   So, it's a matter of installing on one (having the other unplugged?) and then install the other OS on the other drive?

I prefer a setup where I can have a menu come up giving me a choice (like the typical dual boot system on one HDD) and allowing me to choose either Linux or Windows.  I prefer the operating systems on separate drives since the dual boot system is the only real thing to worry about.   If you screw up one OS, it's not as problematic.  It's also easier to follow the drive sequence:

sda => drive 1 so any partitions are sda1, sda2 etc. etc.
sdb => drive 2 and so on....

I want one HDD with Linux on it and I'll install virtualbox but I wanted one HDD to have native Windows (Win 7).

So, if you know a good set of instructions or a link that has one or you can give detailed instructions, go ahead!

Until then, I am using google trying to find an up-to-date how-to for this.   It's grub2 so anything relevant would be pretty recent.  Maybe the only good way is to choose in the BIOS but it will take up more time and I was hoping for a different way.

There's a few things one can do with Grub so I thought there must be an alternative.  Some users say to make Windows the primary drive (use Win7 as HDD 1) while others say, it's easier if Linux is on drive #1 and then you can have Grub on that MBR (first sector etc.) and just 're-map' Windows (so it thinks it's the first drive) as 2nd drive.

Confused yet?  I am.   There must be a good way.  I wouldn't do this with a laptop but with desktops and 6 SATA ports... I think it makes sense.

I also have some data drives, one or two will be in the desktop and another two will be used as 'external' drives.  

Anyway, anyone have some ideas?

---

### Post by darkod on 2012-02-21
I'll try to keep it short, if you have a specific question, post back.

It's very simple in fact.
1. Install windows first, doesn't matter on which disk.
2. Install ubuntu on the other disk, using the manual method if you are OK with it. Under the partitions list there will be drop box to select where grub2 goes. Select it to go on the same disk as ubuntu.

Grub2 will detect the windows and create entry in the boot menu. Set in bios to boot from the ubuntu disk and you get option to boot both.

---

### Post by oldfred on 2012-02-21
I definitely agree with installing different systems on different drives.

When they say Windows first they mean sda1, and installing it first saves Windows boot loader from overwriting the grub2 boot loader.Typical one drive install.

But if you install Windows to a second drive and BIOS is set to boot from the first it may install its boot loader to the first drive. With grub (and manual install only) you can specify which drive's MBR to install the grub2 boot loader to:

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

