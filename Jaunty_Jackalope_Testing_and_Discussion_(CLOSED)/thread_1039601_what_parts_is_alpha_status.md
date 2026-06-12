---
title: "what parts is alpha status ??"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-01-14
I plan maybe to use Kubuntu on my laptop but what parts is alpha and what they can cause? kernel is stable 2.6.28 (kernel is most important that must be stable), kde 4.2 is rc status (this do not affect hardware if it has problems). 

Why i want to use is because 8.10 has problems with wifi card and kde 4.2 is now stable and very usable for now and i want to try out it on real hardware.

So what is these parts that is so alpha.???

---

### Post by Slug71 on 2009-01-14
Everything

---

### Post by forcecore on 2009-01-14
But kernel is stable 2.6.28 and kernel is main thing that can cause critical failures (example that intel lan cards failure with 2.6.27 rc), i do not care if some software crashes sometimes.

---

### Post by Gina on 2009-01-14
There are problems with the installer...  The installer has the possible ability to wipe you hard drive(s) and has been known to on a few systems in the past.  BEWARE!!  If you have everything properly backed up and are happy to reinstall everything then go ahead.

---

### Post by DougieFresh4U on 2009-01-14
> **forcecore said:**
> But kernel is stable 2.6.28 and kernel is main thing that can cause critical failures (example that intel lan cards failure with 2.6.27 rc), i do not care if some software crashes sometimes.

'Intel' is nothing great in Jaunty, it's actually HORRIBLE!!):P

---

### Post by Eclipse. on 2009-01-14
Your getting confused with alpha software and an alpha operating system.

Jaunty is unstable and buggy no matter what stable software is in it.

I think trying to fix your wifi problem is the best idea.

---

### Post by forcecore on 2009-01-14
> **Gina said:**
> There are problems with the installer...  The installer has the possible ability to wipe you hard drive(s) and has been known to on a few systems in the past.  BEWARE!!  If you have everything properly backed up and are happy to reinstall everything then go ahead.

Kubuntu kde 4.2 installer too ?

---

### Post by RAOF on 2009-01-14
> **forcecore said:**
> But kernel is stable 2.6.28 and kernel is main thing that can cause critical failures (example that intel lan cards failure with 2.6.27 rc), i do not care if some software crashes sometimes.

But it's the integration work & testing that's not done. Most of the software, taken individually, is either considered stable or reasonably so.  But the interactions between them aren't.  For example, / on a crypted-lvm setup is curretly broken; you get to spend some quality time at the busybox prompt :). These sort of problems should be expected.  There's no guarantee that X will come up tomorrow!

---

### Post by ronacc on 2009-01-14
If your laptop is your only computer or if you need it for serious work do not install any developement version , wait until it is released . Heed what gina says I have had developement installs take the whole drive when they were told to use only a partition and on one occasion wipe every drive on my box , the probability is low but the risk is real .

---

### Post by Slug71 on 2009-01-14
> **forcecore said:**
> Kubuntu kde 4.2 installer too ?

KDE has nothing to do with the installer.
Like Gina said, If you dont mind the possibility of doing a reinstall if something major crashes then go ahead otherwise i'd wait. There are a few threads here where people have had issues with KDE.

---

### Post by xebian on 2009-01-14
> **forcecore said:**
> 
....
Why i want to use is because 8.10 has problems with wifi card and kde 4.2 is now stable and very usable for now and i want to try out it on real hardware.

So what is these parts that is so alpha.???

What makes you think 9.04 can fix your wi-fi problem?  8.10 has 4.2 from the ppa repo if that's what you want.

---

### Post by forcecore on 2009-01-15
atleast no one has found simple fix for my wifi card yet and i hope that new kernel will fix that but thanks telling that current 9.04 releases may eliminate hdd files, now i wait until beta 1 with kernel 2.6.29.

i have lot of files on my secondary ext3 partition so i must wait.

---

### Post by chrisccoulson on 2009-01-15
In addition to what RAOF said about integration of packages - Ubuntu distributed versions of individual packages that are considered stable upstream, may be unstable and have problems completely on their own. This could be due to the packaging of the upstream code for Ubuntu being broken (package not built correctly or installed correctly, eg files missing from the package), or one of the patches that are applied to customize the upstream software for Ubuntu might cause breakage too.

---

### Post by forcecore on 2009-02-15
> **Gina said:**
> There are problems with the installer...  The installer has the possible ability to wipe you hard drive(s) and has been known to on a few systems in the past.  BEWARE!!  If you have everything properly backed up and are happy to reinstall everything then go ahead.

is that type of bug gone, can anyone confirm that?

---

### Post by ronacc on 2009-02-15
if you are concerned about bugs you should not be using ANY testing version ,alpha ,beta or even rc , they are for finding and eliminating bugs not for solving problems .

---

### Post by forcecore on 2009-02-15
> **ronacc said:**
> if you are concerned about bugs you should not be using ANY testing version ,alpha ,beta or even rc , they are for finding and eliminating bugs not for solving problems .

i am concerned just only by damaging bugs not from some plain error bug or something similar. i can report them too until i can use GUI but if only console then i do not know how to get logs, as for bugs kernel is stable and kde 4.2 too for now.

---

### Post by autocrosser on 2009-02-15
As of THIS SECOND IN TIME, Jaunty is stable for me---we can't look into the crystalball & say that Jaunty will be stable from here on--the next series of downloads could break everyones systems---until Jaunty hits final, nothing is certain.......And thats all that is stable right now:lolflag:

---

### Post by inportb on 2009-02-15
By the way, Ubuntu 9.04 will not use kernel 2.6.29 ;)

But I don't think you understand why Ubuntu 9.04 is alpha. You need to read this thread again.

---

### Post by autocrosser on 2009-02-15
> **inportb said:**
> By the way, Ubuntu 9.04 will not use kernel 2.6.29 ;)

But I don't think you understand why Ubuntu 9.04 is alpha. You need to read this thread again.

Very good point--we won't see 2.6.29 until Kooky Kangaroo ( :lolflag: ) & then it will be only a VERY short run to the final with 2.6.30 or 31

---

