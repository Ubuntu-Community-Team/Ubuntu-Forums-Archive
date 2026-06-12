---
title: "Blank screen/nVidia woes when installing Ubuntu 7.10"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by stefansmith on 2008-03-09
Hi all,
After a successful, painless install of Ubuntu on my Toshiba laptop, I went ahead and installed on my AMD Sempron 3200+ desktop, for which I just bought a new graphics card (an Asus EN7200GS - nVidia). Previously I had installed Ubuntu Studio 7.04 on the desktop using the built-in graphics (GeForce 6150), which worked OK.

Everything on the install of the (verified) alternate 32 bit install CD went fine, but on the final reboot, I got the loading bar, then a blank screen. I had chosen 1440x900 has the resolution during the install, so suspected this was too high to start with. So I reinstalled again, using the onboard graphics, and chose 800x600. Still, a blank screen on reboot.
Then I did some searching here, booted into recovery mode, and did:

sudo dpkg-reconfigure xserver-xorg

and selected standard VGA driver, low resolution, and:

startx

which got me to a low res login screen; logged in, downloaded the restricted drivers; but still seem to be stuck with low res 800x600, that uses only 80% of the width of my new widescreen LCD, and can see now ay of changing it. Also, this works on d-sub on onboard graphics, not DVI. On the graphics card, neither DVI or D-Sub work.

It also annoys me that installing the Windows XP boot partition was painless.

I was tempted to just try openSUSE.... but no, I'm sticking with Ubuntu, and will start from scratch again tonight, and just wanted to know if there is a recommended way of tackling this properly from the start? Surely there is a way of doing it without going to the command line just to get a low res OS?

thanks in advance for the help.

---

### Post by Peter09 on 2008-03-09
The best way to get your Nvidia card running is to install a package called ENVY.

Go here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and follow the instructions to install ENVY. When it asks you - select Nvidia and it will do the rest.

PC

---

### Post by stefansmith on 2008-03-11
Envy did the trick, but not sure how it worked.

I installed Envy, rebooted, and it was fine.

I now get the nvidia boot screen and the resolution I want.

Then I went to activating desktop effects, it said I had to activate restricted drivers, (not envy, I presume), which I did, and it is still working and I get the nice effects, snappy too.

One odd thing though, when I do a sudo gedit for xorg.conf, the file is blank/empty..... :confused:

---

### Post by Charles2008 on 2008-03-11
I followed instructions above yet I still get a black screen.  I have a NVIDIA GEForce 7300 GT card and a new Samsung syncmaster932bw lcd monitor.  Ever since installing the monitor using DVI nothing is working.  I just get a blank screen.  Ubuntu worked on my old monitor fine.  Does dvi not work with ubuntu 7.1?

---

### Post by Charles2008 on 2008-03-11
Also, I tried before envy to manually change xorg.file and that didnt work either.  I couldnt install driver from NVIDIA's website because it said i was in wrong graphics level.  I am currently in low graphics level.


Thanks

---

