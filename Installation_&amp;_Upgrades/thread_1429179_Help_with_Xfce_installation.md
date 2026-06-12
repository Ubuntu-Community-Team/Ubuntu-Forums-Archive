---
title: "Help with Xfce installation"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by OmniCloud on 2010-03-13
Wasup Community... trying to split up partition between Windows and Linux...

I'm trying out a few distros for my wife's hp laptop. (AMD 64bit with ATI graphics card) I have Live CD's of the latest Ubuntu and Xubuntu. Started off with Xubuntu and the live CD detected everything very well so I installed it and split up the drive between Xubuntu and vista using the install manager. Everything went smoothly...

Windows is fine, but after logging into the default Kernel (generic etc..) it doesn't load the actual Xfce desktop, but just leaves me at the command promp ttyl I think. I tried to run "startxfce4" and got an error that no drivers were detected.

there's also a error when i first boot up that something couldn't be mounted.

I'll re-post the error info in full when I get back, but where should i get started? How do i get into the actual desktop environment? I also can't get into root, as I don't know what the default password is, so i can't install anything. Maybe I'm just thinking too much into it lol..Where do I start?

Thank you very much in advance

---

### Post by OmniCloud on 2010-03-13
seems this is a bit of a widespread problem...THere are some fixes on the Wiki, but I'm not sure exactly which is specifically for my problem. 

The error message when trying to startx is this 

EE Failed to load module "Fglrx" (module does not exist 0)
EE No drivers available 

Any help? Do I edit a config file somehow to workaround this?

---

### Post by OmniCloud on 2010-03-14
bump...

I see this is a popular problem...is there a definite fix to this? My xorg. config is completely empty btw...

---

### Post by OmniCloud on 2010-03-14
Problem is the installer...Both ATI and Nvidia graphic cards are of course restricted drivers that you have to download once logging into your new desktop. The installer on the Live CD gives you the option to install these restricted drivers, and after installation, your default xorg conf is looking for a driver that isn't there. 

The simple solution that worked for me was to just do a clean re-install without changing any of the default settings. I'm not running Xubutu 

Even though I didn't get a reply, the stick above has all the info about this bug. Hopefully my upgrade to the LTS version next year will go smooth, then I won't have to worry about anything for another 3+years...

---

