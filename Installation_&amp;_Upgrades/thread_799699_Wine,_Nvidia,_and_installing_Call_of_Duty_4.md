---
title: "Wine, Nvidia, and installing Call of Duty 4"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Markmiran on 2008-05-19
Hey all you fellow UBUNTU users!!  How far has this o/s come in just the last year.  The development is exciting.

I have 2 questions I really need some help with.
1. I am having nothing but problems installing COD4 through wine, one issue after another. I have finally narrowed it down to one last hurdle.  It is saying that my video card does't support enough shaders, and directx might not be installed??  I have been running the standard nvidia drivers installed by Hardy.  Do I need to run the nvidia drivers from nvidia to support directx or open gl properly and also to allow this game to work. I have a geforce 8600gt.  But everything else seems to work fine.  MInd you this is the first game I have installed with wine ... THANKFULLY.  
2. How do I install the nvidia drivers from nvidia, I used to use edgy with earlier versions of ubuntu, but now I am lost. I realise I have to run it sh >nvidiadriver.  but its not that straight forward.  Anyway any help would be great.  I have been reading all these articles with ppl being able to even run crysis, COD4 multiplayer, TF2 etc... but I can't even get past this hurdle.  it is so frustrating.

Thanks..Marky.

---

### Post by DieB on 2008-05-19
I just looked it up on the winehq.org AppDB and it seemes you need to update and patch wine.

for more check out these links:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

hope it is some how a help.


or wait till the wine 1.0 is out (actually the believe to get it done till mid of june - probably earlier)

---

### Post by Markmiran on 2008-05-20
thanks heaps I have been using git ( something new to me ) to patch wine.  have you had any experience with it??

---

### Post by DieB on 2008-05-21
Okay, well never really did it, but the following document seems to be very handy:

[http://www.perceptualmotion.co.uk/linux/cod4-wine.odt](http://www.perceptualmotion.co.uk/linux/cod4-wine.odt)

(it is also linked from the wine-link I posted)

BUT watch out in point 6, you'd need to cd into your Wine-git directory.

for that gutsy-file mentioned in point 3, there are also other versions on the webpage, so take the one according to your ubuntu version.

hope it helps

for more questions lets refer to that document, and I'll try my best to help you.

---

### Post by Markmiran on 2008-05-22
wow I can't believe your from germany... But anyway, I have tried doing step six only to get the following error:

mark@mark-laptop:~/wine-git$ patch -p1 < patch.diff
patching file dlls/wined3d/directx.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 846 (offset 172 lines).
Hunk #2 FAILED at 2044.
Hunk #3 FAILED at 2357.
Hunk #4 FAILED at 2419.
3 out of 4 hunks FAILED -- saving rejects to file dlls/wined3d/directx.c.rej

Ok this is the second time I have attempted to do this, but the hunk error has occurred both times.  Any ideas?
Thanks for your help though its been great!
Regards Marky.

---

### Post by cybercrisis on 2011-06-20
Hi There,
To get this installed properly you need to do a few things...

First install Wine 1.3 (You may need to add "experimental" to your repository & do apt-get update
Then install some stuff from nvidia:
Make sure you enable all the available repositories in your sources:

Then install these packages using the following:

apt-get install nvidia-glx-ia32
apt-get install nvidia-xconfig
apt-get install nvidia-glx-dev
apt-get install nvidia-glx
apt-get install xserver-xorg

once installed run nvidia-xconfig

Reboot

Run the installer package for COD

If you have further problems enable composting - 
in Gnome type ALT+F2 then type gconf-editor
Scroll down to apps, metacity, general & check the box next to composting... You may want to log out & back in again or reboot to enable w/o problems

This should get you going...

If you are still having probs... Follow this

type X-configure
mv ~/xorg.conf.new /etc/X11/xorg.conf
nvidia-xconfig (This will create a new xconfig file)
vi /etc/X11/xorg.conf
Add the following BEFORE the Device Section
Section "Extensions"
     Options "Composte" "enable"
EndSection

Add the following TO the Device Section
     Option "AllowGLXWithComposte" "true"
     Option "TripleBuffer" "true"
     Option "XAANoOffscreenPixmaps" "true"

Add the following to the Screen Section
     Option "AddARGBGLXVisuals" "true"
     Option "AddARGBVisuals" "true"

Reboot

You'll be good to go....

Good Luck  

This has been tested with Debian 6.0 Squeeze

---

