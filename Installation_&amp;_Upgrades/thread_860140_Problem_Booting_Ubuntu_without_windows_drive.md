---
title: "Problem Booting Ubuntu without windows drive"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by trebnoj on 2008-07-15
Hello Everyone!  I've been using Ubuntu for a couple of months now and I really like it, and I've been trying to keep a low profile on these boards but I've finally come across a problem I can't seem to solve on my own:

Ok, so when I first installed ubuntu (8.04, BTW), I had windows XP installed on my primary hard drive, and ubuntu got put onto the secondary (just standard master/slave IDE setup, both 80GB single partitions).  Recently I had to replace the motherboard, so I decided just to take things one step at a time and just make sure Ubuntu worked before I attempted to get both hard drives working.  When I tried to do this, however, I realized that the only way I could get either drive to boot was to have both drives in place. (the fact that my windows drive gives me a grub error 21 is hopefully unrelated, and I'm just taking this one disaster at a time)  It seems that when ubuntu installed itself it somehow requires the windows drive in order to boot.

Anyway, so if my theory here is correct, how do I "unconnect" the ubuntu install from my windows drive?  Somehow there must be a way to make them more independent, correct?

---

### Post by run1206 on 2008-07-15
wassup trebnoj,
Ubuntu uses a feature called Grub to mount either your Windows or Linux hard drives during its boot process.  If you're getting a grub error, maybe grub wasn't installed properly or was deleted somehow.  There's a tutorial in the weekly tutorial section for reinstalling Grub. (i'll try to find the link shortly...) 
If somehow you are able to access you grub files through your menu.lst file 
```

cd /boot/grub
sudo gedit menu.lst 
```
from there shows you what partition goes to which drive.  I'm not quite sure if you can run each drive seperately though.

---

### Post by prshah on 2008-07-15
> **trebnoj said:**
> 

Anyway, so if my theory here is correct, how do I "unconnect" the ubuntu install from my windows drive?  Somehow there must be a way to make them more independent, correct?

You would have install the GRUB (Grand Unified Boot loader) onto the Windows drive. GRUB, during startup, looks for information in the ubuntu partition. If it cannot find the ubuntu partition _in the same place_ as when setup, it cannot find required information and thus BOOM!

In the same way, Ubuntu cannot load because GRUB cannot start it up.

However, it's easy to fix! You need to download a "Super GRUB" disk, and use that to build a new GRUB on your ubuntu drive. Will take only a few seconds, and there's a good tutorial on the site as well!

---

### Post by falcon61102 on 2008-07-15
Yeah, like run1206 said, your GRUB is what boots up your operating systems and it is dependent on what is listed in menu.lst and device.map.  You can either edit those files or if necessary, reinstall the GRUB and you should be able to have completely seperate boot systems.  For instance, the way my laptop is set up right now, I have a Dual boot Vista/Ubuntu but then I also have Ubuntu installed on a USB hard drive so that I can take it to work and play with it there.  To get the USB HD to boot on both my laptop and independantly took some editing to those two files but it's not hard.

---

### Post by run1206 on 2008-07-15
^^i'm the same way, i dual boot XP Home and Ubuntu on my laptop.
btw, here's the link for reinstalling Grub from a liveCD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
K.Mandla runs weekly tutorials and brought this one up a few weeks ago, hope this helps as well.

edit: also, here's a link for editing your menu.lst file for your partitions.
[http://ubuntuforums.org/showthread.php?t=818177&highlight=editing+menu.lst](http://ubuntuforums.org/showthread.php?t=818177&highlight=editing+menu.lst)

---

