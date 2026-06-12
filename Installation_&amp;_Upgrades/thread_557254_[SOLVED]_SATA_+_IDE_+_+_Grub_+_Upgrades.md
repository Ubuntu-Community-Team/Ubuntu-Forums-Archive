---
title: "[SOLVED] SATA + IDE + + Grub + Upgrades"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2007-09-22
Hey all,

I had the ole IDE drive listed first problem with grub and Ubuntu installation. Got it all worked out, then clicked the upgrade button which installed 117 packages and a new kernel and undid the fixes I made in grub. Is there a way to prevent this in the future? 

Actually it turns out that all I had to do this time was to go into menu.lst and change all the hd0's to hd1's but I had to find, then boot the live CD, mount the linux partition and then change it. Kinda a pain.

Any ideas on prevent this change from happening again (or something worse?)

Thanks,
Eric

---

### Post by Pumalite on 2007-09-22
Make your changes to menu.lst and the find the line:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)


Change groot too.(leave#)

---

### Post by nowhere@cox.net on 2007-09-22
Thanks for that AMAZINGLY fast reply. I would just to clarify what you are saying.  You suggest uncommenting this line:

# groot=(hd0,0)

and changing the hd0 to hd1? Is this some flag pointing to the root folder of the linux partition? If so I will need to change it to hd1,1 since Ubuntu decided to make the second partition on the IDE drive its home during install.

Anyway, this will tell future upgrades NOT to change the location of the root I assume.

Thanks a TON!
Eric

---

### Post by Pumalite on 2007-09-22
I don't want you to uncomment it.

#groot=xxx

xxx to be replaced by you according to changes you make to kernel in 'root' line.

---

### Post by logos34 on 2007-09-22
> **nowhere@cox.net said:**
> You suggest uncommenting this line:

# groot=(hd0,0)

and changing the hd0 to hd1? Is this some flag pointing to the root folder of the linux partition? If so I will need to change it to hd1,1 since Ubuntu decided to make the second partition on the IDE drive its home during install.

Anyway, this will tell future upgrades NOT to change the location of the root I assume.

Upgrades don't change the location of root.

If your root partition (i.e. containing /boot) is on the second partition of the first disk (first in bios boot order), you want '(**hd0,1**)'.  If the second disk, second partition then you want '(hd**1**,1)'.

---

### Post by Herman on 2007-09-22
Yes, whenever we have a kernel update in Ubuntu, our menu.lst file for GRUB is refreshed 'automagically' with entries for the new kernel.
The new menu.lst file is written by the update-grub script, which is located in /sbin. 

The update-grub script looks at the section of our old (existing) menu.lst and especially at the 'AUTOMAGIC KERNELS LIST' area where settings are to decide exactly how the Ubuntu entries the new menu.lst should be written. 

When you edit your operating system entries in your menu.lst file to make GRUB work properly, you can (should) also update the corresponding item in your automagic kernels list to make your changes 'permanent'.

The Automagic kernels list can be found in our menu.lst files between around half way and three quarters of the way down the file, and it is marked with labels in capital letters at the beginning and at the end of it.
If you read the sentence right under the begining of it, you'll see that it says, "DO NOT UNCOMMENT THEM, just edit them to your needs". :)

The automagic kernels list is a great feature in GRUB and in Ubuntu. It saves us some work and makes life simpler for beginners. When we use LiLo instead of GRUB and we have a kernel update we need to edit the /etc/lilo.config file manually and then run /sbin/lilo.
Many other operating systems that use GRUB don't have any automagic kernels list, (non-debian based one I suppose), and I don't know how they get their menu.lsts updated. Maybe they have it done automatically some other way or do it manually or maybe they keep the same kernel for the lifespan of the release.
The Ubuntu developers work hard to keep Ubuntu up to date with the latest hardware and software innovations and are vigilant when it comes to security. Every once in a while a new kernel is needed keep our systems up to date in one or more of those areas.

Regards, Herman :)

---

