---
title: "Fesity Fawn Stuck Loading at 11%"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by dutchtom on 2007-08-26
So I'm trying to do a dual boot with Vista and Ubuntu Fesity Fawn. I already have all my paritions set up and vista installed. I burned the x86 desktop ISO to cd (i tried x64 and i just get a bunch of errors after the ubuntu bootscreen on the live cd, and I have an intel x64 processor). So when i go to boot it, i click the install ubuntu  and when it loads the kernel, it just hangs on 11% forever.

Any one know why?

---

### Post by Pumalite on 2007-08-26
Do md5sum on your iso, burn at 4x, etc. If Live CD does not work, try Alternate CD. Post your specs and I might be able to give you better advise.

---

### Post by merlinus on 2007-08-26
It may be video-card related.  Have you tried Safe Video Mode?

If you are still having problems, you may need the text-based Alternate cd.

-merlin

---

### Post by Pumalite on 2007-08-26
Hey, Merlin; how are you doing? Having a blast, I bet.

---

### Post by dutchtom on 2007-08-26
I have an HP dv6000t (notebook)

100gb SATA HD
nvidia geforce go 7400
Conexant Hi-def audio
Intel Core 2 Duo 2.0 Ghz
2.0 GB ram

I tried the graphics safe mode...still hangs at 11%

---

### Post by Pumalite on 2007-08-26
Try Alternate CD as both, Merlin and I suggested: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Mark box below 'Start Download'

---

### Post by Pumalite on 2007-08-26
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by merlinus on 2007-08-26
Not trying to hijack this thread, but Pumalite, would you not agree that there should be sticky threads and how-to's for these problems that come up over and over again?

Frankly, the forum search feature is not all that great.

To whom might we write about this?

-merlin

---

### Post by Pumalite on 2007-08-26
Maybe you can write one Merlin. You sure know your way around and have enough medals on your chest. I think you should do it. Everyone would benefit from it. So, I definitely agree with you.

---

### Post by merlinus on 2007-08-26
Wanna collaborate?  You have the most amazing list of resources/links for just about everything!

That in itself, with a bit of annotation, might suffice.

And I know next-to-nothing about things like RAID, multiple hdds, cabling and such.

Wonder what the mods have to say....

-m

---

### Post by Pumalite on 2007-08-26
> **merlinus said:**
> Wanna collaborate?  You have the most amazing list of resources/links for just about everything!

That in itself, with a bit of annotation, might suffice.

And I know next-to-nothing about things like RAID, multiple hdds, cabling and such.

Wonder what the mods have to say....

-m

I'll help. You do the writing though. I'll send you everything I have.

---

### Post by dutchtom on 2007-08-26
I read that guide and I gave it a try. I used the noapic irqpoll noirqdebug command for the boot option.

That let the kernel load 100% and I got to the boot screen, then after that I just got jibbirish white letters. Completely unreadable and it was way to the left on the screen. I could type but the letters were all discombobulated. So I restarted and tried again. Again I got to the boot screen, but then the screen just stayed black for many minutes.

I never had a problem with edgy eft :( whats happening?

---

### Post by Pumalite on 2007-08-26
I just noticed you use Vista. Did you use Vista's partitioner?. Otherwise Vista will not let anything run in that computer.

---

### Post by dutchtom on 2007-08-26
I have two 50 gb partitions and I installed vista on the first partition and I shrunk the second one to create one 25gb ntfs and another 25gb unallocated space. Apparently ubuntu should recognize the unallocated space and i can adjust the size and swap partition via ubuntu installer.

---

### Post by Pumalite on 2007-08-26
The point is if you used the Vista partitioner or not. If you did not; you should start all over again. If you did, then you are all set to go.

---

### Post by dutchtom on 2007-08-26
Well...I guess I did then :P

I'm gonna try the Gutsy Gibbon Alpha...wish me luck :)

---

### Post by Pumalite on 2007-08-26
Tribe 5 is just out.

---

### Post by merlinus on 2007-08-26
Can I upgrade to Tribe 5 and keep fluxbox and xfce in addition to gnome?

I do not have the luxury of another hdd.

-merlin

---

### Post by Pumalite on 2007-08-26
(lol)

---

### Post by merlinus on 2007-08-26
Shall I take that as a "NO!!!"

:)

-merlin

---

### Post by Pumalite on 2007-08-26
> **merlinus said:**
> Shall I take that as a "NO!!!"

:)

-merlin

Hey, I'm in Tribe 4 now and is GREAT!

---

### Post by merlinus on 2007-08-26
Understood, and I am very happy for you, but....

you did not answer my questions about being able to upgrade and still keep fluxbox and xfce, which I run in addition to gnome.

Or will I have to do a fresh install?

Thanks!

-m

---

### Post by Pumalite on 2007-08-26
Are you kidding me??. Of course not. You have to do a fresh install.

---

### Post by merlinus on 2007-08-26
Thought so, but I was hoping....

Thanks!

-m

---

### Post by Pumalite on 2007-08-26
> **merlinus said:**
> Thought so, but I was hoping....

Thanks!

-m

I think you are pulling my leg!

---

### Post by merlinus on 2007-08-26
No.  I am one of those idealist/dreamers who always believes the best is yet to come.

-merlin

---

### Post by Pumalite on 2007-08-26
Me too!! The best is here! It's Tribe 5

---

### Post by dutchtom on 2007-08-27
Well, I installed the latest herd and it went smoothly. No problems at all.

And I still have my vista :)

---

### Post by Pumalite on 2007-08-27
Glad it worked for you!

---

