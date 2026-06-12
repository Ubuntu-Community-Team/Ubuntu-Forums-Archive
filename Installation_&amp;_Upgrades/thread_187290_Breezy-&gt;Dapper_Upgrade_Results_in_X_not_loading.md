---
title: "Breezy-&gt;Dapper Upgrade Results in X not loading libGLcore.so and no network"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by kimastergeorge on 2006-06-02
EDIT: Don't read anything else, just read this: The main problem is that the networking is down. Not even localhost works. X complains that it can't find the hostname. Every time I call sudo, two errors pop up with a similar problem. ifconfig returns blank; again, not even localhost is shown. What's going on?

End EDIT

I have used Breezy for a while and loved it, but I just tried to upgrade from Breezy to Dapper with bad results:

First, I went to the terminal, and ran:

sudo update-manager -d (or whatever the graphical upgrade tool is)

This ran, and I allowed it to run overnight.

In the morning, I discovered that the Apache config script was asking me whether to replace the Apache config file I had changed since I installed it. I asked it not to replace the file. (This is probably unrelated, but just so you know.)

Then, it ran a few config scripts. I waited for it to finish. Unfortunately, it never did. It stalled when it tried to upgrade libxml-sax-perl--the most specific answer I could get out of it as to why was that one of the commands in the post-install script returned 255, so it decided not to continue, and a slew of dependant packages wouldn't install, either. (My guess as to why this happened was because I probably tried to manually upgrade these files at one point using the command line utility, cpan. Although I don't specifically remember doing this, I bet this is what happened.) The update manager stopped right there and told me to try using Synaptic to try to update these files. I tried, and it failed in the same way. However, these packages seemed pretty inconsequential, so I just tried rebooting (after looking at a few websites in Firefox--an isolated Firefox 1.5 build I got off the website--and trying to switch the theme and start Gaim. The programs wouldn't start, though. I figured these were both because of a new version of GNOME.)

Once I rebooted, I noticed that the networking failed to initalize. Not to worry, I thought; this happens occasionally, I'll just reboot after this has booted all the way. A few seconds later, I found that GDM wouldn't start X. It complained that it couldn't load a file deep in /usr/lib which was named libGLcore.so. It claimed (this is more or less a direct quote): "Failed to load module "GLcore" (loader failed, 7)". It also complained that it couldn't find an fglrx device: PCI:1:0:1, and that fglrx couln't aquire AGP, with the error xf86_ENODEV. Finally, it also couldn't find the mouse device at /dev/input/mouse.

I suspect that if I could rerun the device detection and network/X.org configuration file generators, I could solve this problem (I assume my half-done upgrade at the beginning didn't do some sort of device detection which would have set up X.org and the networking to work with the newer drivers.)

Thanks very much

---

### Post by kimastergeorge on 2006-06-02
Bump, please answer, thanks

---

### Post by npnutn on 2006-06-11
I can't comment on the networking issue, but I am having a similar X server issue after upgrading to dapper last night.  Any luck with that yet?

---

### Post by rgutierrez on 2006-06-22
What does dmesg tell you? Does it tell you anything about your network card? Maybe a specific message regarding the module for your NIC?

---

