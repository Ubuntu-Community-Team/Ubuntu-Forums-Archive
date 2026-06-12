---
title: "Ubuntu Server not recognizing hard drive"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Lindenk on 2012-03-10
I'm attempting to install Ubuntu server 11.10 on my old computer (specs below) and during installation it doesn't find my hard drive then prompts me to select a driver. I've tried every driver on the list and none of them work and I've searched the net for quite awhile and found nothing. Honestly I didn't even know internal hard drives needed drivers to begin with.

The odd thing is I use to have windows XP on it and, after I realized that any version of linux I tried to install failed to find a hard drive, I booted up an xp install disk. It found the hard drive...so I'm assuming windows xp has the driver built in but no where have I found the driver available for download...

I know this is more of a hardware issue but does anyone know where I can get this driver or if I'm doing something wrong?

Specs -
- ST380011A Seagate Barracuda 7200.7 hard disk 60gb (or 80, I don't remember)
- sr1803wm HP motherboard
- Intel Celeron D processor

Also I just realized I could have posted this a better section...sorry

---

### Post by darkod on 2012-03-10
Is that a sata or ide disk?

You seem to be doing the correct thing. Also, unless you use some rare model of raid adapter, in most cases it should detect a hdd connected to a motherboard without problems.

If we are talking about sata disk, go into BIOS and see if the sata mode is IDE (probably, otherwise XP can't see it), or AHCI. You better set it to AHCI for further use. Then try it connected to the same port, and then to another port.

If it's ide disk, see if you can try it in another port, but usually there is only one ide port. Check the jumpers on the hdd, with ide disks the position of jumpers matters.

I know the XP can see the disk so it should be fine, but check all these things again, just to make sure.

Has the disk been used in raid earlier maybe? In that case it might have raid meta data leftovers.

---

### Post by Lindenk on 2012-03-11
Well I feel terribly dumb... apparently I never configured the jumper on the drive to make it explicitly master. Thanks for the help though, I probably wouldn't have noticed that it wasn't set as master if I didn't enter bios.

---

