---
title: "nvidia X server issue"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by TrentG on 2007-08-25
Hi There,

The problem has occurred due to a stupid fault of mine while using the livecd, I just need some advice to work around it so I can get back in to X and fix it.

I have Ubuntu running on a HP dv6000 series notebook which is dual booting with Vista. 
I ran it off a livecd and stupidly played with nvidia drivers before running an install. What I did not do is restart the livecd before performing the install so now when Ubuntu loads it cannot find the nvidia driver and gives an error similar to:

(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

How can I set it to defaults so I can get in and then install the nvidia driver so it works properly?

I have done some stuff in the linux shells but it has never been relating to configuration of the graphical interface so I am dumb on this one.

Your help would be appreciated!

---

### Post by merlinus on 2007-08-25
At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then reboot.

-merlin

---

### Post by TrentG on 2007-08-25
Thanks mate!

That is all I needed and I could not find anyone to assist me with it before posting here! :)

---

