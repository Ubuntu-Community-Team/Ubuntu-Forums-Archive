---
title: "booting windows mucks up grub, help"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by hessiess on 2007-05-05
i asked thiis in biginer chat and haven't got any reply's recently

im trying to dual boot xp and ubuntu.

my computer boots fine until i start windows xp. then if i restart the computer grub dosant work and i haft to boot of the live cd. so windows is oviasly doing something to grub, but i haven't got a clue what.

its a hp pavilion dv2000. 2 gig ram 1.66 dual core.

i need to get this solved by Tuesday.

---

### Post by joiningtheherd on 2007-05-05
Please post the output of:
```
cat /boot/grub/menu.lst
```

It should include a section similar to:
```

title                  Windows XP Home Edition
root                 (hd0,0)
makeactive
chainloader     +1

```
Where (hd0,0) would be replaced with the partition for windows.

This is the entry which loads Windows.  Windows should be completely unaware of Grub and it's machinations and thus have no problem with Grub, and give Grub no problems.  Just Google'ing for this kind of problem should produce many in depth guides pertaining to all aspects of this setup.  

As an aside, in future posts be more meticulous with your grammar and spelling.  It will encourage more people to pay attention to your posts.

---

### Post by hessiess on 2007-05-05
im deslexic.

il try that, thx

---

### Post by cookfromfrozen on 2007-05-06
> **joiningtheherd said:**
> As an aside, in future posts be more meticulous with your grammar and spelling.  It will encourage more people to pay attention to your posts.
I understood his post just fine.  The lack of information is a different issue, but what was there I understood.

As an aside, not being arrogant on forums encourages more people to pay attention to your posts.

---

### Post by bulldog on 2007-05-06
> **hessiess said:**
> i asked thiis in biginer chat and haven't got any reply's recently

im trying to dual boot xp and ubuntu.

my computer boots fine until i start windows xp. then if i restart the computer grub dosant work and i haft to boot of the live cd. so windows is oviasly doing something to grub, but i haven't got a clue what.

its a hp pavilion dv2000. 2 gig ram 1.66 dual core.

i need to get this solved by Tuesday.

When you restart from your windows session,and GRUB fails,do you get any error message?
And if you turn the computer off and on again,not using windows,will it boot ubuntu?

---

### Post by hessiess on 2007-05-06
it goes hp start screen>flashes "grub" then imedatly reboots and repets this until i turn it off or put in the live cd. there are no error messages.

if i reinstall grub using the super grub disk it works until i boot windows and then goes back to infanatly rebooting. if i fix grub and boot ubuntu then restart grub works perfectly.

this thread describes a simaler problem...

[http://ubuntuforums.org/showthread.php?t=428332&highlight=grub]("http://ubuntuforums.org/showthread.php?t=428332&highlight=grub")

im currently booting with the super grub disk

---

### Post by bulldog on 2007-05-06
Yes,I know of that tread,but unfortunately we couldn't solve it either.
Can't imagine windows is corrupting the MBR itself.

But is there any anti virus program running in windows which could make this happen?
I should look in that direction,there must be a program running on windows,which messes up your MBR.
Otherwise I haven't a clue.

---

### Post by hessiess on 2007-05-06
im ruining nortan internet scuraty 2006. i cant uninstall it to see if this is the problem becose i have no way of reinstalling it, the computer is oned by the lea, but its mine welst im at this school. ubuntu wont recognise most of my hardware, including the wireless adapter. so no windows is not a option until this is sorted.
it is on the schools novell network, although i never use it becose its just so slow 

i don't want grumpy IT tecknitions asking why i uninstantiated it, :lolflag:

---

### Post by hessiess on 2007-05-07
now windows wont log on propaly, it makes a tempery acount?. help

---

### Post by MobileDev on 2007-09-10
I had the same problem on a system not much different from yours, hessiess. I chucked the first hard drive and replaced it with a Western Digital 40 GB. Then I installed Windows XP and Ubuntu. Everything worked just fine. Of course, it was working fine when I did it the first time, ***before*** installing Norton Internet Security 2006. Out of curiosity, I wanted to know if this version was just as useless as all the other security products from Norton. It was. :lolflag:  If you're looking for a security software solution that actually does it's job, grab a copy of NOD32 from [http://www.eset.com/](http://www.eset.com/)   It doesn't do anything to GRUB. It's also extremely fast. It you don't want to pay for this, then I suggest chucking Windows altogether. Even if it's not technically your computer (that's just what *I* would do). Hope this helped!

--Click! "submit reply"--

As an interesting aside, I usually blow up defective or broken hardware with fireworks and model rocket kits :guitar:

---

