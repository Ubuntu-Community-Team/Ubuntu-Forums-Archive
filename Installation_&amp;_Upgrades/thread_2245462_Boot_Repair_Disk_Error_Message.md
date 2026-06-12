---
title: "Boot Repair Disk Error Message"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by Priswell on 2014-09-23
I was doing an dist-upgrade from Ubuntu 12.04 to 14.04. During the upgrade, dialog boxes popped up asking what I wanted to do about grub, so I answered the questions as best as I can, but obviously wrong, because when I rebooted from the upgrade, it wouldn't boot properly. Only got a black-screen-white-text announcing that it had an issue with my mouse. I had no answers, so I tried to reboot. Same response. Got my files off of the drive as best as I could, but I had some late emails that had not been saved and needed, so when i read about the Boot Repair Disk, I created a Linux Secure Disk, and worked my way though the menus. 

I evidently was successful removing the grub that was in place, but go the following error message when it came to replacing grub:

E: Unable to locate package

Can someone help me with what to do next?

---

### Post by oldfred on 2014-09-23
Is Internet working? Better to have Ethernet hard wired not wireless.

Boot-Repair will in Advanced mode do a total uninstall of grub, but then download the latest package and reinstall. In between then you have no grub at all. But if download not working then you have that issue to resolve first.

Generally better to use same version, or 14.04 live installer. But Boot-Repair has not been updated so you really are using an older version from saucy.

Or if you had ppa or proprietary drivers in 12.04, they can prevent updates from happening as the ppa may not work with trusty.
Often other issues can be related to having correct video driver.

---

### Post by Priswell on 2014-09-24
*Is Internet working? Better to have Ethernet hard wired not wireless.*

I'm using a wired connection. On other boot ups with a live disk, I've had no trouble accessing the net, so I don't think internet connection is a problem.

*Generally better to use same version, or 14.04 live installer. But Boot-Repair has not been updated so you really are using an older version from saucy.*

So, use a 14.04 live install disk, install Boot Repair, then run that?

---

### Post by oldfred on 2014-09-24
If you have Internet then there must be something preventing update. If dpkg is blocked by an old ppa in your system sources or has other issue that also prevents grub from downloading as it wants to download everything else and cannot.

Best to have a 14.04 live flash drive or DVD anyway as you always need a current version repair disk for every operating system you have installed. But I have several Ubuntu installs on different drives, and boot ISO directly from grub. Then I can have on one flash drive with gparted, parted magic, Knoppix, Ubuntu(s) and other repair installs.

---

### Post by Priswell on 2014-09-24
Well, I used an Ubuntu 14.04 disk, installed Boot-Repair as instructed, ran the commands, chose "use maintainers copy" when asked to choose which grub to use, and rebooted and got a

grub rescue>

command line.

---

### Post by oldfred on 2014-09-24
Post link to the summary report that Boot-Repair creates.

---

