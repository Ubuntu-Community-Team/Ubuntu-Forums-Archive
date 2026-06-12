---
title: "Installation hangs at first boot"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by Anima on 2004-10-25
Hi

I am using a Dell Inspiron 700m Laptop, and installed ubuntu to a 2nd partition, the first partition contains window xp home. The installation didnt complete though as first stage works fine, the problem arise when it restarts and boots, everything goes fine untill its sets up libpt-1.6.3 (1.6.5-3ubuntu1). That is where it stop running and just crash/hang. 

It stops at:
"Setting up libpt-1.6.3 (1.6.5-3ubuntu1) ..."

i have try reinstalling many times and still hangs at the same part, i even try burning a new copy of the image and yet still have the same problem. 

anyone got any idea why or how to fix this? as i really want to use this distro.  :(

---

### Post by stanleys on 2004-11-25
Hi, hopefully you are still there to read this reply...


I'm having exactly the same problem.
In fact, I have two identical Dell 700m laptops and they both have exactly the same problem.



It seems that Ubuntu does not install on Dell 700m's.
Is there a place I can submit this to the developers?

---

### Post by wallijonn on 2004-11-26
From: [http://web.tiscali.it/mupuxeddu/software/libpt/](http://web.tiscali.it/mupuxeddu/software/libpt/) :
> Libpt is small collection of C++ classes for applications that need to perform some kind of pitch tracking. Main features:

    * analisys of audiofile or audiocard input stream
    * rough pitch estimation with spectral peak search
    * fine estimation with phase vocoding techniques
    * multithreaded pitch sequencing


So the first thing to try is to disable the audio in the BIOS. Then see if the install completes.

---

### Post by stanleys on 2004-11-26
[QUOTE=wallijonn]From: [http://web.tiscali.it/mupuxeddu/software/libpt/](http://web.tiscali.it/mupuxeddu/software/libpt/) :


So the first thing to try is to disable the audio in the BIOS. Then see if the install completes.[/QUOTE]
 My installation sometimes goes 1 step further, and sometimes 1 step less. I'll try disabling the audio, but I don't think that's the cause,

---

### Post by strwrsxprt on 2005-01-08
any solutions to this? i'm also having this problem on my 700m. it's not possible to disable the audio in the BIOS, at least not with any options i found.

---

### Post by minghua on 2005-01-09
Hi, in this thread Spooky found the problem and hinted a workaround.  I've confirmed that it works.  Other people may give it a try.

[http://ubuntuforums.org/showthread.php?t=6118](http://ubuntuforums.org/showthread.php?t=6118)

---

