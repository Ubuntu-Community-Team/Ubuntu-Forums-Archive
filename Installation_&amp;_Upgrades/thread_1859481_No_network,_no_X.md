---
title: "No network, no X"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by cwwilson721 on 2011-10-13
Tried upgrading from 11.04 to 11.10. 11.04 full update, all working fine.

I used the upgrade GUI, after 9 hours (on a 20MB internet connection), it finished downloading.

Then, it installed. No issues.

Reboot, got into Gnome3.

All okay so far. But, needed to install "Additional Drivers" for my Nvidia card. All okay. Or so I thought.

Abruptly, the machine rebooted, and in the splash screen, says something about network connection, then waiting 60 more seconds, and then...Blank screen. No X.

Reboot, choose Recovery from Grub menu.

Chose root prompt with networking.

No interfaces enabled (ifconfig). Startx, ends up in Unity, no network. Tried network app, screen box disappears.

Cannot get online to diagnose in either cli or GUI.

Tried installing nvidia drivers from Nvidia already downloaded (The NV*.run), installs, still no X.

And no network.

What can I do?

Luckily, I dual-boot Win7 with Ubuntu, so I can get here and get advice.

---

### Post by cwwilson721 on 2011-10-14
Update:

While the "Network connection..." message was on the splash screen, I hit <ESC> to see what was going on...

modemmanager was going ape. modemmanager tries to connect to a broadband modem (like my smartphone). Since no smartphone connected, it was failing miserably.

However, I have since wiped that pesky install, and reverted back to 11.04, for now.

I'll finish my "base" insrtall, and try the upgrade again (I saved all the downloaded files in /var/whatever already. Maybe that will save some time

I'll update this as I get new info

---

### Post by varunendra on 2011-10-14
'Upgrading' the release from within an existing version using Update manager has the potential (I would say - tendency) to break the system or result in a faulty setup. That's why it is always recommended to do a fresh install using the installation CD or USB. Moreover, the live cd gives you the chance to test the os before installing it to see if it plays nicely with your hardware.

Accordingly, I would suggest to either burn a Live CD, or create a Live USB with a fresh downloaded iso (it takes approx an hour or slightly more on my 2 Mbps connection), and boot into live mode to ensure it is suitable for your hardware. I would recommend trying a persistent Live USB, since you can install the NVidia drivers and whatever needed on it to see how it goes.

---

### Post by smitty825 on 2011-10-14
> **cwwilson721 said:**
> Update:

While the "Network connection..." message was on the splash screen, I hit <ESC> to see what was going on...

modemmanager was going ape. modemmanager tries to connect to a broadband modem (like my smartphone). Since no smartphone connected, it was failing miserably.

However, I have since wiped that pesky install, and reverted back to 11.04, for now.

I'll finish my "base" insrtall, and try the upgrade again (I saved all the downloaded files in /var/whatever already. Maybe that will save some time

I'll update this as I get new info


I'm in a similar situation as you.  I did the upgrade, and things got borked.

While X isn't working, I am able to get to a command prompt by hitting "Ctrl-Alt-F1".  I have re-enabled networking by modifying the /etc/networking/interfaces file and adding the line:

> iface eth1 inet dhcp to the end of the file.  (Your network adapter might not be eth1, but mine is :-) )

To temporarily re-enable your network interface, just type the following commands

> sudo ifconfig eth1
sudo dhclient eth1

---

### Post by cwwilson721 on 2011-10-15
After going back to 11.04, I booted into the 11.10 Live CD, removed all folders/files from my sda1 drive (except /home), and installed 11.10. All went fine.

Updated, reinstalled my "essential" packages (wine, restricted-extras, Gnome), and all is working great.

---

