---
title: "xserver problems on install"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by clark3rd on 2004-12-01
Sorry if this has been addressed already, I looked but didn't find a previous thread about this, so . . . .

I'm having problems with the xserver post install. The install goes smoothly and at the end it says I can now log into my new system. This is where the xserver fails (can't find any screens) and disables GDM and dumps me at the command line log in prompt.

This is what happens most of the time. I've installed Ubuntu quite a few times, and here's why. The very first install, it popped up a screen asking what screen resolutions I wanted to set the xserver, and presented a list. I chose 1024x768, 800x600 and 600x400. It finished install and booted into Gnome and it was beautiful. I love Ubuntu. But, I had to reinstall and for the next 10 (or there abouts) installs, it didn't ask for my desired screen resolutions, and the xserver failed as described in the previous paragraph. On the 11 (or there about) install, it asked for my preferred screen resolutions, and behold I had Ubuntu and Gnome working again. I looked at the xfree86.config file, at for the monitor section, it listed "Generic" as the monitor type.

Not smart enough to leave well enough alone, I screwed things up and had to reinstall, yet again. Well, I've tried a number of times at fresh installs, only to not get the screen asking for my preferred resolutions, and the xserver failing each time post install. I looked at the xfree86.conf file, and behold it correctly IDed my monitor and all the resolutions it can render. So, it seems that I can only get the xserver working when the install can't correctly probe the monitor, and needs input from the user to set the desired screen resolution during the install.

I've got a pretty plane jane machine, and everything seems to get detected correctly. The only thing unusual is I have a KVM switch and I think I recall a post where there is a potential problem with them.

Thanks for any insight you folks might have.

---

### Post by calvinpriest on 2004-12-01
Sounds like a bug in the installer.

What I'd recommend is making a backup of /etc/X11/XF86Config-4 now that it's working.

If you ever have to reinstall again and have the same problem, you can just restore the file to that location, from the command line.  And then boot into X (reboot or do "startx") and go about your business.  

Or you could compare the two, see what's different, and make manual changes (if you're curious).

---

