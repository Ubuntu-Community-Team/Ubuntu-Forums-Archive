---
title: "Edgy Eft Live CD Won't Finish Booting"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by kweiner on 2006-11-09
I tried to use the Edgy Eft 6.10 Live CD on my new Dell Dimension 9200c.   I can make it to the Ubuntu splash screen, but then after a few seconds, Ubuntu stops loading and I am presented with a text screen with the words BusyBox v1.1.3 at the top and the following message and prompt:

/bin/sh: can't access tty; job control turned off
(initramfs)

What should I do to troubleshoot why my Live CD won't load?  I would really like to get this working as I am so anxious to replace Windows with Ubuntu.

---

### Post by gazj on 2006-11-09
There are two possible ways i might go with this.

1. Download the Edgy alternative install cd, this will not start live, and is a text based installer, don't let that out you off, it is as easy as pie.  Hopefully after the installation it will start up properly.

2. Go back to ubuntu dapper 6.06, this was the last release in the last release cycle, (if that makes any sense) so it is much more stable.  Edgy is the first release in a new cycle so uses all bleeding edge technology that is not as proven.


Personally i think i would go for the 2nd option for stability and reliablility.

Hope this helps

Thanks

---

### Post by kweiner on 2006-11-10
Thanks for your tips. I took your advice and tried both option 1 and 2.  Neither were successful.

Option 1: I got the Edgy Eft alternate install CD and the install process could not get passed the "Detect and mount CD-ROM" step.  It asked if I wanted to load CD-ROM drivers from a floppy, but I do not have a floppy drive.  It then asked if I wanted to manually choose a CD-ROM driver, but I had no idea which one to choose.  I had no choice but to abort the installation.  I should note that I do have a Dell Dimension Resource CD that came with my computer that might have the right CD-ROM driver on it, but I don't know how to access it during installation.

Option 2: I got the Dapper Drake 6.06 Live install CD.  It almost finished, but then failed with a text message that read: "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"  I am not experienced enough with setting up X to know what to do or what to look for.

Do you have any other suggestions for what I should try next or how I can troubleshoot one of the options above?

---

### Post by unisol on 2006-11-10
try safe video-mode and install in text-mode

---

### Post by eeried on 2006-11-10
Are you sure your cmputer is compatible with Ubuntu or Linux? You could try the Live-CD of a different distro.

---

### Post by gazj on 2006-11-11
Ok, the X server graphical problem as you may have guessed is a graphical problem.

There is a file called xorg.conf which has all settings to do with the graphical enviroment in it.

you can edit this without the graphical mode working

first press ctrl+alt+f1

you should get to a login screen, login

then enter this followed by enter

```
sudo nano /etc/X11/xorg.conf
```

this will open a simple editor to edit the file

when you have made any changes press ctrl+x to exit

it will ask you to save changes press y

then try starting the xserver with the following command

```
startx
```


What exactly you need to change in the file is really mostly down to what graphics card you have,  if you know try searching the forums for the graphic card to find if anyone else has the same problem.


I can really only give advice on nvidia cards as this is all i have

Hope this is of some help

---

### Post by kweiner on 2006-11-11
> **eeried said:**
> Are you sure your cmputer is compatible with Ubuntu or Linux? You could try the Live-CD of a different distro.

I am not 100% sure if my computer is Ubuntu compatible.  I use Ubuntu at work and really want to stick with it at home too, so I'm reluctant to switch to another distro right now.  I think it should be possible to get it working because the Dapper install recognizes my CD-ROM, but not my NIC while Edgy fails to recognize my CD-ROM but according to some other posts I've read, it recognizes my NIC.  So somewhere in Ubuntu are the right drivers for both my CD-ROM and NIC.  If I could only figure out how to fix one or the other.

---

### Post by kweiner on 2006-11-11
> **unisol said:**
> try safe video-mode and install in text-mode

Thanks for the suggestion.  Safe graphics mode worked for me in Dapper, although Dapper fails to recognize my NIC.  Without access to the network, there isn't much I can do, so I really hope I can figure out how to fix it.

---

