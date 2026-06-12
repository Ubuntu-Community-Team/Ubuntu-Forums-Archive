---
title: "Problem when installing with Dell monitor"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Uriptical on 2006-06-02
Hi, I am trying to set up Dapper Drake on my PC. The specs are as follows:

AMD Athlon XP 2600
1.5 GB of RAM
Seagate 300 GB SATA
ATI Radeon 9700
Dell UltraSharp 2405FPW Widescreen LCD

When installing, however, I get the following error:

[FONT="Courier New"]1. D-SUB
Can not display this mode.
[/FONT]

This a message from the monitor itself. D-SUB is the first of five different inputs that the monitor uses. I would try DVI, but I don't have the correct cable.

The error happens after the first screen (where you can choose to actually install Ubuntu by pressing 1) after several of the packages have loaded.

---

### Post by w_croft on 2006-06-06
Having the same problems but with a Polyview V398 19" LCD Widescreen monitor though I am getting an Out Of Range message.

First time I had the problem was when I bought the monitor because I was running Breezy Badger and the resolution it was running at wasn't supported by the monitor. Back then I was able to fix it because I still had the old monitor lying around, now I don't.

Second time I had the problem with a VGA Box that I use to try to watch the TV/Videos/DVD's/XBox through on the monitor and turns out that the VGA Box only outputs PAL signals at 50Hz and the monitor only supported 60Hz to 75Hz. Nothing I can do here except replace the old box which I will do with one that supports LCD screens but also Widescreen display.

Now I come to this, as per for Uriptical, right after selecting the run/install option there are a few things and then I get the Out Of Range error, which pretty much makes it impossible for me to install Dapper Drake. I'm guessing that the installation is running at a resolution that my monitor doesn't support rather than a frequency?

So does anyone have any ideas that might help us get Dapper Drake installed???? I'm itching to give it a go after having seen it in action at a convention.

---

### Post by xpeeblix on 2006-06-12
Same problem here.  I'm using an Acer ET.L5209.005 19" Widescreen Monitor and have the exact same problem.

The part I really hate is hearing the Ubuntu welcome sound, but not being able to see the desktop.

Is there a solution to this?  It sure would be nice to see Ubuntu's shiny face.

---

### Post by taurus on 2006-06-12
Maybe you need to look in /etc/X11/xorg.conf and make sure both horizontal and vertical refreshing rates are correct for your widescreen monitor!!! 
```

sudo nano /etc/X11/xorg.conf

```
Otherwise, run X configure again to generate a new /etc/X11/xorg.conf
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by xpeeblix on 2006-06-12
Forgive me, for I am a true neophyte in the world of linux.  Where do I type in the code you gave me?  In the installer somewhere?  Sorry, totally lost.

Don't give up on me, I'd really like to see Ubuntu working here.

---

### Post by taurus on 2006-06-12
If you hear the drums but can't see a thing, then you have X running but the display somehow is all messed up.  Then, hold down <Ctrl><Atl>F1 and log in with your username and password.  At the prompt, type in those commands...

---

### Post by xpeeblix on 2006-06-12
Ok, ran the x config thing again and muddled through best I could (auto detect didn't work).

How do I get back the gui?  StartX tells me that it's already running.

Thanks!

---

### Post by confused57 on 2006-06-12
You could try   Ctrl+Alt+F7

or

sudo /etc/init.d/gdm start

---

### Post by golanhall on 2006-06-12
I was having some problems myself with my ati radeon x700 card on my amd64 live cd.
After trying a lot of things posted on these forums I was about to give up.

Until I did this:
sudo nano /etc/X11/xorg.conf
go to the line that says: driver and change "ati" to "radeon"
press ctrl+x and save
Start X with "startx" followed with an enter.

Did the trick for me :D

---

