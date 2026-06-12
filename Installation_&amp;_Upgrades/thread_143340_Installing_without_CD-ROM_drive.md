---
title: "Installing without CD-ROM drive"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by t0maz on 2006-03-12
Dear Ubuntu Lovers,

I want to install Ubuntu (or Kubuntu, I'm not quite sure yet) on my brother's laptop. But there's a problem: the laptop does not have a CD-ROM player (it's broken) and I can't purchase a new one, it would just cost too much.

I have the ability to put the hard disk drive in an external casing and connect it to my own computer. That way I can access the disk and perhaps put a filesystem on it already or some installation files.

I am looking for ways to install Ubuntu without a CD-ROM drive, at all. For example booting with a floppy, accessing some files on the hard disk, or perhaps start an installation from a floppy and installing it completely from the internet.

Any tips are appreciated.

---

### Post by simon_is_learning on 2006-03-12
If you take out the harddrive as you mentioned. 
You can do a server install, then put it back.

Try to boot.... 
If it works:
Then install what ever you want from the repositories.

---

### Post by t0maz on 2006-03-12
Thank you very much for your suggestion. I'm not (yet) very experienced with Ubuntu, but is server install just a minimal install? Also, is there after that a way to go from the server install to a full install and will all the hardware detection work correctly (as the first install would then be on a different computer than than where it will be running up)?

---

### Post by Klaidas on 2006-03-12
[QUOTE=simon_is_learning]If you take out the harddrive as you mentioned. 
You can do a server install, then put it back.

Try to boot.... 
If it works:
Then install what ever you want from the repositories.[/QUOTE]

Why install the server only? If there's a possibility to install without CD-ROM, why not install the full system? :-k

---

### Post by t0maz on 2006-03-13
What I am most concerned about is the hardware detection and configuration. At what stage is this happening? If the hardware detection is done at every boot, then there's no problem and everything will work fine. But if the detection and configuration is done only at installation time (or both at installation and only detection at boot) then it won't work as I will be installing on another machine.

And what about the hard disk in grub/lilo? If I install it in the external casing, which most probably will be sda. If I then put it back into the laptop, it will be hda, so will it be able to boot then?

---

