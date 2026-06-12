---
title: "Is this even going to work? (MY IDEA THREAD SINCE STUFF BROKE)"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by SZF2001 on 2008-08-24
Alright, so I have an older laptop and I think the CD drive is starting to die on me. But it has enough life to host live sessions on stuff like GParted and others.

So I have an idea. You see, I have this USB stick that can hold either the Ubuntu .iso or the Alt-Ubuntu .iso file. I'd prefer the Alt since using the regular one slows things down.

I made a copy of the Alt CD as slowly as possible on my desktop (2x speed) and tried my luck on the laptop. No luck, sadly, the base system installs and then when it gets around to installing all the software it hangs at 6% for a long time then tells me there was an error (but isn't very specific what error)... I've been through three CDs now so I'm just going to assume it's the drive.

I have this crazy idea. If I could get something going, maybe Ubuntu 5.04, open up gparted, have my .iso thats sitting in the USB card... Well, could I make a partition and then set it to load the .iso on the next reboot so I can install Ubuntu through it? Then when it's done, could I free up the space the partition left? It kind of sounds like an OEM thing that Dell would do but I'm willing to give it a shot.

I'll clarify - the laptop doesn't read USB sticks or boxes through the BIOS, so what I'm trying to do is get this .iso off of the USB stick and into a partition so I can use that partition to install Ubuntu.

Is this all just crazy talk? School is starting soon and I'd love having Ubuntu back on the lappy since it was all just so smooth last year.

---

### Post by Catalyst2Death on 2008-08-24
you might try a network install... If its possible:
[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)

---

### Post by SZF2001 on 2008-08-24
That sounds nice but we are all wireless here. :(

I'll look into that though if all else fails. Thanks bro.

---

### Post by SZF2001 on 2008-08-24
Another way to implement the idea (and small bump)...

Maybe I could load a script into this partition? Like, whenever you load into it it first thing trips the script which is something simple like 'mount /alt-iso.iso' or something similar? Or would there be more commands involved?

---

### Post by mrsteveman1 on 2008-08-25
If all you want is to run the livecd from a usb stick you can do that easily, unpack the ISO to the stick (vfat format), rename isolinux.cfg to syslinux.cfg in the isolinux directory then move everything in it to root, and install syslinux to the drive. You may have to edit the cfg file to change /isolinux to /

It should boot right up as a liveusb, from there you can install easily.

The alternate CD will not work. The alt installer is actually just a tiny initrd resident program, and the kernel modules in the initrd lack the module for the vfat filesystem so it cannot read the packages once it boots. It could be replaced i suppose but easier to just use the livecd method.

---

