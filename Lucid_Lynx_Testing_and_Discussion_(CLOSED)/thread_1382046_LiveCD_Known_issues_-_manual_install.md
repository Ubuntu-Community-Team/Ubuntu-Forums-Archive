---
title: "LiveCD Known issues - manual install"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-01-15
In the [Known issues]("http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues"):

> Manual partitioning fails in the graphical installer due to a bug in ubiquity: you can select existing partitions to use as targets for installation, but you can neither create new partitions **nor delete existing partitions**. As a workaround, users can install using the alternate CDs. This issue will be resolved for Alpha 3. ([506585]("https://bugs.launchpad.net/bugs/506585"), [507012]("https://bugs.launchpad.net/bugs/507012")) 

I used the manual graphical install and selected an existed partition and was able to delete it and format it without any problems. Not sure what to make of issue.

Maybe I'm reading this all wrong. 

Anyone else use the LiveCD and manual installation?

Thanks.

---

### Post by jerrylamos on 2010-01-15
> **VMC said:**
> In the [Known issues]("http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues"): 

Anyone else use the LiveCD and manual installation?

Thanks.

I'd like to.  CD won't even boot.  The first CD screen freezes and that's it.  i845 video graphics.  See the release notes for a possible related bug..

Jerry

---

### Post by Ibidem on 2010-01-15
> **jerrylamos said:**
> I'd like to.  CD won't even boot.  The first CD screen freezes and that's it.  i845 video graphics.  See the release notes for a possible related bug..

Jerry
If I were dealing with that, I'd use the alternate CD to install (expert install if needed), reboot into either "rescue mode" on the CD or recovery mode on the hard drive, run Aptitude, and remove the Xorg Intel drivers.  These are the "official" drivers for your card, and presumably are not working correctly.   If removed, X will resort to vesa, which should be safe.

It won't let you try the Live CD, but at least you might be able to run Lucid.

---

### Post by ranch hand on 2010-01-15
> **Ibidem said:**
> If I were dealing with that, I'd use the alternate CD to install (expert install if needed), reboot into either "rescue mode" on the CD or recovery mode on the hard drive, run Aptitude, and remove the Xorg Intel drivers.  These are the "official" drivers for your card, and presumably are not working correctly.   If removed, X will resort to vesa, which should be safe.

It won't let you try the Live CD, but at least you might be able to run Lucid.
That is just an excellent suggestion.  One of those "why didn't I think of that" moments.

---

### Post by cariboo on 2010-01-15
Did you try starting in safe-graphics mode? I found the Live CD desktop wouldn't load after I installed a 9400GT in my system. Enabling safe graphics mode did the trick.

---

### Post by mc4man on 2010-01-15
> Anyone else use the LiveCD and manual installation?

Yeah and it appears the release notes are correct, though when in the partitioner it seems you are able to delete a partition(s)

Ex.
This drive - sdb, had 
karmic - primary
extended w/
lucid 
swap
In the manual partitioner was able to 'delete' all, but no new free space was created and the new lucid could only be installed to one of the 'former' partitions ( in this case sdb1

So the drive now looks as in screen, the 'former' lucid in sdb5 still exists though it has been removed from grub

---

### Post by Kevbert on 2010-01-16
Seen the unable to delete an old partition problem in Kubuntu. Instead formatted that partition and install was OK (other problems encountered elsewhere).

---

### Post by VMC on 2010-01-16
> **Kevbert said:**
> Seen the unable to delete an old partition problem in Kubuntu. Instead formatted that partition and install was OK (other problems encountered elsewhere).
I had so many problems with kubuntu ubiquity that i started using alternate. I don't like to do that because most new users will use the LiveCD, and the devs need to know why it doesn't work.

---

### Post by jerrylamos on 2010-01-16
> **VMC said:**
> I had so many problems with kubuntu ubiquity that i started using alternate. I don't like to do that because most new users will use the LiveCD, and the devs need to know why it doesn't work.

Live CD doesn't boot on this IBM ThinkCentre tower at all, i845G video graphics.  No combination of cheat codes or anything else works, it absolutely freezes as soon as "enter" is hit at the initial boot screen.

ssh doesn't work, the logs aren't posted, nothing.

There's some reference in the A2 release notes to the freeze at boot time but nothing I've been able to glean gets me past that.

This is Alpha 1 upgraded, runs O.K. so long as the boot option is "quiet splash nomodeset" and xorg.conf specifies "vesa".  The bugs have been on launchpad for weeks with logs and batchbuffer dumps so I presume the developers are working on something else.

Jerry

---

### Post by PaulInBHC on 2010-01-16
Downloaded the 0113 386 iso on Winxp and make CD with the recommended recorder. Plopped in the drive, restart. Pick english, try check CD. Black screen with white logo then nothing happens. Press esc, screen goes black, nothing works. Restart button on case. Try installing from menu, screen goes black, monitor goes off, keyboard off, fans still running, can't eject CD. Restart and go to grub...

---

### Post by VMC on 2010-01-16
> **PaulInBHC said:**
> Downloaded the 0113 386 iso on Winxp and make CD with the recommended recorder. Plopped in the drive, restart. Pick english, try check CD. Black screen with white logo then nothing happens. Press esc, screen goes black, nothing works. Restart button on case. Try installing from menu, screen goes black, monitor goes off, keyboard off, fans still running, can't eject CD. Restart and go to grub...
I had the verify problem also. Even after I removed the 'quiet' from the end of the linux line. Since I verified the burn I decided it was good. there's a another way to verify by using the md5sum and check it yourself.

On install though everything worked.

---

