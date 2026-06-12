---
title: "After upgrade, how do I use a wireless network?"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by T C on 2012-12-29
I just upgraded Ubuntu and now I have many problems. I plan to tackle them one at a time. In this thread, I'd like to solve my problems with wireless networking.

Before I upgraded, the computer would automatically connect me to my home network. Now, it doesn't seem to be doing that. Furthermore, I can't figure out how to see a list of available networks and I can't figure out how to connect to one.

In this new version of Ubuntu, how do I see the networks available? How do I connect to one? How do I know, at any given moment, whether the computer is connected to a wireless network and, if it is, which network it is connected to?

-TC

---

### Post by dino99 on 2012-12-29
"I just upgraded Ubuntu"

thats a great news :p but what else ?

[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/)
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

note: with some hardware, network-manager can be horrible, but wicd is a nice choice.

---

### Post by T C on 2012-12-29
dino99,

Thank you for the reply. Please bear with me -- I'm very much an Ubuntu novice.

From your post, I infer that I should be looking at an application called "Network Manager". When I look in the Ubuntu Software Center, it tells me that something called "network-manager-gnome" is installed, but I can't figure out how to launch it.

Also, I've tried to make headway with the "Networking tips and tricks" you referred me to, but I can't get anything to work. The "Connection Information" option under the networking icon is greyed-out. And when I try "iwconfig" from the command line, I get:

```
lo      no wireless extensions.
eth0    no wireless extensions.
```Can you suggest the next step?


-TC

---

### Post by darkod on 2012-12-29
The Network Manager icon is top right, in the top bar. It looks like wi-fi symbol, or like two arrows up/down. Clicking on it will open the network options. If the adapter is recognized correctly, it should display the available networks.

If the adapter is not recognized correctly, you will need to install the correct driver or make it work in any other way. Only after that it will show you the networks.

---

### Post by T C on 2012-12-29
Darkod,

Thanks, that helps a lot! I didn't see any networks in that area, so I didn't realize that's where they would be displayed.

It looks like my adapter is not recognized correctly. I'm a little confused about how this is possible, since everything was working okay before the upgrade. Does the upgrade uninstall or change drivers?

In any case, I went to System Settings / Hardware / Additional Drivers to see if I could reinstall the driver. There, I have the option to install a driver called "Broadcom STA wireless driver". However, when I try to install it, I get the message "Sorry, installation of this driver failed." The log file says this:

```
DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```I don't know what that means, but "blacklisted" sounds bad.

I'm going to do more research on this, since it now clearly sounds like a driver issue. In the meantime, I'd be grateful if someone could give me a better understanding of why an upgrade like this would break things that used to work.

-TC

---

### Post by darkod on 2012-12-29
Do you remember if you had those modules blacklisted on putpose earlier?

I remember in previous versions you sometimes needed to blacklist the b43 module so that the wi-fi can work. Maybe in the new version it needs actually not to be blacklisted.

Anyway, the blacklisted modules are usually in /etc/modprobe.d/blacklist.conf but if you didn't put them there yourself, they might not be there.

Since you now seem to know where the issue is, you might wanna make a new thread in the Networking subforum. People there know more about wi-fi and specific drivers.

As for an upgrade breaking things that work, doing an upgrade to another version is not the same as only updating the packages of the current version. Some things that were working might not work by default, as you noticed. Ubuntu has a new release every 6 months and personally I don't recommend doing an upgrade every 6 months just for this reason. I stick to LTS releases which are usually tested more. And do clean installs instead of upgrades.

---

### Post by T C on 2012-12-29
Darkod,

Thanks for the help. I've moved my question over to the Networking forum, where they are already discussing this issue: [http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)

-TC

---

