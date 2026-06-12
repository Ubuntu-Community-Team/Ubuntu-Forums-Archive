---
title: "Cannot Get past boot screen with edgy"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by alex77 on 2007-03-05
Hiya all,

I am trying to install edgy so that it will dual boot with windows xp

I have Asus p5w dh deluxe mobo and core 2 duo e6300- not sure if that makes a difference

My problem is this, when I boot from the live cd, it works fine- up to the start screen with all the options. However, when i choose to start using ubuntu the screen changes to the boot screen fine (with the moving orange bar) but then does nothing from then on. All that happens is that the orange bar goes back and forth forever.

What should i do/change to get ubuntu to boot from the cd? Are there any alternatives?

Thanks :)

---

### Post by Kateikyoushi on 2007-03-05
What uis your videocard ? I guess something newer, then try what this post suggests. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

You could also try the alternate install cd which installs in text mode.

---

### Post by alex77 on 2007-03-05
Thanks for that link, would never have thought my vid card would be the problem.

I have twin x1600s so i'm pretty sure that soulution will sort me out :)

Also, thanks for the incredibly quick reply. Will post back about if this works later (am at uni atm 'working')


Thanks!

---

### Post by alex77 on 2007-03-05
hmmmm. no joy there...

However, using the quiet boot option, i think I'm getting to the root of the problem

First off, the boot was hanging because i had the asus remote control receiver plugged in, so out that came, but now the boot goes so far and then sits at a command prompt, occasionally telling me that it has "lost interrupt".

Should i fiddle around with this some more, or would i be faster to use the alternate install cd? would there be any difference?

---

### Post by alex77 on 2007-03-05
Using quiet boot turned off, booting gets to a command prompt (initramfs)

Also, apparently /bin/sh cant access tty; job control turned off

what does this mean? And what is busy box V1.1.3?

Busy Box v.1.1.3 ( Debian 1:1.1.3-2unbuntu3 ) Built-in shell (ash)
Enter 'Help' for list of built in commands
/bin/sh : cant access tty;job control turned off
(initramfs)_

---

### Post by Dart31 on 2007-03-05
Alex77,
I had some of the same issues you had and I ended up using the Alternative CD version of Ubuntu and everything went fine. 
I would say this is what you should try and then post if you are still having troubles and what they are.  

Hope this helps,
Dart

---

### Post by alex77 on 2007-03-20
Well, sort of solved I guess.

Turns out Ubuntu doesn't like JMicron, and wasnt recognising my CD drive. Seems strange as this is where it booted from but hey. Sadly if i disable JMicron i disable my cd drive, and i havent got the cash to replace it with a sata one.

Any other suggestions? Is there any sort of workaround I can try? This problem occurs with both the desktop and alternative CD

Thanks

---

### Post by SPENGLER on 2007-03-20
just posted my findings on another thread [HERE]("http://ubuntuforums.org/showthread.php?p=2327235#post2327235")

---

### Post by alex77 on 2007-03-20
Have decided to try the 6.06 version of ubuntu instead, maybe this is just an edgy problem. Downloading now.

Is it easy enough to upgrade to edgy from within 6.06? And will this JMicron problem go away?

---

### Post by alex77 on 2007-03-20
Hmmm, might give that a go if i can't get dapper to run.

Pretty certain its a problem with JMicron- quite a few other folk on this forum are having the same problem, but no fixes or workarounds to be found.

I know it can be done just about in feisty: [URL="http://ubuntuforums.org/showthread.php?t=373662&highlight=feisty+p5w"]http://ubuntuforums.org/showthread.php?t=373662&highlight=feisty+p5w
[/URL]
but I dont really want to use an alpha version as my day to day system.

---

### Post by Kateikyoushi on 2007-03-20
Well you could try the livecd of feisty, and it is just a month till the final is out.

---

### Post by alex77 on 2007-03-20
Sorry for my ignorance here, but if i install feisty now, will i be able to upgrade fairly easy in a month time? Or will i have to reformat etc? I'm a bit of a n00b at this...

---

### Post by alex77 on 2007-03-21
Think a solution may have been provided by a nice chap called temis01:

[http://ubuntuforums.org/showthread.php?p=2330689#post2330689](http://ubuntuforums.org/showthread.php?p=2330689#post2330689)

---

### Post by alex77 on 2007-03-22
Yep, that solved it!

Ubuntu installed ok! Sadly i now have a new problem, the GUI wont load because it hates my graphics card (x1600xt), but this is a problem for another thread i guess...

Thanks to everyone who helped me out, hopefully should have ubuntu goodness soon!

---

### Post by rayj00 on 2007-03-22
Busy box is a linux type utility that allows access to the basic linux commands.

I have busybox in my DSL modem!!! (factory installed).......

---

