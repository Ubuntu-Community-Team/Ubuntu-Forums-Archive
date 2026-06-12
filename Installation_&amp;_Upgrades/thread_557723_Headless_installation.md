---
title: "Headless installation"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by nickj6282 on 2007-09-23
Hello all,

I have a need to install a Ubuntu server on a headless PC (no monitor/keyboard) and I need to know what my options are. I've thought of several ways to do it and I'm wondering which will work and what my best course is.

Hypothetical method 1:
**Remote install using SSH or VNC.** If there's a way to get the Ubuntu install CD to start this way, that would be great. I can download the ISO and edit it a bit before burning, or just find a way to set the default install CD to work this way.

Hypothetical method 2:[B]
Put the HDD into a USB enclosure and use my Ubuntu-powered laptop to make the installation, then transplant the HDD to it's final destination.[/B][ Something like this.]("http://ubuntuforums.org/showthread.php?t=107421") The problem I see with this is in the hardware. Specifically the network interfaces. If I do this and my laptop has a broadcom ethernet card, while the destination PC has a D-Link (for example), will it then recognize the new ethernet card as eth1 or eth2 or something instead, therefore making my network configuration invalid? Also, how would I get the boot loader installed correctly so that the system boots into the new Ubuntu install once the HDD is transplanted?

Hypothetical method 3:
**Install and configure to a virtual machine, then transplant the image to a HDD**. I've got VMWare or MS Virtual PC available to me for this purpose, but the same hardware/boot worries as above apply. Also, I'm not sure how I'd transfer the VMDK/VHD file to the hard drive so that it works.

Hypothetical method 4:
**Unattended installation.** Is there a way to set up the Ubuntu CD to just run and install everything the way I want it without *any* human intervention? The PC I'm installing to does have a floppy drive and a second CDROM drive in it.

Thanks for any and all ideas!
-Nick

---

### Post by theangryamoeba on 2007-09-25
I have set up more headless servers than I would like to admit. While you could do it in a vm and copy the image over, its a pain in the butt.  
First, unless the machine you are running the virtual machine is pretty powerful, its going to take  longer than installing natively. I've run into problems where my server never comes up after tranfering the info to the drive and putting it into the server. Usually something like a kernel panic that you can't see without having a monitor attached. Sometimes you also have to make sure that the computer will boot without having a keyboard attached.

By far the easiest method I've found for setting up a headless system is to put a graphics card into the computer temporarily. I have a pci graphics card I got out of a computer I got for $5 at a garage sale.  I keep it in my toolbox just incase :).  It won't do any graphics acceleration but it will do terminal output.

---

### Post by nickj6282 on 2007-09-27
Well the machine has a video card. The problem I have is that I don't have a monitor to connect to it right now. My wife and I both use laptops, and my old HDTV doesn't have a VGA input. That's why I need to headless install.

My laptop is quite fast for doing a VM install, and install speed isn't important to me at all. Is it at all possible to set up a "portable" Ubuntu install on a 2gb USB drive and boot from that? That way I can boot it up in my laptop and set up VNC/SSH to start at boot, then boot the other machine (I know the boot order is set to 1. floppy, 2. cdrom, 3. usb-zip, 4. hdd) and remote in to configure it.

---

### Post by motin on 2008-01-23
To be practical I would recommend you to borrow a monitor for a day and make the installation. 

Nevertheless, I am interested in how one would perform a headless install. I have an older computer with a broken VGA out and got no extra PCI graphics card lying around and would like to attempt it if there was a clear guide. Nice experience to put in the box if it works out smoothly. 

How did you end up doing?

Cheers,

Fredrik

---

### Post by darkpixel on 2008-03-04
> **motin said:**
> Nevertheless, I am interested in how one would perform a headless install.

The way I wish it would work would be for the installer CD to automatically request an address from DHCP, fire up SSHD and then let you use the installer SSH component...

It would make it extremely easy to provision headless boxes.  It would also be very easy for hosting providers to slip the CD in, and tell the customer what their IP address is.  Then the customer can setup the box how they want it from remote.

For people worried about security, you could maybe do something like toss your public key in as a DHCP parameter or something and only allow login via trusted key...

---

