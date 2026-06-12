---
title: "grub update impasse, Ubuntu 10.04"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by murrayE on 2010-07-15
I just did a clean install of Ubuntu 10.04 Desktop (as a guest virtual machine in VMware Workstation 7.1 on a Windows XP host), using a .iso image. All defaults were accepted during installation.

After restart, I get the usual package update notifications so I did the software update. After it downloaded everything and completed most of the package updates, it got to grub (presumably grub 2). I got pop-up "Debconf on Ubuntu" window with title "Configure grub-pc". Unchecked there was "Continue without installing GRUB?" Naturally, I left that unchecked and clicked the Forward button. But nothing ever happened -- everything just stopped. (I waited 10 minutes.) So instead I checked "Continue without installing GRUB?" and clicked Forward. Now the update process continued to its end. I did a restart.

But I got a kernel panic message and could not boot.

Next, I uninstalled Ubuntu entirely and did a clean install. This time, for the software updates I chose only the one for grub-pc. But exactly the same impasse.

How resolve this impasse?

VMware Workstation folks assure me this is not a VMware issue but rather an Ubuntu / grub issue.

I've read the docs on grub 2, but I really don't know where to start, since the whole installation process was essentially transparent to me, with my making no choices other than language and time zone (accepting defaults).

I'm still a Linux & Ubuntu novice -- I just want to USE Ubuntu!

---

### Post by sprosty on 2011-02-02
Similar issue experienced today, upgrading my servers which use Ubuntu 10.04 Server LTS.

Ran upgrade via: 
$ sudo aptitude safe-upgrade

During the upgrade a blue screen dialog (curses?) pops up, entitled "Configuring grub-pc" which states:

[FONT=Courier New]You chose not to install GRUB to any devices. If you continue, the boot loader may not be properly configured, and when your computer next starts up it will use whatever was previously in the boot sector. If there is an earlier version of GRUB 2 in the boot sector, it may be unable to load modules or handle the current configuration file.

If you are already running a different boot loader and want to carry on doing so, or if this is a special environment where you do not need a boot loader, then you should continue anyway. Otherwise, you should install GRUB somewhere. [/FONT] [FONT=Courier New]

Continue without installing GRUB?   <Yes>  <No>[/FONT] 

For me, "No" was highlighted. If I click "No" the same screen just reloads again with the same text. The only way I was able to continue with the upgrade was to click on "Yes". Upon reload the server seems to work fine. 

However I had installed grub on my servers during the original installation, so the dialog stating that I had chosen not to install grub was confusing. 

All my servers run as VPS's

Just curious if others have had similar experiences or further insight into this. Thanks.

---

