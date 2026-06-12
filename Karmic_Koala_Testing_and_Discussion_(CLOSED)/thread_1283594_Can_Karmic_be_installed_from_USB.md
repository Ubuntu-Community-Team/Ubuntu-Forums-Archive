---
title: "Can Karmic be installed from USB?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Fzang on 2009-10-05
Normally I'd use Unetbootin on Windows to create a bootable USB, but it doesn't seem to support 9.10 yet? Has anyone tried successfully installing Karmic from USB and lived to tell the tale?

---

### Post by fela on 2009-10-05
I'm sure it can.

Whether it CAN, is a different matter.

But any Linux distro will boot off USB with enough tweaking.

---

### Post by pomalin on 2009-10-05
I create a live usb using  usb-creator from System menu, and install from this live without problems.

---

### Post by Fzang on 2009-10-05
Created live USB from Unetbootin, which works flawlessly. Unfortunately Karmic doesn't spot a 270 GB NTFS partition. Dammit.

---

### Post by miegiel on 2009-10-05
> **Fzang said:**
> Created live USB from Unetbootin, which works flawlessly. Unfortunately Karmic doesn't spot a 270 GB NTFS partition. Dammit.

Not in the partiton editor during the installation or not in the grub menu ?

---

### Post by aysiu on 2009-10-05
I used UNetBootIn to install Karmic. It works fine.

Download the Karmic .iso using BitTorrent. Then point UNetBootIn to the file, and it'll extract it to USB.

---

### Post by FuturePilot on 2009-10-05
I've used usb-creator to create a bootable USB drive and installed it from that. Works fine. Not to mention it's way faster than installing from CD. :)

---

### Post by kestal on 2009-10-06
I am currently on Karmic Beta. I installed via USB (using unetbootin). My Laptop (Dell 14z) does not have an internal cd/dvd drive and I havent bought an external yet.

It worked like a charm.

---

### Post by gmc on 2009-10-06
> **kestal said:**
> I am currently on Karmic Beta. I installed via USB (using unetbootin). My Laptop (Dell 14z) does not have an internal cd/dvd drive and I havent bought an external yet.

It worked like a charm.

So if I understand you, you have no DVD/CDROM drive on your system? This is weird, I created a unetbootin from the current 9.10 Beta ISO to install on my EEEPC 1000HE and during the install, it craps out telling me it needs to load additional drivers from CD.

G

---

### Post by aysiu on 2009-10-06
> **gmc said:**
> So if I understand you, you have no DVD/CDROM drive on your system? This is weird, I created a unetbootin from the current 9.10 Beta ISO to install on my EEEPC 1000HE and during the install, it craps out telling me it needs to load additional drivers from CD.

G
I have no CD/DVD-ROM on my HP Mini netbook and was able to load Karmic on via USB.

Which drivers does it complain about?

---

### Post by gmc on 2009-10-06
> **aysiu said:**
> I have no CD/DVD-ROM on my HP Mini netbook and was able to load Karmic on via USB.

Which drivers does it complain about?

It's looking for CD-ROM modules.

G

Updated: I checked ALT-F4 using the above and noticed that there's and error message about failure to load the i82365 module. Maybe that's the problem

Updated(2): After playing around with options, I found that if I use the "command line install" (not default or install options), I can do a netinstall with the DVD image. Which is a bit silly considering everything that's downloaded is supposedly already on/in the ISO image.

---

### Post by DominicF on 2009-10-06
Hi,

I too have had problems with unetbootin and Karmic but I think it is hardward related.  The karmic image on my usb stick works with most PC's but doesn't doesn't like my Acer Revo Nettop and fails to boot saying media not bootable or words to that affect (I tested with other distros and those worked e.g ubuntu 9.04).  

I then tried to create a USB bootable image from another of my Ubuntu desktop machines.  With this method I am able to boot Karmic from USB on the Revo but later fails to load the desktop and remain at a commandline.  Running the command startx doesn't help... (I don't remember the messages that appear on screen).  I tried this with the last few Alpha's and now the Beta without successfully starting up the Desktop screen.

---

### Post by jperez on 2009-10-06
I dunno...I just used a PC to install Ubuntu straight onto a SD Card with no usb booting software or anything.  Just did a straight, normal install like I would do on any computer, only directly on a USB device.  If you have a PC, do that.  It boots perfectly and can be used in any computer that boots USB devices.  I've tested it out on three different PC's (desktop and 2 laptops) and it worked.

Just my experience.

Jesse~

---

### Post by gmc on 2009-10-06
I tried creating mine on both a 4GB USB drive and a 8GB flashcard (Sandisk brand) using a Windows machine at work and my Jaunty system at home, same results for both. I then thought maybe it's a problem with the card reader build into the 1000HE and tried using a cheap multiport external card reader plugged into the USB port, but that didn't work either.

Choosing the "Command line Install" option and plugging the 1000HE directly into my router did allow me to do a network install. On the ubuntu irc forum, someone pointed me to [http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/) where I found CD ISO's for both the Live and Alternate 9.10 ISO images.

Ultimately, I ended up re-downloading the 9.10 Beta Live ISO and re-re-re-installed using that.

Hope this information helps anyone else having similar problems...

G

---

### Post by MacUntu on 2009-10-06
The usb-creator seems to work fine: just installed Jaunty and Karmic from a SD card put in an USB card reader (the system can't boot from the internal card reader). :D

---

### Post by kimda on 2009-10-06
I've installed Karmic via usb on three systems now and works fine. Only I had to use the alternate image instead of the live cd image (alpha 6). With the live cd image the installation would fail unfortunately (maybe it works now with the beta image). I created the usb disk via usb startup disk creator in Ubuntu.

---

### Post by tom56 on 2009-10-06
> **DominicF said:**
> Hi,

I too have had problems with unetbootin and Karmic but I think it is hardward related.  The karmic image on my usb stick works with most PC's but doesn't doesn't like my Acer Revo Nettop and fails to boot saying media not bootable or words to that affect (I tested with other distros and those worked e.g ubuntu 9.04).  

I then tried to create a USB bootable image from another of my Ubuntu desktop machines.  With this method I am able to boot Karmic from USB on the Revo but later fails to load the desktop and remain at a commandline.  Running the command startx doesn't help... (I don't remember the messages that appear on screen).  I tried this with the last few Alpha's and now the Beta without successfully starting up the Desktop screen.

I'm running Karmic on a Revo which I installed using a usb stick made in unetbootin on Windows. Not had any of those problems.

---

