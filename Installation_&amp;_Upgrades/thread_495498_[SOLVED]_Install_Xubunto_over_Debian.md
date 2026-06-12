---
title: "[SOLVED] Install Xubunto over Debian"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by madzieph on 2007-07-08
First, here's little background...

**PC Specs:**
Model: IBM Aptiva e Series (2146-163)
Processor: AMD K6-2 337 Mhz
RAM: 256 MB
Video: SiS 5598 (on-board 4MB shared)
Motherboard: IBM with SiS Chipset 5598 (5597 v16)
HDD   : hda 4.2 GB 
           hdb 40 GB Maxtor Diamond Max 8
BIOS: BKLEN21A (10/20/2000)

*(a very old system I discovered in a junk shop and wants to resurrect to serve as my BitTorrent rig)*

I was trying in vain to install Ubuntu and Xubuntu for 2 days already... 

With Ubuntu Feisty Fawn 7.04 (Alternate CD), installation went only as far as Partitioning because it can't find the 40 gb hdb where I want it installed. I checked with the BIOS and it is detected. After all this has been the best bios update I can find in the net which came from IBM... I think it was also the last for that model... I even tried to make the 40 gig as primary but now I got errors that the installer cannot find CDROM and asks if I have a driver on the floppy... I already removed the floppy to give way for the 2nd HDD.

Then after some reading, I decided to try Xubuntu... still to no avail. I went only as far as those missing CDROM errors again.

I even tried replacing it with the working CDROM drive from my other desktop but the same error.

I thought of doing a net install for either of the two but I can't seem to find that option for both of them ( Or I just didn't search well enough?)

Finally, I discovered that Debian has a net install option and gave it a try... voila, it worked... but that's not the end of the story...

It seems that there's a problem with the on-board SiS 5598 video controller... it is not supported and the screen is garbled although since I have used Gnome-Ubuntu in my other desktop I can decipher which icons to click to be able to have a clean exit...

What I did was to reinstall the Debian to the bare minimum instead....

However, I still would want a GUI environment to work with hoping that the driver provided by Tom Winischoofer in his site would work with XFree86 because it didn't with Gnome Desktop.

Now, the question... is it possible to upgrade from the base debian install to xubuntu? Can I do this with "apt-get xubuntu" or any command? 

Thanks.

---

### Post by kevinlyfellow on 2007-07-08
You could install xubuntu, but I'm sure that it would be way too much of a headache.  Instead, you should just use debian with xfce.  
```
su -
aptitude install xfce4
```

Edit: You'll also want xorg or xfree86 (if people still use that) to go with it.

---

### Post by madzieph on 2007-07-08
Thanks for the quick reply... I already got xorg running...

Now since I got the display corrected, am thinking of getting a stripped down gnome... just the basic desktop.. without the add ons like multimedia, email, etc... I may one to use Firefox as web browser and run uTorrent stand-alone (within wine) if my system can still support it... Can't seem to find a good bit torrent client with the features of uTorrent in linux... any suggestions?

I tried BitTorrent and BitTornado but I can't seem to make it run as fast as uTorrent does in Windows... tried uTorrent within wine in my other desktop and it runs very well..

Thanks.

---

### Post by CREEPING DEATH on 2007-07-08
Gnome is a lot of that machine.
If you find a good BT client let me know, Azureus is not working well for me.

CD

---

### Post by madzieph on 2007-07-08
I guess I won't go into gnome anymore... even just with xfce, it's already slow...

Now how do I configure the system to run xfce at boot?

---

### Post by madzieph on 2007-07-08
> **CREEPING DEATH said:**
> Gnome is a lot of that machine.
If you find a good BT client let me know, Azureus is not working well for me.

CD

Go for uTorrent standalone... does the trick for me

---

### Post by kerry_s on 2007-07-08
> PC Specs:
Model: IBM Aptiva e Series (2146-163)
Processor: AMD K6-2 337 Mhz
RAM: 256 MB
Video: SiS 5598 (on-board 4MB shared)
Motherboard: IBM with SiS Chipset 5598 (5597 v16)
HDD : hda 4.2 GB
hdb 40 GB Maxtor Diamond Max 8
BIOS: BKLEN21A (10/20/2000)

with those specs you should go even lighter than xfce4, try fluxbox, openbox, icewm, you want the lightest you can stand.
i use debian+fluxbox on a 450mhz 256ram and this thing flies.
here's the setup i'm using

debian minimal install
apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
select fluxbox in the session menu and login
open synaptic and get what ever else i want

i use:
emelfm & mc = file manager < i like having 1 for X and 1 for without X
mousepad = text editor
links2 & iceweasel = web browsers <1 for X, 1 for without X
pidgin = mail / instant messenger


that should get you started, a little tip on links2 run it with> xlinks2 google.com

---

### Post by madzieph on 2007-07-08
Thanks for the help guys... Kerry thanks for the info about Fluxbox... it's what I needed... XFCE was dragging the system too..

---

