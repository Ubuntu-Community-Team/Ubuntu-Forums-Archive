---
title: "setting up dual boot"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by SonicSteve on 2007-02-02
I'm hoping that with a bit of help from the Ubuntu clan this can be done with ease.
So lets see....

I want to end up with a dual boot between windows XP and Ubuntu

Currently I have 2 drives;
1. 80Gb Western Digital -Has windows XP, NTFS
2. 30Gb Maxtor -Has Ubuntu, EXT3

They are not connected at the same time currently as they are still both masters.
I would like to set one up as the slave and connect them in a Dual Boot. 

Which one should be the master? I figure this makes a difference. I assume that the Ubuntu drive should be master since it has the Grub loader.
I don't care if the OS's can see the other drive or not just that they can be dual booted without opening the PC and disconnecting them.
It would probably be better that Windows can't see the Drive as this would change the drive letters and screw things up. So this too is an objective.

If someone could tell me the way to do this without loosing any data  I would be very appreciative.

---

### Post by Herman on 2007-02-02
Hi SonicSteve,
I think you' re right, it probably will be a little easier to have the Ubuntu disk plugged in as master, and plug the Windows drive in as slave.
All you will have to do then is add an operating system entry to your Grub boot menu.
You can do that by adding something like this to your /boot/grub/menu.lst file in Ubuntu,
```
## ## End Default Options ##
                                                            
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot
                                                            
title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot
                                                            
title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot
                                                            
[COLOR=Red] ### END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR]
                                                            
[COLOR=Red]# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
rootnoverify        (hd1,0)
savedefault
makeactive
chainloader    +1[/COLOR] 
```You can probably just copy and paste what I have in red here right to the bottom of yours and it'll probably be fine.
If not, let me know and we'll fix it, but if I guessed right, it should work.

If you aren't sure about where to find your /boot/grub/menu.lst file and how to open it and edit it, just click on my third sig link and that should have all the info you'll need.

Regards, Herman :)

---

### Post by SonicSteve on 2007-02-03
No go Herman,
I did what I think I'm supposed to do and Ubuntu still loads up nicely, but when I try the windows option it just says "starting up..." and does nothing. 
I'll post my menu.lst file and double check my drive numbering.

# ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
rootnoverify        (hd1,0)
savedefault
makeactive
chainloader    +1


OK so the maxtor is 00 and the western digital is 01

I made a change to reflect that in the rootnoverify line above,
I'll post if it works or not

---

### Post by SonicSteve on 2007-02-03
Hehehe,
I forgot it's drive # then partition,
I got the "invalid device requested" message.
So then what do I need to do?

---

### Post by SonicSteve on 2007-02-03
I'm going to talk out loud for a minute here,
Is it not loading because;
1. the grub menu is wrong
2. now that windows is the slave it has become drive D not C and hence can't boot. I can change this back by swapping the drive settings but... I don't know if this is true since Windows can't even read a single bit of EXT3. I think that it will see itself as drive C if it can't read the from the other Hard drive.

Do you know?

What drive letter does your windows partion see itself as?

---

### Post by confused57 on 2007-02-03
> **SonicSteve said:**
> I'm going to talk out loud for a minute here,
Is it not loading because;
1. the grub menu is wrong
2. now that windows is the slave it has become drive D not C and hence can't boot. I can change this back by swapping the drive settings but... I don't know if this is true since Windows can't even read a single bit of EXT3. I think that it will see itself as drive C if it can't read the from the other Hard drive.

Do you know?

What drive letter does your windows partion see itself as?
Your Windows entry should probably be something similar to this:

title              Windows XP
rootnoverify   (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

The mapping commands fool Windows into thinking it's the first OS booted to...this works if Ubuntu is master & Windows is set up as slave.

Added:   Herman, I knew it was an oversight on your part & thought I'd offer some assistance, since you weren't active on the forums at the time...most of what I know about bootloaders & grub, I learned from your site & forum posts.

---

### Post by SonicSteve on 2007-02-03
AWESOME!!!
That did it, the community here with Ubuntu is one thing that Windows just can't even come close to.  I've never seen a forum in all my days where you can get this kind of help for windows. 

The more I see of Ubuntu the more it impresses me.

---

### Post by Herman on 2007-02-03
Thanks, confused57! :)
Silly me I left out the vital map commands and went to sleep later on.
Lucky I have friends backing me up!  :KS
Sorry there, SonicSteve! (I better have an extra cup of coffee this morning).
He-he, :)
Thanks again, confused57.
Regards, Herman

---

### Post by SonicSteve on 2007-02-03
> **Herman said:**
> Thanks, confused57! :)
Silly me I left out the vital map commands and went to sleep later on.
Lucky I have friends backing me up!  :KS
Sorry there, SonicSteve! (I better have an extra cup of coffee this morning).
He-he, :)
Thanks again, confused57.
Regards, Herman

No prob,
In the end it all turned out well, I'm now booting perfectly between the OS's. I learned a bit more about Ubuntu in the process, and no data loss. All in all perfect.

---

