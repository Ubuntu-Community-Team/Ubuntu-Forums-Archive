---
title: "How do I get/install drivers for video?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by bit mad on 2009-11-25
On Windows I'm used to installing drivers - just download something and run it. How is it done in Ubuntu?

Mandriva manages 1024x768 with my video card, and with their configuration system even manages to get the refresh rate up to 70 ... but with Ubuntu I'm stuck at a flickery 60 Hz (looks awful on my trusty old CRT) and I don't know how to sort it out. (Dell Vostro 200 with Intel Graphics of some description)

My thread here [http://ubuntuforums.org/showthread.php?t=1334462](http://ubuntuforums.org/showthread.php?t=1334462) isn't getting much assistance so I thought I'd have one more cry for help :)
I'm willing to learn and experiment, I don't want it all handed on a plate, but it's got to the point where I'm too overwhelmed to make any progress.

Thanks

---

### Post by byStanderone on 2009-11-25
...have you done your backport updates? perhaps a codec or two are missing in your new ubuntu install.

---

### Post by bit mad on 2009-11-25
Wow that looks hairy! I'm trying not to apply too many updates because it's a persistant USB live key install on a 2GB key with not much space spare. All would be well if only I had the video card under control!

---

### Post by phillw on 2009-11-25
> **bit mad said:**
> Wow that looks hairy! I'm trying not to apply too many updates because it's a persistant USB live key install on a 2GB key with not much space spare. All would be well if only I had the video card under control!

The Sticky, at the start of this forum area [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)  Has a good discussion on video drivers - Go have a read. Chances are, someone else had the issue & the solution.

Regards,

Phill.

---

### Post by bit mad on 2009-11-25
Thanks, I read as much of that as I could stand, but it may as well be in Chinese :)
If someone could "dumb down" to my level, that would be great!

---

### Post by bit mad on 2009-11-25
If I recreate the Mandriva USB key I had working at 1024x768_70 yesterday, is there any way I could work out what driver it was using, save it (or the details) to my Windows disk, then reload Ubuntu USB and get the same thing running there?

---

### Post by darkod on 2009-11-25
Try EnvyNG package in ubuntu. It worked for me, automatically downloads a driver (have no clue from where), you just need to tell it whether Nvidia or ATI. Assuming you have one of them. :)
You can find it in Software Centre I think otherwise in terminal:
sudo apt-get install envyng-core envyng-qt

It shows up in Applications -> System Tools
You can run it in text mode in terminal with:
envyng -t

PS. I just checked your first post in detail, intel graphics... Not sure if it can work but you might give it a shot... :(

---

### Post by bit mad on 2009-11-25
Thanks, I looked it up and the URandR widget looks interesting, I shall look into that one.
Cheers

*update* - I figured out how to download the .deb for URandR, right clicked and used GDebi to install, ran it.... and found that it couldn't give me anything other than 800x600_60 either! :(
Garghhh!!!

btw, lspci (terminal command) gives me this, FWIW :
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

and this is hopeless too :
ubuntu@ubuntu:~$ xvidtune
Unable to query monitor info

also... although the first time I had 9.10 on persistent USB was via LiLi and that used a etc/x11/xorg.conf file, this time I'm using **USB Installer-U910.exe** from [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) and it doesn't appear to use xorg at all :)

---

### Post by bit mad on 2009-11-25
fixed ... see [http://ubuntuforums.org/showthread.php?t=1334462](http://ubuntuforums.org/showthread.php?t=1334462)

---

