---
title: "Dual boot Ubuntu distros?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by AdrianOfTyriel on 2007-07-09
Hi, i'm wondering if i have to set up another partition to run 2 Distros... what i want to do is to have the option to select between normal ubuntu and ubuntu 64-bit, but i'd LIKE to maintain the same information between distros (i.e. Evolution emails, contacts, etc.)

Can someone tell me if this is possible?

---

### Post by kidders on 2007-07-10
Hi there,

Be very careful with any attempt to share data between OSs with different bitness. Email is a perfect example, because it tends to be cached in a very database-like manner. I would be bitterly disappointed if it turned out that you *could* share the same local email/contacts caches between a 32-bit and 64-bit OS, because it would mean that your software wasn't taking proper advantage of its 64-bit environment.

Anyhow, to answer your question, it would be highly inadvisable to attempt to install more than one operating system into the same disk partition. Also, it's worth noting that there's nothing abnormal about 64-bit Ubuntu ... in fact, there's very little point in having a 64-bit processor unless you install a natively compatible OS!

I hope that helps.

---

### Post by AdrianOfTyriel on 2007-07-10
Yeah, well, that's why i want to have 64-bit, but my understanding is that not everything works on 64-bit OSes yet, so i'd like to have a 32-bit OS for my daily needs, and a 64-bit OS when i need extra CPU power.

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **AdrianOfTyriel said:**
> Hi, i'm wondering if i have to set up another partition to run 2 Distros... what i want to do is to have the option to select between normal ubuntu and ubuntu 64-bit, but i'd LIKE to maintain the same information between distros (i.e. Evolution emails, contacts, etc.)

Can someone tell me if this is possible?

Can't you just copy over your "/home/" directory? ;)

Better yet. Create entire "/home/" partition and make both installs use it for your /home/ directory. :D

---

### Post by kidders on 2007-07-10
> **Odrodzona-Sarmacja said:**
> Create entire "/home/" partition and make both installs use it for your /home/ directory. :DBe very cautious with that approach. Sharing a /home between a 32-bit and 64-bit OS can cause unpredictable behaviour and data loss. I would advise against doing it, unless you know what you're doing.

---

### Post by AdrianOfTyriel on 2007-07-11
So, it sounds like i should just use 32-bit for most of my computing needs, and ONLY use 64-bit when i really need the power on specific tasks.

---

### Post by kidders on 2007-07-11
I dunno about that. It seems odd to *want* to force your CPU to perpetually emulate non-native operation. Surely an OS that is designed to run on your hardware will be more stable for everyday use.

---

### Post by AdrianOfTyriel on 2007-07-11
Yes, but my understanding is that there is still a lot of stuff that isn't compatible with 64-bit systems, both hardware and software alike that just plain don't work, and since i'm not exactly a developer... i need things to work most of the time...

---

### Post by regomodo on 2007-07-11
> **AdrianOfTyriel said:**
> Yes, but my understanding is that there is still a lot of stuff that isn't compatible with 64-bit systems, both hardware and software alike that just plain don't work, and since i'm not exactly a developer... i need things to work most of the time...

be prepared for flaming. a lot of people here are in love with their 64bit ubuntu as they say it works

---

### Post by AdrianOfTyriel on 2007-07-11
> **regomodo said:**
> be prepared for flaming. a lot of people here are in love with their 64bit ubuntu as they say it works

Lol, well if it works, then great! I guess i'm wrong, i have no issue with that, i'm just reitterating what i had read.

---

### Post by kidders on 2007-07-11
> **AdrianOfTyriel said:**
> i'm just reiterating what i had read.There's certainly some truth to what you may have read. For instance, 64-bit web browsing is a bit of a headache, because compatible, reliable Flash/Java/RealPlayer/etc. plugins simply don't exist. As a result, many browser developers (eg Opera) don't see the point in releasing 64-bit versions of their software at all. On the other hand, 32-bit developers are not very likely to take support for 64-bit hardware terribly seriously ... after all, *they* will hardly see the point in spending time on software to support hardware that won't even work with 32-bit machines.

In general terms, 64-bit users run into problems where crappy software developers refuse to acknowledge the existence of their CPUs. Eventually, that will change, but until then, the "usual" approach is...[LIST]
[*]Install a 64-bit OS that can emulate 32-bit operation on demand (eg Ubuntu). Imo, very few 64-bit PC owners run a "pure" OS ... although you *can*, if you don't mind exposing yourself to all the gotchas you've read about.
[*]Occasionally, it can be nice to install a full-blown 32-bit chrooted environment ... essentially a minimal 32-bit Linux install that you can use alongside the native 64-bit one, for even more flexibility.[/LIST]Regomodo's comment about flaming is true hehe ... it's not very likely that many forum posters (including me, tbh) will be too enthusiastic about the idea of running the "wrong" OS on your machine. The natural assumption, you see, is that you must have chosen a 64-bit box for a reason. Having said that, it's *your* box!

Personally, my approach has always been to run a 32-bit web browser (along with one or two other applications) on my 64-bit Linux, to avoid any problems.The result is, of course, very slightly slower than native 64-bit operation, but at least only a handful of applications are affected, rather than my entire PC.

Hopefully that helps a bit. Bluntly speaking, I can certainly understand why someone might want to run two different Linux distros on their machine, but running two copies of the *same* thing (albeit with differing bitness) seems odd. You'd be deliberately engineering your PC so you would *have* to reboot it in order to browse a flash website, rather than simply double-clicking your embedded 32-bit web browser.

**Edit:** One thing worth noting is that, unless you're engaged in something very heavy duty (eg hardcore rendering, highly CPU-intensive scientific research, etc.), the performance difference between "64-bit on 64-bit" Ubuntu and "32-bit on 64-bit" Ubuntu probably wouldn't be significant enough to warrant a reboot. What I mean, I suppose, is that if you were using 32-bit Linux on your 64-bit machine for day-to-day purposes, it's not very likely that you'd ever want to do anything that would make the irritation of a reboot into the 64-bit OS seem worthwhile to you. The performance & stability differences are there, but they are modest. Consequently, the most sensible options are probably (a) installing 32-bit Ubuntu only, and pretending you hadn't bought a 64-bit box at all, or (b) installing 64-bit Ubuntu only, and taking the benefits where you can get them.

Incidentally, are there any reasons why you would _require_ a 64-bit operating system? Examples might include using very large filesystems, having an awful lot of RAM, having hardware that is incompatible with 32-bit OSs, doing a lot of rendering or media processing, and so on.

---

### Post by AdrianOfTyriel on 2007-07-11
Okay, so it's not hard to set up a 32-bit browser (firefox lets say) on a 64-bit OS? Then that's what i'll probably do... do most of my computing in 64 bit and have a minimal install of 32-bit (and... i hate to even mention it... windows... for the few programs i can't get working under wine that i need).

Thanks a lot for your help! This is why i love linux... the people on the forums are just much more helpful than most webforums out there.

---

### Post by kidders on 2007-07-11
Lol hey again...

I've been busy tweaking my last post, and I didn't even see your reply!

If you *do* decide to run 64-bit Ubuntu, you will probably find that none of the brick walls you run into is unique, and that someone else has invariably already found & documented solutions. Taking the browser plugin issue as an example, I recently installed Gentoo (an old favourite of mine hehe). Even a web search as non-specific as "gentoo amd64" returned pages explaining ways of keeping my nice 64-bit operating system *and* getting headache-free web browsing. Hopefully, you'll be able to find what you need with similar ease.

Chrooting is an immensely convenient way of running two kinds of applications side by side. Having said that, you don't always need to do it, so don't be in too much of a rush to set it up. For instance, afaik (I don't use Wine), there are methods of running Wine on 64-bit Linux both with and without chroots. Quite often, Ubuntu's built-in 32-bit system libraries are quite enough to get by.

---

