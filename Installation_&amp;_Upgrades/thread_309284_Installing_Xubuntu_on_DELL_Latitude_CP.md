---
title: "Installing Xubuntu on DELL Latitude CP"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by skaughtEE on 2006-11-29
I am attempting to install Xubuntu on an old Dell Latitude CP laptop that I have.  It is a 233Mhz with 128MB of RAM and a 4GB hard drive.  It is currently running Windows NT 4 and I would like to use it to get into Linux. 

I have downloaded the various ISO files for Xubuntu and have not been able to install the system yet.  I put the CD into the CD-ROM drive, power up the machine and I get the main start up screen giving me various options.  When I select to start and install it spins the CD ROM and then it just spins and spins and spins.

I believe that it is having troubles recognizing the CD-ROM drive, but I'm not quite sure.

If anyone has installed Xubuntu on this laptop before and had success, perhaps you could pass along your wisdom.

Thanks, and take care.

..scoTT

---

### Post by Sigudian on 2006-11-29
I think this has more to do with the ram, rather than the CD-rom

since your choice it to boot up live to later install it within the live boot, your computer needs a lot of ram to do this, this is the most negative thing about the newer releases of Ubuntu. on older machines you cant install it with a newer CD, because you have to boot it to the heavy to run Live Boot.

I recommend you try to get an older release that does not have live boot on the main install disc, then install it, then upgrade though the update manager.

---

### Post by skaughtEE on 2006-11-29
Is there a particular version that you recommend?  And am I able to find these on the Xubuntu download page?

---

### Post by Sigudian on 2006-11-29
I just saw that Xubuntu was first released after this thing with the live CD happened, but i think you can install it without going trough the live boot if you use [this iso]("http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso"), youl find the [torrent file here]("http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso.torrent") 

these links are the alternate install cd, from the [official download page]("http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/")

---

### Post by K.Mandla on 2006-11-29
Hmm. :-k I've put 6.06.1, 6.10 and some earlier versions on CP-series laptops, and haven't run into problems like that.

A couple of things come to mind. First of all, if you're committed to installing, go with the [alternate (installation) CD]("ftp://mirror.d-jacobs.com/ubuntu/edgy/ubuntu-6.10-alternate-i386.iso"), not the live CD. Those CP machines are a bit lightweight for the live environment. (Perhaps you've tried that already. ... ;) )

If you find it hanging again, try pressing CTRL+ALT+F2 or F3 or F4 or ... to see if you can find the installation log. One of those keys should give you a screen that tells you what Ubuntu is thinking and why it's jammed up.

You could also try starting with a command-line installation, and see if that helps at all. Once you have your system in place, you can install Xubuntu with *sudo aptitude install xubuntu-desktop*. 

Don't forget there are some boot options at the splash screen that might come in handy. If it's crapping out over a video display mode or something like that, you can modify those at the initial menu.

---

### Post by skaughtEE on 2006-11-29
I have been attempting to use the alternate installation CD.  I am, though, using the Xubuntu.  Does it make any difference between the Ubuntu and the Xubuntu?  Being my first attempt at this I wasn't sure which one to pick.

I have taken your advice and after pressing CTRL-ALT-F4 I am looking at a screen of information and it is repeating the following over and over again...

Nov 29 13:xx:xx kernal: [171nnnnn.4nnnnn] ide-cd: cmd 0x28 timed out
Nov 29 13:xx:xx kernal: [171nnnnn.4nnnnn] hdc: DMA interrupt recovery
Nov 29 13:xx:xx kernal: [171nnnnn.4nnnnn] hdc: lost interrupt

and the CD just keeps on spinning.

All of this after putting the alternate CD into the CD-ROM, turning on the laptop, having the Xubuntu start up screen appear, selecting the install a command-line system, seeing a Trying to enable the frame buffer message, selecting English as the language, selecting Canada as the location, selecting the U.S. English as the keyboard and then watching it detecting the hardware to find the CD-ROM...

---

### Post by skaughtEE on 2006-11-29
I have run the process again and just before it starts to loop i see the following:

hw-detect: Missing modules 'ide-core (Linux IDE support), ide-mod (Linux IDE driver), ide-probe-mod (Linux IDE probe driver), ide-detect (Linux IDE detection)

it then has another line saying

cdrom-detect: Searching for Ubuntu installation media

and then it enters into the looping scenario

---

### Post by skaughtEE on 2006-11-29
I did a quick search on the cmd 0x28 timed out error and found a post that seems to have resolved the issue.

After following these instructions the installation is proceeding and seems to be quite happy.

-------------
What worked for me (alternate CD):
- proceed with install until the keyboard selection dialog
- select your keyboard if not American English but DO NOT proceed to next step (hardware detection)
- disable DMA support: Alt-F2, Enter, hdparm -d0 /dev/hdc
- proceed with install: Alt-F1, Enter

The install might be slower because DMA is off, but any attempt to re-enable it freezes the install.

Note: you might want to add the line 'hdparm -d0 /dev/hdc' to your /etc/rc.local once the system is installed.
---------------

Thanks for everyone's help on this.

..scoTT

---

### Post by K.Mandla on 2006-11-29
Excellent. Let us know how it goes. :)

---

### Post by skaughtEE on 2006-11-30
Well... it was going fine.  The core applications all seemed to install, but when it came time to install the other various pieces of software I think that I had some MD5 checksum issues.  It would get to 6% and then the CD would just start to spin again.  Perhaps I can try installing with another burn of the ISO... or perhaps it is best to get an actual version from Ubuntu...  I'm so close though.

---

### Post by fvbakel on 2007-11-11
Hi,

Just for information for all those old Dell latitude owners out there. On my Dell Latitude Cpi-A series the workaround mentioned here did not work. However it did work when I disabled the dma at the boot parameters. 

The boot parameters I used where:

ide=nodma 
acpi=force

Hope others can share the experience of x-ubuntu on the old dell laptops with this tip.

---

