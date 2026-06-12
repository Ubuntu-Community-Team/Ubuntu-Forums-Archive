---
title: "Installer graphic issues"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by jarrett on 2007-06-06
Hi,
I have been trying to install 7.04 onto my laptop a few times now. I have tried Ubuntu 7.04, Kubuntu 7.04 and the Ubuntu alternative cd.
On the live cds graphics messes up, and I can't see a whole lot. Running in 800x600 and really messed up, 5 instances of the same screen is spread around the screen
And when I used the alternative iso, it threw an unhandled exception at around 85% when installing some python things...

I use an Acer Aspire 5024 with a x700 graphic card... What could I do to get around the graphic problems on the live cds?

---

### Post by taurus on 2007-06-06
Before you installed using the alternate CD, did you run a CD check from the first menu to make sure the CD is good?  Also, make sure you burn it at a slow speed like 4x.

I would do the check CD first though.

---

### Post by foxmulder on 2007-06-06
Hi,

I have had the same/ similar problems with my PC even for the LiveDVD/CD of 6.06 (see my post from over a year ago: [http://ubuntuforums.org/showthread.php?t=139921](http://ubuntuforums.org/showthread.php?t=139921)).

No one ever bothered (or was able) to help me there so I had to figure it out myself. The problem is that the generic Ubuntu driver for my card doesn't work!

Here is how I managed to get everything working:

1) Install Ubuntu in text mode (I think you can do than from the Alternate CD) so without a graphical interface
2) Set up your network and make sure you have another PC that you can use to login to your Ubuntu PC
3) Install SSH ("sudo apt-get install SSH")
4) Install the graphical desktop of your choice ("sudo aptitude install ubuntu-desktop" for Gnome)
5) when your screen gets garbled after reboot try to go to a terminal using "ctrl-alt-f1")
6) Login to terminal and kill Xorg: "sudo /etc/init.d/gdm stop

- note: when using ctrl-alt-f1 gives you a grabled screen you can still login your PC by using SSH from a remote PC: you then can kill GDM (see step 6) and probably you can use your laptop again...

7) Download and install "ENVY": [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Envy will install the right drivers for your Nvidia OR (in your case) ATI driver; it has a text mode so that should do the trick..

See Envy website for more info...

To be honest I do not know if your particular ATI card is supported, so check that first!

Also note that due to upgrades etc. you might run into problems and have to run the whole setup again from time to time...

The drivers that Envy installs are not open source...

Good luck!

Ps: in your case try to use 6.10 alternate as well; you can always upgrade your distro later to 7.04...

---

### Post by jarrett on 2007-06-07
Hey thanks for the quick replies!

I shall first try to check the cd for defects, if that doesn't work i'll go with foxmulder's advise and install 6.10 and after that do an upgrade...
I must say, something mighty strange going on with my laptop I think.. I tried to install Fedora 7 also after ubuntu failed, and of course that failed too.. It halted on 'Installing bootloader' and just didn't move past that point with my laptop going HOT as a ******!
I ran Kubuntu 7.04 on it just fine before I sent it to acer for repair, they have replaced the motherboard in it, but I don't think it's anything wrong with it, because Windows XP installed and ran just fine on it :-\

---

### Post by jarrett on 2007-06-08
It was the stinkin' cd that was corrupt :(
Burned a new one at 4x and it worked just fine...
Thanks taurus!

---

