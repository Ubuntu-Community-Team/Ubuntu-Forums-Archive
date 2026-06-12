---
title: "Boot failure after disabling gdm"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by oborysm on 2005-11-11
I have Ubuntu set up working nicely in my home LAN. Now to save resources, I want to disable X and use it as a headless server. I don't want to remove X, I just want to boot to a command line, with the option to start the GUI from the command line if I want. Is it feasible to modify Ubuntu to run headless this way, without actually reinstalling in server mode? Or is the gdm so intertwined the system won't work without it? 

So following some advice in another thread, I disabled gdm with:

# update-rc.d -f gdm remove

and that removed all the gdm entries in my rc.n files (I was surprised to see gdm in every run level!)

But when I rebooted, it hung right after entering runlevel 2, "Checking battery state.."  Is this a known problem? 

I was able to restore it with:

# update-rc.d gdm defaults

Thanks for any help!

---

