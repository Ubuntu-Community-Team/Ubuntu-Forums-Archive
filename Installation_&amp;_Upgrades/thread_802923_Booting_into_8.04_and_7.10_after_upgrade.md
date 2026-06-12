---
title: "Booting into 8.04 and 7.10 after upgrade"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by puzzledinmn on 2008-05-21
I upgraded to 8.04 and now I boot into a downlevel 7.10 desktop about a third of the time.  The problem may have something to do with my NVidia 8400GS display adapter, which is why I posted there first.  Any suggestions on how to stop the 7.10 boots?

[http://ubuntuforums.org/showthread.php?t=801013&page=2](http://ubuntuforums.org/showthread.php?t=801013&page=2)

---

### Post by overdrank on 2008-05-21
> **puzzledinmn said:**
> I upgraded to 8.04 and now I boot into a downlevel 7.10 desktop about a third of the time.  The problem may have something to do with my NVidia 8400GS display adapter, which is why I posted there first.  Any suggestions on how to stop the 7.10 boots?

[http://ubuntuforums.org/showthread.php?t=801013&page=2](http://ubuntuforums.org/showthread.php?t=801013&page=2)

Hi and when you updated did you leave the grub intact? If so then this why I think you are still booting into your 7.10. Have you tried and select the other options from the grub loading or do you see the grub loading?

---

### Post by puzzledinmn on 2008-05-21
I did not alter GRUB.  I assumed it still pointed to a single Ubuntu boot point.  Each time I boot I select the first selection in GRUB which says 7.10 but I assume it should be pointing at the 8.04 boot sector.  There is no option in GRUB for 8.04. I am curious on why 7.10 is still around.

---

### Post by zvacet on 2008-05-22
Go to the synaptic and find linux-image package and delete them all exept 2.6.24 ( I think you have two of them).

```
sudo update-grub
```

---

### Post by puzzledinmn on 2008-05-22
I did indeed have 2 linux-images.  I deleted the older one and now my 8.04 Ubuntu does not have a network connection. (I am sending this from 7.10)  I noticed that the /boot/grub/menu.lst is different for the respective boots.  IE I see 8.04 in the 8.04 menu even though it never shows up on my screen.

Today I remembered that I have a clone backup disk that would still contain 7.10 although it is not listed in the grub menu so I don't think that came into play.

---

### Post by puzzledinmn on 2008-05-24
I figured out that the 8.04 upgrade got applied to my clone disk.  It appears I may have been booting into the clone for a while.  Grub bug??  The upgrade went ok after I deleted the clone Ubuntu partition with Vista (don't know how to do it with Ubuntu). I have two linux-image versions listed on grub now but I think I will just leave the old one since it doesn't bother anything.

---

