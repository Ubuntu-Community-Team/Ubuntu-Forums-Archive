---
title: "Borked Hardy to Intrepid Upgrade, Options?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by BJ_Covert_Action on 2010-10-26
Howdy Everyone,

So, there appears to already be one [thread]("http://ubuntuforums.org/showthread.php?t=1606648") very similar to this, but I wanted to repost for my own purposes. I decided last night to upgrade my 8.04 box to 8.10 to improve the functionality of some of my programs. Well, lo and behold it was an epic failure.  The upgrade got about 70% through and froze everything on the computer. I had to kill the upgrade-manager process and reboot. After rebooting, I couldn't log into the OS using the 2.6.27-17 kernel. I could, however, log into 2.6.24-28. 

The upgrade seems to have nerfed a lot of my networking abilities (it can't detect the wlan0 interface, even though I can see traffic on it, the eth0 interface is ridiculously slow). My nvidia drivers disappeared (it happens, I am not surprised). And over all the system is laggy and unresponsive. So I am thinking about doing a wipe of the hard drive (backing up my home folder now) and starting fresh. However, I was curious what options there might be for patching a borked upgrade.

I think I backed up most of the OS on an external hard drive via a tar command, but I do not know how much effort I would need to go through to unpack only parts of that backup. I am probably going to try an "aptitude upgrade" and "aptitude dist-upgrade" command tonight, but the networking is so slow that may not prove to be an option. Are there any recovery options that can be accessed through recovery mode or a live CD that might help?

It seems like I am in for a lot of work, either way. I just wanted to get some feelers out there for the simplest way to recover.

Thanks ahead of time guys.

---

### Post by BJ_Covert_Action on 2010-10-28
Hey guys,

So I am not sure if it ironed out all of the kinks or not, but hopefully it did. Essentially all I had to do was log on, kill the X-session (ctrl-alt-F2), stop the GDM process (/etc/init.d/gdm stop), and run the following commands:

```

sudo bash
aptitude update
aptitude dist-upgrade

```

The process took a few minutes and then, on reboot, things were moving along a bit easier. I should note that I had to reinstall my proprietary Nvidia drivers and do a new nvidia-xconfig to get the display issues fixed. Then I had to delete my /etc/network/interfaces file and reboot to get the network manager to handle my WPA2 encrypted wireless appropriately. All in all, I lucked out as those were the only issues I found. Good luck to anyone else doing an upgrade.

Cheers,
Brady

---

