---
title: "[SOLVED] Nightmare Upgrade 7.10 to 8.04"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Porpoise on 2008-05-11
It's a nightmare!

Did update then did upgrade and the system hung just before the end of the upgrade. Had to reset the PC, then it wouldn't boot into Ubuntu. I could get to a console but couldn't do anything.

Now I've bitten the bullet and installed from scratch (from CD).

The problems I now face are:

In 7.10 I had the /home, /mythtv, etc. folders on a seperate partition but now don't seem to be able to find the info to point to these other folders. (This would presumabley then enable Thunderbird etc. to pick up all my previous settings - which they currently don't).

I can't remember whether this was done as part of the installation process last time, or as a modification of configuration files somewhere.

It'll be really tedious having to re-configure everything from scratch, so if anyone can enlighten me I would be grateful.

(Still couldn't get MythTV to work in 7.10 so that might benefit from starting from scratch in 8.04) :(

---

### Post by tgalati4 on 2008-05-11
If this is a desktop machine, then a process that I use:

Put in a second hard disk.  Load the new distro CD and boot from it.  Install the new distro to the new disk.  Ubuntu detects a previous Linux installation and asks if you would like to import the user.  Say yes.  Continue with the installation.  Edit GRUB if needed because sometimes GRUB gets confused by your disk numbering or hardware configuration.  

Boot to the new distro and your settings should be intact.  It worked for me from Feisty to Gutsy, and I'm preparing to do the same with Hardy.

If there is something broken in the new installation, you always have your previous installation (which still works and is untouched.)  In time, Hardy will become as solid as Gutsy.  It's a tradeoff of patience vs capability.

Upgrading from one version to the next has been hit-or-miss.  By overwriting your old installation, you will definitely lose configuration settings.

The upside is that you get better at it with each new release.  Another hint:  every time you touch a configuration file, make a backup of it in your home directory.  This way you will know which files were modified in your previous release.  You can't simply copy the files over to the new release because of framework changes--config files are changing all the time.

---

### Post by Porpoise on 2008-05-11
> **tgalati4 said:**
> If this is a desktop machine, then a process that I use:

Put in a second hard disk.  Load the new distro CD and boot from it.  Install the new distro to the new disk.  Ubuntu detects a previous Linux installation and asks if you would like to import the user.  Say yes.  Continue with the installation.  Edit GRUB if needed because sometimes GRUB gets confused by your disk numbering or hardware configuration.  

Boot to the new distro and your settings should be intact.  It worked for me from Feisty to Gutsy, and I'm preparing to do the same with Hardy.

If there is something broken in the new installation, you always have your previous installation (which still works and is untouched.)  In time, Hardy will become as solid as Gutsy.  It's a tradeoff of patience vs capability.

Upgrading from one version to the next has been hit-or-miss.  By overwriting your old installation, you will definitely lose configuration settings.

The upside is that you get better at it with each new release.  Another hint:  every time you touch a configuration file, make a backup of it in your home directory.  This way you will know which files were modified in your previous release.  You can't simply copy the files over to the new release because of framework changes--config files are changing all the time.

I kind of nearly started there (should have known better really) but no spare disk capacity at the moment - until I have to time to sort out all the duplications...

Anyway, I still have all the /home  data on a seperate drive - I just can't remember how to get the new install to use this data so I don't have to re-configure email and everything from scratch.

---

### Post by inportb on 2008-05-11
You have the option to manipulate your partitions and mount points alllll the way at the beginning, when you're telling the installer what to do.

Otherwise, all you have to do is boot into a live session, copy all the new /home files into the old /home if you want the new configuration, add fstab entries for /home and /mythtv, and delete the new /home. Reboot. After you boot up, you might need to recursively chown your home directory to your user+group.

---

### Post by HunterThomson on 2008-05-11
when you reinstall you chose the manual partition option. Then you have to relabel the partitions back to /home and all.... Then you have to make the user name and password the same. And then all the settings will be the same wallpaper fierfox and all.... And you will not have any problems...

---

### Post by HunterThomson on 2008-05-11
> **inportb said:**
> You have the option to manipulate your partitions and mount points alllll the way at the beginning, when you're telling the installer what to do.

Otherwise, all you have to do is boot into a live session, copy all the new /home files into the old /home if you want the new configuration, add fstab entries for /home and /mythtv, and delete the new /home. Reboot. After you boot up, you might need to recursively chown your home directory to your user+group.

Yes you can do this too but after that all the files will be ownd by root and you have to change the ownership of them all and could end up taking longer then just re-installing again. 
The choice is up to you.

---

### Post by Porpoise on 2008-05-18
Managed to sort it out by editing the .conf to re-map /home to the other partition and, BINGO! there was all my data as before!

---

