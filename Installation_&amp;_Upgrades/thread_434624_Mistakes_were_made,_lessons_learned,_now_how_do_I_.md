---
title: "Mistakes were made, lessons learned, now how do I fix it?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by TransplantedCanuck on 2007-05-06
Hello, 

First some background to explain why some options aren't possible. I'm from Canada, but I'm living in Germany right now. I've been planning to install Ubuntu as soon as I can get my own computer sent over from Canada, because there is too much important stuff relying on my girlfriend's computer to risk making a mistake. That said, my mom back in Canada wanted to install Ubuntu (Hates-Gates Syndrome), and I thought that sounded great.

However, that means I'm walking her through these things by phone, as she reads out the screens. And me, having only a computer (windows/networking) semi-savvy guy's intuition as to what should go where. Unplugging drives and changing jumpers are not something I want to introduce my mother to over the phone. 

Her computer has a new(er) harddrive that has her current XP installation on it, and we'd prefer to keep it around until we've got all her stuff transfered over and working, and we know she likes Ubuntu and can work with it, etc. 

We have an old(very old) nicely blank harddrive that happens to already be hooked up to her computer (long story). The first HD is IDE 1, the second is IDE 2, CD is also on #2. Being used to windows, I just figured throw Ubuntu on the second HD and all should be well. I didn't know there would be a different boot loader and all that. Oops, next time read more eh? (lesson 1).

So during the install, Ubuntu was properly installed on the second drive, and it knows that windows is on the first drive. Great I thought, let's reboot and then I just have to get her on the internet and her email working and I can go to bed. NOPE.

GRUB loading stage 1.5
GRUB loading, please wait...

No error message given to me.

And thats where we are now. After doing some searching I realize that installing a dual boot and a dual boot with 2 HDs is a bit trickier. Of course, those threads help people who were much smarter than I was (I usually would have explored all the options during the install and caught wind of something like this, but my mom didn't know what to look for (no instinct). ).

So now we're at the point where: Ubuntu is nicely installed on the second HD, Windows on the first and GRUB is grumpy. 

So, I'm assuming the problem is GRUB isn't in the right place? Or else the harddrive configuration needs to be changed up? Or... ?

And secondly, whats the easiest way to talk a 50 year old woman (she's got courage to try stuff, and no fear of losing everything if she must) through fixing this problem. Re-install GRUB? Re-install Ubuntu and change settings? Wipe out Windows with a Ubuntu install? Install Ubuntu on the first HD with that partition adjustment thingy where it puts itself into the freespace?

We're willing to try pretty much anything, and any help would be appreciated. 

Cheers

---

### Post by TransplantedCanuck on 2007-05-06
bump, anyone, at least able to point me in the right direction to fix it?

---

### Post by bulldog on 2007-05-06
Well,we can try to help you,but we need a little more info.
First she needs to fire up the ubuntu live cd,and perform in a terminal```
sudo fdisk -l
``` it's a lowercase L,not a one.
Post the output to the forum,so we know how your hdd's are partitioned.

If this is looking promising,we need some additional information.

---

### Post by TransplantedCanuck on 2007-05-06
Aight, thx. Will post it soon as I get the info from her.

---

### Post by bulldog on 2007-05-06
Well we can do it with you as an intermediate,but maybe she can post it to the forum?
We'll be very gentle and friendly to her.:) 
But if you prefer to post it your self,it's okay.

---

