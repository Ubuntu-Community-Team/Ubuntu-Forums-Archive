---
title: "Nvidia in Hoary"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by elwis on 2005-03-13
Just did a big mistake upgrading my lovely Warthog to Hoary.
Anyway, what's done's done. But I would really like to get Nvidia working at least.

My problem is that starting without doing anything (old warty config) gives me a blank screen. So I downloaded the latest driver, but since there's no kernel-source (2.6.10-4) I don't know how to get it to work?? :(

EDIT: The log doesn't tell me much either, seem that the system thinks a white screen is good enough!

Well, better try to find the debian source for kernel 2.6.10-4, would be nice if someone put that one in the repos..

Edit II: The problem I suppose is that Hoary installs nvidia-kernel-common 1.0.7167 and the nvidia-glx is 1.0.6629.
Since there are are only incompatible versions available and no kernel source to let you compile the nvidia driver yourself, I guesss there are no nvidia in hoary?

---

### Post by Insanely on 2005-03-13
Since warty uses Xfree86 and Hoary uses x.org you need to copy your XFree86config-4 to xorg or xorg.conf (can't remember atm)

I'm not in front of my machine at the moment but it would work something like this:

sudo /etc/X11/xorg /etc/X11/xorg.backup
sudo /etc/X11/XF86Config-4 /etc/X11/xorg

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

cause i can't confirm any of the commands above try this how to (it's great):
[http://www.ubuntuforums.org/showthread.php?t=5608](http://www.ubuntuforums.org/showthread.php?t=5608)

---

### Post by elwis on 2005-03-14
[QUOTE=Insanely]Since warty uses Xfree86 and Hoary uses x.org you need to copy your XFree86config-4 to xorg or xorg.conf (can't remember atm)

I'm not in front of my machine at the moment but it would work something like this:

sudo /etc/X11/xorg /etc/X11/xorg.backup
sudo /etc/X11/XF86Config-4 /etc/X11/xorg

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

cause i can't confirm any of the commands above try this how to (it's great):
[http://www.ubuntuforums.org/showthread.php?t=5608](http://www.ubuntuforums.org/showthread.php?t=5608)[/QUOTE]
 Hi and thanks, but I already done that. The problem is my incompatible versions, I got tid of all the nvidia stuff and tried to reinstall but can't get the driver to work, it presents me with a white frozen screen. 
Well, maybe it's not Ubuntu's fault, could of course be that old Geforce2 card and the nvidia driver.

But i still can't get why there's different versions provided?

---

### Post by martijntje on 2005-03-14
[QUOTE=elwis]Hi and thanks, but I already done that. The problem is my incompatible versions, I got tid of all the nvidia stuff and tried to reinstall but can't get the driver to work, it presents me with a white frozen screen. 
Well, maybe it's not Ubuntu's fault, could of course be that old Geforce2 card and the nvidia driver.

But i still can't get why there's different versions provided?[/QUOTE]
 Just a few minutes or so ago, the update manager picked up a new version of nvidia-glx and nvidia-kernel-source. Maybe it solves the problem you just described.

---

