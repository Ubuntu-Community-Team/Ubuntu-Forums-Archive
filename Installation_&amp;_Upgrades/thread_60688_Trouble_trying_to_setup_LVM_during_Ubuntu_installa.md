---
title: "Trouble trying to setup LVM during Ubuntu installation"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by mchatel on 2005-08-28
Hey all.
I was wondering if anyone else came across this, or knows how to help me.

I was installing Ubuntu on my system again (trying to test my backup/restore capability, in case I ever have to restore my system - it worked), but this time, I was thinking of trying to setup LVM instead.

I understand the concept behind LVM, but I ran into trouble during installation.

I marked a bunch of my disk space (about 30GB), to set aside for LVM use (doing this right in the Ubuntu installation).  I then went into the LVM setup from the partition setup...  and chose to create a LVM volume group.

I was then presented with a disk partition where I would be creating my groups.  Only one choice was displayed on the screen, and as expected, it was the partition I had set aside for LVM use.  However...

The installer seems to want me to pick it, before I hit continue, but I can't.  I only can pick the "Go back" and "Continue" options.  I can get the cursor to sit at my disk device, for selection, but I can't select it.  None of the keys seem to highlight it, or tick it for use, in anyway.  If I pick "Continue", Ubuntu tells me I have to pick a device.  

Is this a bug in the LVM setup menu?  Or is there something I'm totally missing here? 

In the meanwhile, I just stuck to my old method, of setting up partitions to install Ubuntu again.

Any info would be appreciated,

---

### Post by AndrewStout on 2005-08-30
[QUOTE=mchatel]
The installer seems to want me to pick it, before I hit continue, but I can't.  I only can pick the "Go back" and "Continue" options.  I can get the cursor to sit at my disk device, for selection, but I can't select it.  None of the keys seem to highlight it, or tick it for use, in anyway.  If I pick "Continue", Ubuntu tells me I have to pick a device.  

Is this a bug in the LVM setup menu?  Or is there something I'm totally missing here? 
[/QUOTE]

I was also puzzled by this.  I wound up semi-systematically trying keys until I found the one that toggles selection.  It's the space bar.

(woulda been nice if that had been made obvious.  now I'm having a problem where it appears that LVM is swallowing 23 GB of my 340 GB volume group...see thread "LVM eats HOW MUCH?")

--A.

---

### Post by Buffalo Soldier on 2005-08-30
I did this some time ago... forgotten the exact steps. I believe you have to create a Volume Group first then Logical Volume.

Hope this [link](http://www.tldp.org/HOWTO/LVM-HOWTO/anatomy.html) and this can help you:
```
 20Gb hda1 ntfs /media/windows
  5Gb hda2 vfat /media/dos
256Mb hda3 ext3 /boot
 55Gb hda4 lvm (VG - volume group)
      -> 40Gb /home (LV - logical volume)
      -> 15Gb / (LV - logical volume)
```

---

### Post by mchatel on 2005-08-30
The Spacebar...?  Hmm...  I thought I would have tried that, to select the menu selection, but it's hard to say.  Maybe I missed trying such an obvious choice...  lol.  If I didn't try it, I tried every other key.  lol.  

I agree, that particular screen needs some more intuitive commands.

I would really like to try LVM, so I will possibly re-setup my system again, sometime this week, and give this a try.  I like how easy it is to backup an Ubuntu/Linux system.  :D  

So, I can play with it all I want.

I will be sure to check out your other thread about LVM taking lots of space.

Mike

---

### Post by AndrewStout on 2005-09-01
[QUOTE=mchatel]The Spacebar...?  Hmm...  I thought I would have tried that, to select the menu selection, but it's hard to say.  Maybe I missed trying such an obvious choice...  lol.  If I didn't try it, I tried every other key.  lol.  
[/QUOTE]

It took me an embarrassingly long time to think to try the space bar.  [shrug]

--A.

---

