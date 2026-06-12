---
title: "Boot Disk Installation"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by davidwashere2003 on 2005-03-15
I have an old computer that I'm trying to put Ubuntu on.
It's got a 100MHz CPU, 3GB HDD, 64MB EDO RAM, 12x CDROM.

Will these specs work for Ubuntu?

It does not support booting from the CDROM at all, because the BIOS sucks.

I have a DOS boot disk that can initiate the CDROM for DOS.

Is there any way that I can run the install on the Ubuntu CD after I've booted into DOS? 

Is there a boot disk image for Ubuntu I can put to diskettes using DiskWrite?

Or should I just leave this comp as an ISA card and EDO RAM testing machine?

------------------

Just an update...
I have FreeBSD boot disks (didn't get the actual program downloaded yet) that bring me into a prompt of sorts. There's a number of commands. Can any of the commands from FreeBSD be used to initiate the installation of Ubuntu?

Thanks in advance.

---

### Post by az on 2005-03-15
You are on the right track.

Try this:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)


Gidde up!

I would use something like icewm and xfe (file manager).  Abiword instead of openoffice.org.  Sounds like a top-of-the line machine for the time!  (64 megs of ram is tremendous for a 100MHz machine.  More is better, though)

---

### Post by davidwashere2003 on 2005-03-16
Right on, thanks for the lead.

Just sorted through about 300 sticks of EDO and managed to come out with 4x32MB DIMMs -128MB EDO is a nice little upgrade. 
Switched the 100 for a wopping 166MHz CPU... she's screaming now!
I'm still trying to get this going for a diskette boot. 
Maybe if I update the Award BIOS it'd be able to boot CDs.

I'm working on setting up a little more powerful Ubuntu system at the moment... 
Got a 450MHz PII on an Asus P2B-L out of the shop "untested" pile... seems to be working fine, only 64MB SDRAM though and I'm running it on top of my desk without a case to put it in. This board supports CD boot. 

The Ubuntu is loading right now.
Can't wait to see it... if it ever loads.

Thanks again for the lead.

----
Just a quick update... ran into problems with the 450 machine... some trouble with my RAM... had to upgrade to 128MB SDRAM. Ubuntu seems to be struggling though. Keeps crashing durring the load. Haven't picked out precisely where it's failing yet.

Got a boot disk made using the steps from your link.
Just like to mention that there's alot to pick from for image writing programs.

Rawrite did the trick.

DiskWrite won't work on the sbootmgr.dsk file.

Will attempt boot via floppy tomorrow.

----
Another update.
Troubles booting Ubuntu from CD on PII450... kept crashing about the point where it loads GUI.
Thought maybe a problem with bad RAM, switched 128MB SDRAM for 64MB and got errors about there not being enough RAM. Arrrg.
Noticed Ubuntu was crashing with interrupt errors on an unlisted device.
Replaced S3 Trio 32 video card with an ATI Mach64 VT and put in a second stick of 64MB (128 total).

Booting into Ubuntu GUI via CD now without a hdd in the comp yet. 
Loading the GUI fine, but there's trouble getting my serial mouse to pick up.
Will try a PS/2 mouse.

Is there a way to navigate through the GUI using the keyboard?

Haven't attempted diskette boot yet on older machine, it's in use testing cards right now.

---

### Post by packardbio on 2005-03-24
I just got Ubuntu Hoary 5.04 preview going on an old low memory Dell PC I brought out of retirement with the following specs:

Pentium 133
48M EDO RAM
HDD#1 = 1.6G
HDD#2 = 8.0G
4xCD-ROM drive (TEAC)
Number Nine Motion 771 PCI video card w/2M VRAM

I can't boot off of the CD ROM on this system even though the option is available in the BIOS setup. So I created a boot floppy with Smart Boot Manager on it (SBM). Booted from the floppy and chose CD-ROM from the menu, then let the CD-ROM install take it from there. 

Works great! I even got X working using XFCE as the desktop/window mgr. I basically follow the miniRAM HOWTO with a few changes (since it's really geared towards Warty 4.10:

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)
 
For Hoary:

a) Use "server" at the boot prompt instead of "custom" (there isn't a "custom" option in Hoary for some reason)
b) installed x-windows and xfce as described here: [http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

I had to tweak the X configuration by hand to get it to work on my video card and monitor, but I have to say it works pretty good for an old beater. XFCE is "not too slow" on this system. I had Fedora Core 1 installed previously and GNOME was WAY too slow on it. XFCE is actually usable - if I don't try to do too much at once.

Good Luck!

---

### Post by MemoryDump on 2005-06-29
[QUOTE=azz]You are on the right track.

Try this:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)


Gidde up!

I would use something like icewm and xfe (file manager).  Abiword instead of openoffice.org.  Sounds like a top-of-the line machine for the time!  (64 megs of ram is tremendous for a 100MHz machine.  More is better, though)[/QUOTE]

wow.. what a great util/image! This just saved my @$$!! Damn I love the SEARCH button.. search is your friend.. that and beer 

-MD :p

---

