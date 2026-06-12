---
title: "Kernel requires following cpu features: cmov"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wwusnobrdr on 2008-06-18
I set up Ibex on an old pentium 400 mhz machine and after doing aptitude dist-upgrade to the latest kernel and packages I get the following error on boot.
> 
kernel requires the following features not present on the cpu:
    cmov

I am guessing I may have to compile the kernel myself, but could not find much information on this message other than people getting this in their VM.  Looking forward to helping test, thanks for the help in advance.

---

### Post by psyke83 on 2008-06-18
> **wwusnobrdr said:**
> I set up Ibex on an old pentium 400 mhz machine and after doing aptitude dist-upgrade to the latest kernel and packages I get the following error on boot.


I am guessing I may have to compile the kernel myself, but could not find much information on this message other than people getting this in their VM.  Looking forward to helping test, thanks for the help in advance.

With such an old CPU you may need kernel 2.6.26-1-386.

---

### Post by wwusnobrdr on 2008-06-19
Thanks for the suggestion, I am trying to install the linux-386 package (latest 386 complete kernel) but it says there are some dependency problems.  The error I see is the restricted modules cannot install because lrm-manager is not found.  I did a locate and this file is not on my computer, will continue to troubleshoot.

EDIT:
Okay so I scp'd lrm-manager from my hardy install to intrepid and it worked.  Should I file a bug report because lrm-manager was not installed?  Thanks for the help.

---

### Post by durand on 2008-06-20
Uh, Ubuntu is really, really not suited to this kind of machine. Try puppy linux or deli linux.

---

### Post by wwusnobrdr on 2008-06-21
I realize this, i have 5 computers and this is one that I am not currently doing anything with so I decided to help test with it.  I know it would run DSL or Puppy linux, but I just wanted to see if I could help beta test, guess I should just follow your advice then...ah well.

Should I keep 'trying' to test using this machine or consider installing it on another box where it may not get as much uptime.

Edit:  With regards to my original post, I installed the linux-386 kernel package but it would not boot from it.  I can boot for the slightly older generic versions of the kernel so no biggie.

---

### Post by Gina on 2008-06-22
For old machines try Xubuntu - needs far fewer resources, particularly RAM.  You didn't say how much RAM your machine has.  I had a 400Mhz Pentium with 384MB RAM and was running Gutsy (I think I swapped to a 650MHz processor before using Hardy - not sure now).  When installing, the Alternate CD needs less memory than the Live (desktop) CD.  I think it's worth having a try with your old machine.  Personally, I love trying to get old machines working with Ubuntu :) I didn't succeed on a 300Mhz Cyrix with 32MB RAM however :lol:

---

