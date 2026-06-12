---
title: "Dual boot xp problem"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by steigerwald on 2008-04-17
So the other day I updated to 8.04 beta and now for some reason when I try to load XP, it asks for a disk check, which goes smoothly, then i just get a screen with the default background, and no login interface. what gives?

Tried asking on IRC but no solutions were provided, also I could not find any relevant posts to my problem. Hopefully someone knows whats up. Thanks guys.

---

### Post by Herman on 2008-04-17
I can't imagine how an update in Ubuntu can affect another operating system in another partition. 
Maybe it's just a co-incidence that you received an update in your 8.04 system and then you noticed a problem in Windows XP.

In any case (whatever the reason your XP troubles might be), if it  it "asks for a disk check" it seems as if you may have a file system problem of some kind in Windows XP which the regular file system check before boot-up isn't able to fix.
If you have a Windows Installation CD, you can boot to a Recovery Console, and run 'CHKDSK C: /R', and that should fix your file system in Windows.
Maybe that will fix it.

Other than that, "a screen with the default background, and no login interface", could mean your copy of Windows XP has timed out.
Windows XP is a proprietary operating system and to prevent it from being illegally copied and used for free, it contains software 'booby traps', and one of those is a count-down timer.
The count-down timer runs for a number of days, like maybe about 30, 60 or 90 days, (I don't know, I'm just guessing), and allows Windows to be evaluated or used for test purposes.
If you haven't registered your version of Windows XP by the time the timer runs out then 'wham!', without any warning it will boot someday with just a  Windows logo and no login field.

It could be that you have a perfectly legal copy of Windows XP, but  some other software problem in Windows has started the count-down timer by accident without you knowing about it. It just runs secretly in the background, you have no way of knowing if it's running. 
Copying or 'Ghosting' your Windows partition and a glitch or error in re-installing from the backup it is one possible way to start the timer without your knowledge even in a perfectly legal copy of Windows XP. I imagine a virus or malware might be able to do that too, I don't know, but maybe.
There's no way your Ubuntu upgrade could have affected your Windows XP in any way that I can think of.

If you believe your copy of Windows XP is valid then the best thing to do would be to contact Microsoft and get help from them.

The best thing to do is avoid the use of operating systems that contain booby traps and move all your data into Ubuntu and just use Ubuntu.

Regards, Herman :)

---

