---
title: "Installing 10.10 64bit on a Dell Poweredge SC420"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by jarofgreen on 2010-11-05
I am having problems with this.

The live CD doesn't detect my HD's - the install window to partition disks just comes up empty.

The alternate CD does detect the disks but gets to 73% installing the base system and hangs. I've seen other threads with this problem. Some say to try removing the network cable, and that had no effect.

Tried the alternative CD on a USB stick and that wouldn't even boot.

Any ideas?

Thanks,
James

---

### Post by yeats on 2010-11-05
> The alternate CD does detect the disks but gets to 73% installing the base system and hangs. I've seen other threads with this problem. Some say to try removing the network cable, and that had no effect.

You can do Alt-F4 during installation with the alternate CD, which will show log output.  When it hangs, do Alt-F4 and see what's at the bottom of the screen.

---

### Post by jarofgreen on 2010-11-05
"Updating the list of available packages" the screen says
The last log messages are to do with writing the new sources list.
It has 4 warnings "Skipping nonexistent file" with paths 
"/media/cdrom/dists/maverick/main/binary-amd64/Packages"
"/media/cdrom/dists/maverick/main/debian-installer/binary-amd64/Packages"
"/media/cdrom/dists/maverick/restricted/binary-amd64/Packages"
"/media/cdrom/dists/maverick/restricted/debian-installer/binary-amd64/Packages"

I am currently downloading 10.04.1 Alternative CD 64bit to try installing that :-(

---

### Post by jarofgreen on 2010-11-05
This is the thread that suggested removing networking and USB [http://ubuntuforums.org/showthread.php?t=1593454](http://ubuntuforums.org/showthread.php?t=1593454)

---

### Post by jarofgreen on 2010-11-05
Installing 10.04.1 Alternative CD didn't work
"Please insert the disc labeled Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release (xxxxx"
Got the same problem others seem to have had.

However, installing it from USB worked.

I now have 10.04 64-bit installed, and tomorrow I will try updating it to 10.10 from within Ubuntu.

It's a good thing I like using Linux so much, because this install has been terrible :-(

---

### Post by jarofgreen on 2010-11-06
That seemed to work .... :-)

---

### Post by MadsR on 2010-11-06
I am having the exact same problem on nothing but standard (Asrock, Intel, ATI) hardware.Is  this bug, which it clearly is, since we are quite a few people experiencing this, escalated to developers? Or, how is this reported?

/Mads

---

### Post by Ahser on 2010-11-27
I had a similar problem here, installation hangs at 73% "Updating the list of available packages". The solution for me was to not specify that I have a localized keyboard when I install. I tried with both norwegian and swedish keyboards. Since I'm installing a headless server it doesn't really matter to me so I just went with "USA" keyboard (and the other choises), then it worked... This took me a few hours and reinstalls to figure out though, so this bug should really be fixed...

---

### Post by WoraZ on 2011-01-01
I had it too. Tried reinstall few times with different options, but that doesn't worked. Then i found that users have problems when they read CD with NEC cd/dvd drives, so i changed it to TSCorp dvd drive and no hang up on 73%.

---

### Post by shadow on 2011-01-07
Had exactly the same annoying issue yesterday trying a fresh server install. Stuck at 73%. Managed to find an old cdrom and swapped that out and luckily managed my way through it though.

---

