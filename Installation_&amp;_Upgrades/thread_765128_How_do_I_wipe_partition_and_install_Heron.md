---
title: "How do I wipe partition and install Heron?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2008-04-24
Does someone have a link or list of instructions to completely wipe out an existing partition of Ubuntu (running 7.10 at the moment) on a secondary HD and then install Hardy Heron fresh?

I installed a VMWare partition back with 7.04 that got corrupted upon upgrading to 7.10.  I've never been able to wipe out/reinstall that old VMWare partition since I upgraded to 7.10. Since Hardy is now here, I'd simply like to completely wipe out that entire partition (it's on my second harddrive in my main computer) and do a fresh install of Hardy.

I fear that GRUB or something might get corrupted to where I can't log into my Windows partition (on my first harddrive) anymore.  If this happens my wife would be ohhhh upset with me.

Any tips to keep me straight and to make sure I don't get yelled at?

---

### Post by Peter09 on 2008-04-24
Use the LiveCD. Format the existing partition when you come to install it and there you go. :)

PC

---

### Post by essexboyracer on 2008-04-24
also try gparted livecd or sysrescuecd, essentially the same as the LiveCD from ubuntu, but a tool specifically for the job

---

### Post by Shinobi326 on 2008-04-24
That's it?  Seriously?  I was expecting a 10 point checklist.... but maybe I'm just a nervous nelly old-school user :lolflag:

---

### Post by Shinobi326 on 2008-04-24
Also I've had a heck of a time to get my nvidia gts8800's to work with ubuntu in general (I always have to compile the drivers manually...restricted drivers or envy have never worked before).  

Is there a list of setup files I should print out/save so I can make sure I get my settings to work again?

I'd like to know my video card settings, my NAS network drive mapping/settings, printer settings... what are the files I need to save/print?

---

### Post by Peter09 on 2008-04-24
Hardy has a new version of envy called envyng, might be worth trying that. Its in the repository already.

PC

---

### Post by legendnz on 2008-04-24
You could load the live version and download any updates making sure your video drivers work. Then you could install, making the Ubuntu disk partitioner take care of any previous partitions. When I installed Ubuntu, I made two partitions for Ubuntu and one 2GB for swap. That way I set my second partition for my home folder so if I upgrade again I can do so and leave my home folder intact :)

---

