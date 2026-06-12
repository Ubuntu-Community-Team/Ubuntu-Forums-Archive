---
title: "Xubuntu 6.10: won't boot after installation."
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by captainpotato on 2007-02-20
Hello,

I've just installed Xubuntu 6.10 (alternate CD) on an old box that I have lying around. The installation went without a hitch. However, upon booting, I've had a few problems.

On the first attempt, I was given a warning telling me that it could not load the welcome screen and that it would try an alternative (roughly this - the message went away quickly). It then booted to the login screen. I enter my username and password, and the machine goes into a cycle of what seems to be changing the screen resolution (even though the boot screen is fine), and then returning to the login screen (if I'm lucky).

I then changed the xorg.conf file to lower the maximum screen resolution to see if this was the issue, using a failsafe boot from grub (the X failsafe options, well, fail...). I can now get to the desktop, but it immediately returns back to the login screen.

The machine's nothing unusual - a Celeron 366, running a Voodoo 3 graphics card, an MSI motherboard, and a couple of PCI cards. It has 128mb RAM, and a10gb hard drive.

Any ideas?

---

### Post by Kateikyoushi on 2007-02-20
I would try to reconfigure X with the following command.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by captainpotato on 2007-02-20
Thanks for your response - I'll give it a shot from the failsafe login to see how it goes.

---

### Post by captainpotato on 2007-02-20
(Won't let me edit my last post...)

Update: no change from before. I did see another option in the card recognition section that I'll try tonight - it chooses 'tdfx' by default, but there is also 'voodoo' as an option.

---

### Post by captainpotato on 2007-02-21
Replying to myself again - no change, I'm afraid.

Any other ideas?

---

### Post by kingcharles1666 on 2007-02-27
the tdfx driver is broken in edgy, you need to select the vesa driver or go straight to feisty

see
[http://ubuntuforums.org/showthread.php?t=212175](http://ubuntuforums.org/showthread.php?t=212175)

---

