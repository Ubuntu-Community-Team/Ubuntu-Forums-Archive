---
title: "Upgrade failed, now system unuseable"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by IceblueGen3 on 2010-10-11
I upgraded from 10.04 to 10.10 a few hours ago using the alternate CD. I selected not to download files off the internet as I wanted to do that at a later stage. After running for close on an hour performing the update, as it reached the end it gave me a message saying the update had failed and the changes will now be restored (or something like that). I clicked ok, and the update window closed. I then restarted the pc and it stopped at the splash screen. Now I cannot get it to load the desktop environment. It Jst sits at the splash screen. Pressing the power button shuts it down normally, but alt-ctrl-f1 does not open a shell.

If i start up using recovery mode and then select fail safe graphics mode something comes up about a segmentation fault in xserver in I then end up at the shell where I can work from the command line, but can never get the graphical interface to work.

Can anybody help me? I'm still quite new to Linux and I need my pc urgently but am trying to avoid a clean install

---

### Post by mörgæs on 2010-10-12
Does it work when booted with a live CD?

---

### Post by santosamaru on 2010-10-12
Upgrading from Ubuntu 10.04 LTS
To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.10' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 10.04 LTS on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade -d; and follow the on-screen instructions.

To upgrade from Kubuntu 10.04 LTS follow the instructions at [https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu](https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu)

---

### Post by IceblueGen3 on 2010-10-12
> **mörgæs said:**
> Does it work when booted with a live CD?

I don't have a 10.10 live disc. Will get one in the next two hours and try it. But it boots fine using any of the older live discs.

---

### Post by roddie on 2010-10-12
> **santosamaru said:**
> Upgrading from Ubuntu 10.04 LTS
To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.10' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 10.04 LTS on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade -d; and follow the on-screen instructions.

To upgrade from Kubuntu 10.04 LTS follow the instructions at [https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu](https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu)
He's already upgraded and now can't get past the splash screen.

---

### Post by garvinrick4 on 2010-10-12
Does 
```
startx
```do anything
If not are you missing 
```
sudo apt-get install gdm
```If you can get to a command line and startx does not work.
```
sudo apt-get install aptitude
``````
aptitude show gdm
```It will tell you if installed or not. You are missing something find out what?
Most likely is going to be the desktop envirment which is gdm or ubuntu-desktop is the whole ball of wax. But if you use aptitude show (package name)
you will find what is missing. Alternate cd does have installs without the GUI!!!

---

### Post by IceblueGen3 on 2010-10-12
```
startx
```
gives the following output:
(EE) failed to load /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(EE) failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available

Fatal Server error:
no screen found

ddxSigGiveUp: Closing log
giving up.
xinit: No such files or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): server error.

```
aptitude show gdm
```
says that gdn is installed.

Am I correct in saying that the ATI driver is not installed (based on the above output)? If so, how do I fix this?

I also tried renaming the the xorg.conf file as recommended in another thread I read. When I do this I get past the splash screen but then shows the text style login screen (non graphical).

If I then type startx I get a long text output which contains the following near the bottom:
8: /usr/bin/X (0x8048000+0x1a191) [0x8062192]
Segmentation fault at address (nil)
Caught signal 11 (Segmentation fault). Server aborting.
ddxSigGiveUp: Closing log
giving up.
xinit: No such files or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): server error.

---

### Post by IceblueGen3 on 2010-10-12
oh and the live CD boots fine.

---

### Post by IceblueGen3 on 2010-10-12
Ok I managed to get it working. I removed fglrx and then reinstalled it all, so X starts fine now.

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall xserver-xorg-core

```I'm still having some minor issues with the upgrade (it was only partial), but I should be able to sort that out.

Thanks though to all who tried to help!

---

