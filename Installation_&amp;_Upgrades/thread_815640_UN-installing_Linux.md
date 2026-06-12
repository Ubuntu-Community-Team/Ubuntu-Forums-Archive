---
title: "UN-installing Linux"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Mecharuva on 2008-06-01
Not that I don't like it, just that I don't want to use it on this machine since I have a 'guinea pig' box to mess with now.
Can I just use the partition editor on the Live CD to take the Linux '/' and 'swap' partitions and put them back together with the Windows C: drive?

---

### Post by pytheas22 on 2008-06-01
Yes, boot to the live CD, install gparted with:
```

sudo apt-get install gparted
```

and use that program to do what you need.  It should be easy, but keep in mind that partition-editing always carries a risk, so be sure to backup important data on your Windows partition.

---

### Post by Mecharuva on 2008-06-01
> **pytheas22 said:**
> Yes, boot to the live CD, install gparted with:
```

sudo apt-get install gparted
```

and use that program to do what you need.  It should be easy, but keep in mind that partition-editing always carries a risk, so be sure to backup important data on your Windows partition.

I know I'm making myself out to be a tech dumbass here but:
I've never backed up data before.  Can I back it up to my secondary hard drive?

---

### Post by IHATEDLINK on 2008-06-01
> **Mecharuva said:**
> Not that I don't like it, just that I don't want to use it on this machine since I have a 'guinea pig' box to mess with now.
Can I just use the partition editor on the Live CD to take the Linux '/' and 'swap' partitions and put them back together with the Windows C: drive?

The best way to go would be:
1.[RESTORE MBR]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")
2.Delete your Ubuntu partition and add the free space back to the windows partition using the gparted tool (Gnome Partition Editor) that comes with ubuntu live CD (System>Administration>Gnome Partition Editor)
**I REALLY DON'T ADVISE YOU TO USE GPARTED FROM YOUR HD, TRY THE LIVE CD INSTEAD.**
for more information about uninstalling go [HERE]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

For backing up data, that's easy!
Just plug-in your external drive. (It can be an USB stick, an actual USB/Firewire HD, or your iPod!)
And a desktop icon will appear, just drag n' drop the stuff you want to backup to the icon and *voilá*!  You can also use online storage like [Windows Live SkyDrive]("http://skydrive.live.com/").)

---

### Post by pytheas22 on 2008-06-01
> I've never backed up data before. Can I back it up to my secondary hard drive?

Sure, you can back it up to wherever you want.  The idea is just to have a copy somewhere as a safeguard.  If you wanted to be really fancy you would image the Windows partition and copy the whole thing somewhere else, but that's a lot of work; I would recommend just making copies of any irreplaceable files that are important to you.

Either way, the chance that something will go wrong is quite minimal--I've shrunk and enlarged partitions plenty of times and have never had any kind of problem--but it's better to be safe than sorry, as they say.

---

### Post by Mecharuva on 2008-06-01
Okay.  I'll try that.
The only  thing I'm worried about on that drive really is Windows itself.
Can't drop that D:

---

### Post by IHATEDLINK on 2008-06-01
> **Mecharuva said:**
> Okay.  I'll try that.
The only  thing I'm worried about on that drive really is Windows itself.
Can't drop that D:

Don't worry, everything should go fine. My XP installation dual-booted with fedora, freebsd, mint, ubuntu, vista and even Mac OS X! And I never had any trouble. (BTW, my favorite dual-boot was (and is) OS X ;))

---

### Post by Mecharuva on 2008-06-01
Okay I've run MBRFIX and now I'm on the Live CD.
I've formatted the Linux EXT3 and Swap partitions back to ntfs.
How do I mold them together back into the original?
Or will it do this automatically when I restart?

---

### Post by pytheas22 on 2008-06-01
Can you delete the former Linux and swap partitions and then simply expand the Windows one to take up all the space on the disk?  I think this is the approach you'd have to take.  They won't merge on their own, no.

---

### Post by Mecharuva on 2008-06-01
Oh.... Thaaaat's what I was supposed to do.
Lol, blonde moment I guess.
Okay all looks good here, back to Windows I go :P
Thanks all for your help :)

---

### Post by IHATEDLINK on 2008-06-02
> **Mecharuva said:**
> Oh.... Thaaaat's what I was supposed to do.
Lol, blonde moment I guess.
Okay all looks good here, back to Windows I go :P
Thanks all for your help :)

Glad it went well.
You can mark this thread as solved by clicking "thread tools" and then "mark as solved". so... DO IT! ;)

---

