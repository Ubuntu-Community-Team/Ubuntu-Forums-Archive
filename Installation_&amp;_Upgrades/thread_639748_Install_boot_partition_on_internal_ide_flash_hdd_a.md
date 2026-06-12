---
title: "Install boot partition on internal ide flash hdd and rest on usb hdd"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by vincentroberge on 2007-12-13
I have a HP thin client T5720 that I use as a computer (it might seems weird, but I wanted a low power server to run a ftp and http server).  I added 1 GB of RAM in it and it has a 512MB IDE internal flash HDD.  I tried few times to install ubuntu to a 500GB external HDD.  I followed a tutorial that I found on the web at the following address

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

I was then able to use my system for a week or two and then, it would not want to boot for some reason.  Right at the beginning, my bios would not recognize my usb hdd as a bootable disk.  I do not know why.  I reformatted and again it worked for 1 week or so.  I did that for few times until I got tired.  I am wondering if I could not install the boot partition (/boot) on my internal flash HDD and the root partition (/) on my usb HDD.  So I did that, but it still does not work.  When I boot, it cannot mount root and proc and other stuff... and it stops with initramfs written on the screen.  From there, I can only have the ash command line.  Anybody can help me?  Thank you.

Vincent

---

### Post by clubsoda on 2008-01-19
Bump for an interesting approach on a low TDP, silent device.

---

### Post by donkeytime on 2008-04-04
I have this box (HP t5720 / t5725). 

/boot is on the internal flash. everything else is on /dev/sdb, my usb disk.  I used a USB CDROM for the install.  

SILENT BOX! !  No fans.  1GHz processor, 1GB RAM, 1GB Flash.  USB 2.0, Audio, 10/100 NIC, PCI Expansion slot.  I like it a lot.  Kinda looks like a PS2.

I'm running a full Ubuntu dextop and mythtv frontend on it. 

Next steps include getting the PCI expansion bay and a PCI video card with composite out so I can hook it up to a TV.

lemmie know if you're still unable to get yours to boot.  I messed with mine for a bit before it worked too.

---

### Post by donkeytime on 2008-05-30
Hey all, 

Just wanted to post an update... I've been running my HP t5720 thin client hardware for almost 2 months with Ubuntu.  I've added the PCI expansion module and an nvidia graphics card with svideo out.  The box serves as the mythtv frontend in my living room.  I'm still using the internal flash as /boot and an external USB 2.0 hard drive for the rest of the filesystem.  I'm considering moving this to a 4GB or so  USB flash card since they're so cheap.  I use a Keyspan RF Vista remote control.  

Everything works pretty smoothly except for a few glitches I've traced down to MySQL performance problems on the backend.

I'm really pleased with this hardware because it is totally silent.  The sound of CPU / Power supply / Graphics card fans pisses me off.  

I keep a digital thermometer on top the thin client case.  When I'm  watching mythtv the temperature hovers around 120F.

As for price, for a silent box this seems pretty low.  I paid $200.00 on eBay for the t5720 w/ 1GB SDRAM, 1GB Flash, ~$30.00 for the pci expansion module ~$35.00 for the graphics card and $35.00 for the remote.  The disk came from my piles of parts.

---

### Post by bboygate on 2008-07-07
hello,


is it possible to installe ubuntu 8.04 server edition on this thinclient?

could please somebody give me any documentation to make it possible?

thx allot!

---

