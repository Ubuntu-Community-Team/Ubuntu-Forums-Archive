---
title: "Lost all my good settings"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by freymann on 2007-12-20
In search of enabling better graphics on my new Ubuntu 7.10 Gutsy system, I have managed to screw things up. I installed the Server version, then added unbuntu desktop with Gnome.

Everything *was* great. Good screen size, sound, network neighbourhood. But I couldn't enable desktop effects and the restricted drivers manager keeps telling me I need to install linux-restricted-modules-2.6.22-14-server but when I try that it says it doesn't exist.

SO...

I removed anything to do with restricted modules in add/remove and synaptic package manager.

I rebooted a few times.

Then I went back in to Add/Remove, System Tools, searched for nvidia, and selected Restricted Drivers Manager (the first option), and Nvidia binary xorg driver 'new' (the 3rd option). It installed, told me to reboot.

Now I see new options on my grub menu..

7.10 Kernel 2.6.22-14-386
7.10 Kernel 2.6.22-14-386 (safe mode or whatever)
7.10 Kernel 2.6.22-14-server
7.10 Kernel 2.6.22-14-server (safe mode or whatever)
7.10 Kernel 2.6.22-14-server
7.10 Kernel 2.6.22-14-server (safe mode or whatever)
XP

So I selected the first option and got a few more notices about enabled restricted drivers. But first thing I noticed is no more sound. Oh well, let the restricted thing do its job. Nice, I have desktop effects as far as I can tell.

But no sound! and no more network neighbourhood so I can't browse the hard drives on my other computers!? Oh, and it no longer shows both CPU's being utilized, only 1.

So I rebooted and this time I selected the 3rd option, which is what I've been using up to now, and now it's complaining about video drivers, keyboard layouts, my screen is ugly at 800x600 and I can't change it, and although my sound is back, no network neighbourhood, but both CPU's are back.

You know, I really don't care about the desktop effects. Can I just go back and deselect this stuff from add/remove and be back where I was?

---

### Post by freymann on 2007-12-20
I did make a backup copy of my xorg.conf file before I started goofin around, so I copied it back and logged back in and now my screen is back to 1280x1024 and everything looks good. Network Neighbourhood is showing the other computers, I've got sound, dual processors. I think I'm back where I was.

I still can't change the video driver, I still can't access Restricted Drivers Manager, but at this point, I really don't care.

How does one edit GRUB to remove the latest entries I don't like? It seems to want to default to it now... 

1) 7.10 Kernel 2.6.22-14-386
2) 7.10 Kernel 2.6.22-14-386 (recovery mode)
3) 7.10 Kernel 2.6.22-14-server
4) 7.10 Kernel 2.6.22-14-server (recovery mode)
5) 7.10 Kernel 2.6.22-14-generic
6) 7.10 Kernel 2.6.22-14-generic (recovery mode)
7) XP

The one that seems to work best for me is #3. I would be happy to eliminate 1 and 2 completely. 

Ubuntu is new to me, but I'm learning. How do I remove those things from GRUB?

I'll add this: I read how to edit the file that controls Grub, and I simply removed the two lines I didn't want anymore. Seems OK.

---

