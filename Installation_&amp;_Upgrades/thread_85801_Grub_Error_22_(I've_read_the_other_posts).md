---
title: "Grub Error 22 (I've read the other posts)"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Kez1980 on 2005-11-03
OK, I'm new to ubuntu but have successfully installed redhat, madrake, and several other flavours of linux in the past.

I tried initially to install as a dual boot with Windows XP, all went well in the install until reboot when I got the 'grub error 22'.

Now, I already knew about 'fixmbr' in the windows console so I tried it and it failed (I've done this several time before when removing lilo and grub after using the platforms above).  My only thought was that when resizing my windows partition before installing it made some claim that it was passing some cycle(I think?)  boundry and may not be bootable, but windows booted fine after the resize.

As the windows partition seemed to be foo-baa'ed I figured a complete reformat and allowing ubuntu to set up the partitions was worth a go.

Guess what, after install on reboot 'Grub Error 22'.

Does any one have any ideas?

---

### Post by teaker1s on 2005-11-03
fixmbr and there is fixboot command for x86 processors in xp recovery console

---

### Post by Kez1980 on 2005-11-03
[QUOTE=teaker1s]fixmbr and there is fixboot command for x86 processors in xp recovery console[/QUOTE]

:rolleyes: 

Perhaps read that I tried that and then did a single OS install on a clean disk with just Ubuntu.

---

### Post by tonysathre on 2005-11-03
that error means that u have a bad partition table, install windows first, then ubuntu, and make sure u manually partition your HDD

---

### Post by Kez1980 on 2005-11-03
Thanks for that 'tonysathre', do you have any recommedations for a good partitioning strategy?

---

