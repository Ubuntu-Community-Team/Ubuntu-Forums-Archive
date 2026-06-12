---
title: "[SOLVED] kernel 2.6.20-17-generic upgrade broke X -- now can't boot"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2008-06-22
I had a very solid "Ubuntu, kernel 2.6.20-16-generic" that I've used for months without any problems.

Then Synaptic "suggested" I do a large multi-file upgrade to "kernel 2.6.20-17-generic".

Now the updated system won't boot into Gnome -- the X system won't start and I get some essentially unhelpful offers to browse log files (as if I'll know what to do after I look at them...)

My *guess* is that it's my NVIDIA driver.

Synaptic tells me I have "NVIDIA binary kernel module for Linux 2.6.20-16-generic" installed, but I don't see a corresponding 20-17 version.  The only thing I do see is the still-uninstalled "NVIDIA binary kernel module source" for 20.6-17.

I re-ran Envy which is how I got my NVIDIA driver installed the first time.  It downloaded some files and recompiled and reinstalled my driver but I can still only boot into the version 2.6.20-16 Gnome, NOT the newer 20-17 version.

I've also added a Zip archive containing my xorg.conf and menu.lst files in the hope that someone can identify the problem.  Please Let me know if there's anything else I can supply that might help a more knowledgeable person unsnarl the mess...

Cheers & thanks,
Ric
SFO

P.S.  I'm trying to maintain a positive attitude, but this sort of thing is exactly why so many people throw up their hands in despair at Linux...

---

### Post by Pumalite on 2008-06-22
You have to reinstall your driver.

---

### Post by Phrawm48 on 2008-06-22
Pumalite:

Per "You have to reinstall your driver."  Thanks -- so far, so good.

Can you please be a bit more specific?  Which driver?  How, exactly?  Synaptic?

Cheers & thanks,
Riley
x5633

---

### Post by Pumalite on 2008-06-22
The one you installed for .16 previously. After each kernel upgrade you have to reinstall your video driver unless you did it with Hardware Drivers.

---

### Post by bsmith1051 on 2008-06-23
Do you really need the latest/authentic Nvidia driver?  If not you should just use the version included in 'Restricted Drivers Manager' since it's automatically updated along with each kernel update. 

Otherwise, you need to be VERY WARY of kernel updates!  When you see one listed in the updates, you should first run the Envy Uninstall routine.  Do the kernel update, then download and install the latest update of Envy before re-running it.

---

### Post by Phrawm48 on 2008-06-29
Well, I'm now dead in the water -- I can no longer boot into Gnome in either the -16 or -17 kernels.

Under -16 (the only one I could get a GUI running under), I used Envy to uninstall the Nvidia driver.  I then used Synaptic to uninstall Envy.

Now what?

Does anyone please have any steps I can take from the command line to get my system working again?  I sure hope so...

Cheers & thanks,
Ric
SFO

---

### Post by bsmith1051 on 2008-06-30
do you have the command-line login working?  if so, then you can try manually running the X configuration,
> sudo dpkg-reconfigure xserver-xorg

---

### Post by Phrawm48 on 2008-06-30
"do you have the command-line login working?"

Yes, in recovery mode.  But as you can tell, I'm not sure what to do with it.

So first I'll try the "sudo dpkg-reconfigure xserver-xorg" suggestion.  If that works, great.

If not, I'm thinking I may be able to use "apt-get" to install Envy from the -17 command line and go from there...(?)

Thanks to everyone who has responded -- believe it or not, I'm not entirely dumb, I just don't know what to do to remedy this situation without risking making it worse...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by Pumalite on 2008-06-30
You can also try xfix

---

### Post by frlgrb on 2008-07-01
This has happened to me as well. I think the proprietary NVidia drivers are the problem but am still investigating. I had to first install xserver-xorg from the command line. I did: sudo apt-get install xserver-xorg which worked well. Then I ran the utility as described below: sudo dpkg-reconfigure xserver-xorg and carefully accepted the defaults and recommendatons (not recommended if you're using anything other than an everyday reasonably current PC in North America). After I completed the configs I simply ran startx from the cmd line and booted to my Gnome session.

Now I need to figure out how to stabilize as my software updater now fails because of the new changes in xserver-xorg. I'm sure other stuff is fractured as well. Any ideas out there? How is your fix coming along Phrawm?

---

### Post by Pumalite on 2008-07-01
Do not install xserver-xorg in Hardy. It comes with it's own. Just install the driver.

---

### Post by Phrawm48 on 2008-07-05
Okay, thanks everyone -- I now seem to be once again bootable.

The key was the "sudo dpkg-reconfigure xserver-xorg" command.  (For whatever reason, I don't see "xfix" in my Feisty repositories...)

For whatever reason, I needed to make two iterations through it before I could get things working.

Also, because I could only boot into text-based "recovery" mode, I needed to run "gdm" to start Gnome; Gnome then expressed a bit of mild confusion regarding its settings versus the ones it was being handed, but a couple of mouse-clicks at GUI dialog boxes reconciled the settings and I my GUI was back.

Now, the only problem is that when Gnome first boots the screen resolution is wrong.  It's only after I login that my desired 1280x1024 settings get applied and everything looks right.  (Any ideas on that one, anyone?)

Cheers & thanks 'gain to all,
Ric
SFO

---

