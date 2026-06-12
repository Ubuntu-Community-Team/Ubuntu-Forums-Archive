---
title: "Install error. . ."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Bright_View on 2010-01-11
During (failed) installation of any Ubuntu (Hardy, Karmic, Jaunty), I get the following error, generally several times:

'The following did not match its source copy on the CD/DVD' 

and then it lists the problematic file and suggests that it could be a faulty CD/DVD drive or disk, or a faulty hard disk.  My question is what exactly is the system comparing to the source copy on the CD/DVD?  Is it the file as written on the hard disk?  Or is it the file in memory before it's transferred to the hard disk?  I'm trying to isolate the source of this problem, and it would be easier if I understood more fully what this error means.

Cheers.

---

### Post by zvacet on 2010-01-11
It can be bad burn or bad iso.Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before burning iso and [CD integrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck") after?If you have iso on HDD download same iso with torrent and point download where your iso is.That way torrent will check iso for bad files and replace them with good ones.After that run md5sum again.Burn disc on lower possible speed.You can find all you need [here.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Bright_View on 2010-01-11
Thanks for the reply zvacet.  I am actually looking for more information about the actual error, as I have tried four different optical drives to burn the discs, I have tried two different drives to do the install, I have used md5 sums to check the disc integrity, I have verified the soundness of the memory using memtest, I have replaced the hard disc, I have set the bios settings to default.  Nothing has helped.  

I'm  thinking there is a very interesting hardware problem and I'd very much like to isolate it.  More in-depth information regarding this specific error may help, because it's very repeatable (although it doesn't always fail installing the same file).  So if I knew what it was actually comparing, I might have a clue as to what component is faulty.

If anybody has any idea, I would very much appreciate the information.

Thanks all,

Dave.

---

### Post by Bright_View on 2010-05-09
I never did figure out what was being compared to what, but I did isolate the problem:  faulty memory.  I tried the install with only one stick of memory in at a time, and it worked when I left one of the memory modules out.  I was kind of surprised, since this stick of memory had passed memtest several times, but got the idea from a friend who is more knowledgeable about hardware than I am.  He informed me that repeatable, random errors during install are almost always due to bad memory.

Hope this helps somebody else. . .

---

### Post by matmuc on 2010-05-10
IHello,
I have the same problem during installation. I tried different disks, different image files and so on, and I always get the same mistake. But it always reports different files!
I am sorry, but I don't believe in those hardware excuses anymore. I am in the business too long (25 years) to believe that.
It simply appears to me that no one has an answer to the problem, because the error message is wrong, due to a programming error: wrong error trapping in the installation routine. So you never get the real cause of the error and the guessing goes on and on. You could as well get an answer telling you not to install it in a full moon night, or just anything.
Very disappointed!
Mathias

---

### Post by Bright_View on 2010-05-11
> **matmuc said:**
> IHello,
I have the same problem during installation. I tried different disks, different image files and so on, and I always get the same mistake. But it always reports different files!
I am sorry, but I don't believe in those hardware excuses anymore. I am in the business too long (25 years) to believe that.
It simply appears to me that no one has an answer to the problem, because the error message is wrong, due to a programming error: wrong error trapping in the installation routine. So you never get the real cause of the error and the guessing goes on and on. You could as well get an answer telling you not to install it in a full moon night, or just anything.
Very disappointed!
Mathias

Sorry to hear you're having the same problem matmuc, it was pretty agonizing for me.  I'm not a hardware or software expert, but from what I do know the hardware explanation makes sense to me.  In my case, both XP and Ubuntu weren't installing properly, so it definitely didn't seem to be due to Ubuntu.  Actually, what made it so frustrating was that the first couple of times XP did install, so I figured it was something to do with Ubuntu, but upon further experimentation XP suffered the same fate.

I would definitely recommend removing your memory modules and keeping only one it at a time and see if you can isolate the bad module.  Then experiment with it to verify that the memory module is indeed the problem.  That's what I did - I attempted re-installing several times once I isolated the bad module, to make sure that it always worked with that module out of the system, and always failed when that module was in the system.  I'm quite certain after all that that the memory module was indeed to blame. 

Best of luck!

---

