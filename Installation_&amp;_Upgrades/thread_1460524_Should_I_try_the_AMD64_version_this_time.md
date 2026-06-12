---
title: "Should I try the AMD64 version this time?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by schmickey on 2010-04-22
I now have a laptop with a 64-bit processor (Intel SU2300).  In the past I read that there can be driver and other problems using the AMD64 version so I have always used the i386 one.

Now I'm wondering if those cautions are still valid. Karmic 9.10 (i386) ran just fine on this laptop but now I'm wondering if I should try the 64-bit version for Lucid -- a clean install, of course.

Will I run into any software/driver problems?  Any advice, cautions, or tips would be very much appreciated.

---

### Post by labinnsw on 2010-04-23
I recently made a booboo on my system and decided to reinstall. I used the opportunity to install the 64 bit and it has been the best decision I have made since my decision to switch to Linux. Everything works, everything is faster, and everything looks better. Just remember this command and use it whenever you need to install 32 bit software. ```
sudo dpkg -i --force-all *.deb
```

When using this command cd to the directory where the package is located.
You can type or paste the command exactly as I have posted it, or you can substitute the package name for the asterisk.

---

### Post by Detonate on 2010-04-23
Absolutely!!

See this thread for installing flash.  Don't use the flash plugin in the repos.

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by schmickey on 2010-04-23
Thanks for the replies and tips!  I'll try the AMD64 for Lucid.

Yes, I was wondering about Flash with 64-bit.  And what about Java?

---

### Post by ddarsow on 2010-04-23
I had to do the following for Flash to be clickable, but 64 works perfectly now.

```
sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Add this before the last line of text “export GDK_NATIVE_WINDOWS=1&#8243;, then save and restart firefox.
```

---

### Post by cascade9 on 2010-04-23
If your CPU supports 64bit, then go for it! 64bit used to be far more troublesome, but its very good these days. 

> **schmickey said:**
> Yes, I was wondering about Flash with 64-bit. 

You can run 32bit flash in 64 bit (ddarsows method is just one way to do it) but I use the 64bit beta myself- just d/l it from adobe, then manually install it (well, unzip and move it to the right directory- /usr/lib/mozilla/plugins) 

I havent had any issues at all with running 64bit flash like this.

---

### Post by Detonate on 2010-04-23
> **schmickey said:**
> And what about Java?

In Firefox, I use the IcedTea plugin to handle Java.  In Chromium, my preferred browser, Java is handled by the system default.  No problems in either.

---

### Post by schmickey on 2010-04-23
I tried using the 64-bit Adobe Flash before I read the thread recommended above.  I neglected to install the 64-bit Firefox mentioned in the thread.  I assumed 64-bit Linux would come with 64-bit Firefox.  Am I wrong?  I put the libflashplayer.so into the /usr/lib/mozilla/plugins folder but it would not run.  It showed up in the add-ons within firefox but wouldn't run.

I'll try again after following the thread concerning this topic recommended above to install 64-bit FF.

EDIT:  Okay, the "help/about" in my default installed FF says I *do* *have* 64-bit Firefox but it's ver. 3.5.9, not version 3.6 as recommended in the thread.  I installed the Karmic AMD64 today for the first time.  Maybe this process will be easier with Lucid?  Perhaps even transparent?  Or is that too much to ask?  I suppose it is, due to limited cooperation from Adobe.  Also, if you're using 64-bit Ubuntu, are you automatically offered 64-bit apps from the repos?  Or do I have to manually install 64-bit apps?  This is all new to me... was never a problem with 32-bit.

I will say that most things seem faster with the 64-bit installed.

---

### Post by labinnsw on 2010-04-24
I don't recall any issues with apps from the repos. Where an issue arises is with other downloaded 32 bit debs like skype or frostwire in which case you force installation from the command line as I have indicated.

---

### Post by schmickey on 2010-04-24
Okay, good.  Thanks for the info.  Got the Flash working okay.  Next will be Java (or IcedTea) in FF.  It definitely does seem faster than the x86 version and I'm showing 3.8GB RAM instead of the 2.9 that was showing in 32-bit.  (I have 4GB in this machine.)

---

### Post by labinnsw on 2010-04-24
I have java (needed for OpenOffice, Frostwire and I don't know what else.)
I can't be sure now, but I vaguely remember getting something from [here]("http://www.java.com/en/download/manual.jsp#lin")

Yes I am sure now. I went back and looked at the instructions and that confirmed my suspicions.

---

### Post by schmickey on 2010-04-24
Excellent.  Thank you!

---

