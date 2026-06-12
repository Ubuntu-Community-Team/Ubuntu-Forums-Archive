---
title: "No CD XUbuntu Install"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by DrDave on 2006-11-30
Hi Folks,
Hope someone can help me.

I've got an old laptop (portege 3110CDT) with no CD rom drive (got a floppy though). It's  a PII with 128 MB memory and a 6GB HDD, ideal for XUbuntu (I think).

There's no option in the bios to boot from external devices which is a shame as I have a USB CD burner.

What I want to know is if I can install XUbuntu using my external USB drive and some sort of boot floppy (plus a dummys guide to setting it all up).

Thanks in advance,
Dave.
:confused:

---

### Post by louieb on 2006-11-30
Maybe.  try [Smart boot manager]("http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk") link is to the floppy image download.
I guess you are using Windows so you will need [RawWriteWin]("http://www.chrysocome.net/rawwrite") to copy the SBM floppy image to a floppy.
After you make the floppy and boot with it You will just have to see if it pickups up your USB CD Drive.
Let me know.
This is what I use on older computers  that will not boot to an internal CD Rom drive.

---

### Post by zzsimonb on 2006-12-03
Ah, I have exactly the same problem on exactly the same equipment! I have about a dozen of these 3110 toshiba's and would love to get ubuntu on them.

I have succeeded in getting Debian on, but Ubuntu is being really hard to get along with.

Get a copy of the debian diskette installer, this is 2 diskette images 'root' and 'boot'.

Boot from 'boot' and insert root when you are asked.

The installer will configure the ethernet on the 3110 back pack, and you can do an over the internet install, only trick bit is to set the monitor up for 800 x 600 @60hz

Life is good, this works every time!

To get ubuntu on the technique should be:
Use root and boot and as soon as you have run the disk partioner bale out by using alt+F2

At this point you should be able to d/l debootstrap.

run debootstrap for the flavour of ubuntu that you want and it will magically install.

Well thats the theory anyway. In practice i get a very consistant crash and burn with debootstrap. 

if you look on the ubuntu site there is documentation explaining the exact process. I beleive its in user docs "install using diskettes".

If you do crack this problem, please let me know. And if you want to collaberate on it again let me know [email]zzsimonb@gmail.com[/email]

Simon

---

### Post by phuturism on 2007-01-22
Hi guys,

Another option to consider - although I wish I had seen the debian floppy install option four days ago!

I had the exact same issue with a Portege 3480CT with  a USB cdrom drive but of course this could not be booted from due to bios limitations.  If you have internet access and another machine to use as a server I would recommend a netboot install.  Check in bios if it has a LAN boot option

My story - after a weekend of pain trying to boot from a dos floppy with usb cdrom drivers on it and modified config.sys and autoexec.bat files I gave up on this and did a netboot install from a windows XP machine on the network - fortunately the portege has a PXE (net install) option in the bios.

Theoretically you can do the same thing from an Ubuntu machine with dhcp3/tftp servers  configured correctly but as I am only two weeks into my linux experience i found it much easier to do this from a win xp machine  on the LAN.  Pretty good instructions are available at this thread [http://www.ubuntuforums.org/showthread.php?t=327597&highlight=netboot+windows](http://www.ubuntuforums.org/showthread.php?t=327597&highlight=netboot+windows)

You will see my comments and modifications at the bottom of the thread - let me know if you want to try this option and I will be happy to help.

The netboot option is also great as you can do a number of machines very easily - the install process also gives you the option to install the Xubuntu desktop instead of Ubuntu which helps if you want to run a lean and clean desktop for older machines like my 3480CT.

Good luck!

---

### Post by phuturism on 2007-01-22
Dp

---

### Post by tassoman on 2007-03-13
What about guys with only SCSI CD roms PCI controlled and any USB port?

---

### Post by sledge737 on 2007-03-22
> **DrDave said:**
> Hi Folks,
Hope someone can help me.

I've got an old laptop (portege 3110CDT) with no CD rom drive (got a floppy though). It's  a PII with 128 MB memory and a 6GB HDD, ideal for XUbuntu (I think).

There's no option in the bios to boot from external devices which is a shame as I have a USB CD burner.

What I want to know is if I can install XUbuntu using my external USB drive and some sort of boot floppy (plus a dummys guide to setting it all up).

Thanks in advance,
Dave.
:confused:

My best suggestion is that you will rig a PXE boot server (Network boot) with the OS of your choice. Had the same problem with a defect CDROM on an IBM laptop and set up a pxe boot machine and installed it from there. Plenty of HOWTO's on PXE boot server setup.

Sledge737

---

### Post by TexasRed1974 on 2008-07-12
I was in the same boat with a Toshiba Portege 3480CT.  BIOS doesn't allow boot to USB or PCMCIA, so no CD options for me.  I attempted to use the SmartBoot, but could never get it to see either USB or PCMCIA, and was about to give up when I stumbled across the Netboot option.  

I'm a Linux Noob, but a seasoned Microsoft admin.  So setting up the TFTP/DHCP server on the windows machine was easy, and once I booted the 3480CT over the LAN, the installer took over. I had a very nice installation of Xubuntu running on the laptop in about 45 minutes.  Very slick!

The laptop is a PIII-600 with 192MB of RAM, using a Xircom CWE1100 (airo_cs driver) PCMCIA wireless card.  Came with Win98, and not quite snappy enough to run XP very well.  I was using 2000 for a while, but grew tired of everything 'almost' working.  So I figured I'd give Ubuntu a try.  people were saying that Xubuntu was a good lightweight distribution of linux, and the Netboot gave me the option to install it.

Performance-wise, it is snappier than XP, but not as responsive as 2000.  I guess it was not as quick as I was hoping, but people do say that it should have 256 at the low end.  So, all in all...not bad.

Thanks to everyone who shed the light on the Netboot option, and thanks to the Ubuntu crowd in general for making it work so smoothly.

Carry On.

---

