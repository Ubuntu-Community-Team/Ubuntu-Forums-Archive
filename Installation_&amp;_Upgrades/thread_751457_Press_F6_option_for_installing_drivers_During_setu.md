---
title: "Press F6 option for installing drivers During setup"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by SonicSteve on 2008-04-10
Forgive me if this idea has already been mentioned but here goes.

Just like windows has a Press F6 option for Windows XP and a spot in Vista to add SATA/Raid controllers it would seem that Ubuntu needs such an option. Here's why.

A friend of mine is building a system (OK I'm most the one building it) The mainboard is an ASUS P5e-WS-Pro with a real honest to goodness Raid controller on it with 6 SATA ports. He wants me to configure this baby with XP and Vista both using 64 Bit versions. Now before you get too bent out of shape this brings me to the Why.....
Ubuntu couldn't boot up with this board.
The driver CD has drivers for source code, Redhat and Suse. 

If Ubuntu had a pre-Bootup Press F6 that you could specify source code or drivers it may have had a hope.

What do you guys think? Has this been suggested before?

---

### Post by SonicSteve on 2008-04-11
Does someone know how to move this thread to the Ubuntu Ideas area? After thinking about it I don't think Installation and upgrades is the right place for this.

---

### Post by twist2b on 2008-04-11
This is actually "common sence" though when n00bs come (trust me, ubuntu draws n00bs) you can suggest.

Drivers can be added after install. If you cant boot, adding in recovery mode works.

When I had Feisty I had to add official nvidia drivers before I could use the OS. to do this I used "apt-get install nvidia-glx-new"
then changed my driver choice in "dpkg-reconfigure xserver-xorg"

---

### Post by SonicSteve on 2008-04-12
I'm not quite sure I understand your comment. 
What is common sense? My idea? Why would I suggest it when "n00bs come? 
Would you mind explaining?

---

### Post by twist2b on 2008-04-12
I'm saying that getting drivers for your OS is common sence. Everyone should know that drivers are one of the most important things to get/install

Though you can also get the drivers AFTER install and go straight to recovery mode.
I install my drivers after install in recovery mode for instance:

I go into recovery mode (I have nvidia graphics)
and type this:
apt-get update
apt-get install nvidia-glx-new
dpkg-reconfigure xserver-xorg
choose the newly added "nvidia" driver and move through the steps
My graphics are now working under good drivers. I can now add sound and wireless drivers while booted.

I also suggest Envy for getting good Nvidia/ATI support.

---

### Post by SonicSteve on 2008-04-14
I understand, 
The main trouble is that installation is impossible in some cases. Such as the Asus mainboard above, the P5E-WS-PRO. Without having a during setup option to load drivers for the chipset it is impossible to use this board. 

However if there was an option to use Third Party drivers during setup (at you own risk of course) there might be a hope to use it. 

I think Ubuntu needs to have the same option as Windows XP. Press F6 to load third party drivers, it's done right at the beginning of setup and then immediately used and compiled into the OS. Ubuntu could do this also. There are have two or three different instances I seen in recently where Ubuntu didn't jive quite properly with the mainboard chipset, thus making installation either difficult or impossible.

Here is a link to the thread I started in the Ubuntu Ideas pool
[http://ubuntuforums.org/showthread.php?t=755103](http://ubuntuforums.org/showthread.php?t=755103)

---

