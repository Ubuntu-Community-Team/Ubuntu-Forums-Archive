---
title: "Installing Ubuntu on Pentium I 200 MHz"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Superdude_123 on 2008-05-13
Hey All,


Here's my question:

I just woke up the dinosaur and I would like to run a FTP and/or HTTPS server with it. The system specs are:

32 MB ram,
3 GB hard drive
Intel Pentium I 200 MHz
and use to run Windows 95


So what can I do with this unit?.....and I already tough of making it into a BBQ

---

### Post by Mhurst1 on 2008-05-13
Use it as a big paper weight :D

---

### Post by SoloSalsa on 2008-05-13
I really don't know anything about it, but maybe Ubuntu Server might interest you.

---

### Post by Mhurst1 on 2008-05-13
I dont think it will install on that harddrive. I think its too small. You could try puppy linux though.

---

### Post by CREEPING DEATH on 2008-05-13
Forget Ubuntu, it won't load on that.  You're going to have to go pure Debian, which will be a strain.  Just download the netinst image, install, and then install the packages you need.

CD

---

### Post by Neobuntu on 2008-05-13
Here's what you do. It will not run like a new computer but you can use it.

You hit the real bottom RAM at 32MB (I actually did one with 24MB and that was hard) for running X and maybe a tiny browser. All your apps need to be tiny versions like are used in lean distributions. Your goal is to avoid swap space and therefore disk thrashing at all costs.

Abiword for word pro etc...

Install a base comand line system.

Install X

Install icewm
 
You can actually make it look just like XP if you use the Silver XP theme and it's fast. The best way to setup icewm is to simply edit the configuration text files. 

Of course you can do all manner of CLI apps. Networking. File backup server. Music player/sever. Video server (to other front ends).

Let me see If I can find you a guide...

[http://forums.debian.net/viewtopic.php?t=20228](http://forums.debian.net/viewtopic.php?t=20228)

I'm not sure if I would use a Debian base or a Ubuntu base. Ubunutu if it will work, I guess. Either of these leaves the door open for upgrades and better hardware compatibility. Puppy Linux may have something pre-rolled that you could use but you'll have to try a few versions and you might not like it's different way of doing everything. It is optimized for speed though and you could just stay live, if you have a fast CD ROM.

You can learn from Puppy. You can set up a similar system installed (my link above). It's more flexible.

Of course, more RAM is recommended.

If you have notebook, there's a slight possibility you might run into a weird built-in video chip. 

Is it a Desktop?

Don't forget, modern computing needs over 256MB RAM and anything less is an exercise in getting by. It is **NOT** representative of modern open software (like Kubuntu.) Yet, at least it's supported.

Remember, Win98 would choke on this box eventually. So this is the bottom. XP can actually run on 64MB but it's no fun at all! You'd need more memory than (384MB min) Kubuntu to run as fast with the XP. I stopped doing Window installs due to the horrendous, comparative time it takes to really set one up.

Enough RAM, is the line. It's 384MB; so that you can run Kubuntu IMHO (on your main full system). Secondary uses, see above.

---

### Post by iissmart on 2008-05-13
Here is the guide I used to install Ubuntu 7.10 on a 166MHz, 80MB RAM, 2.2GB drive COMPAQ laptop. It works well if I don't use X and at an *almost usable* speed when using X to mainly browse the web. Although at this point its not really the "Ubuntu" experience. A Debian netinst might work better but I don't want to go through the 4+ hours it took to install the base command line system on that thing again. Really the main reason it works so "well" (I use the term loosely) is because I upgraded the RAM in it to a whopping motherboard-capped 80MB.
 
Yes it will take a long time to install and yes you will probably think the installer froze (especially with 32MB of RAM) but just let it chill for a while, play some GTA IV, and it should be done eventually.
 
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by wandalalakers on 2008-05-14
Also try damn small linux

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

Minimum Requirements for DSL with X-Window:

    * i486
    * 24 MB RAM

---

### Post by Neobuntu on 2008-05-16
I found those DSL minimums true but slightly misleading. Not all of it works with those minimums and many things are limited(comparatively). It depends on what you plan to do with it. 

I had a good experience with a Live CD of Puppy 2.15CE over DSL(Linux) but I suppose that is dated now. It highly depends on which version(s) of DSL or Puppy CD that you burn, and that is the problem. Newer is not always better (more so) with them.

You might also consider...> [http://antix.mepis.com/index.php/Applications_used_in_antiX-M7.2](http://antix.mepis.com/index.php/Applications_used_in_antiX-M7.2)... This shows which lean apps that Antix uses.

Antix is kind of a custom Debian/Mepis hard drive (not live) install. You may consider it an example; done for you (time saver!). You might want to see it in action even if you roll your own.

The problem with all this is time. If you take the time to build on Ubuntu (or maybe Debian would be better for this) then you will have just what you need and better options, come time to upgrade what you have. As I said, most importantly, better compatibility with whatever old hardware you may have or get.

So, if you would like to do this fast(er), AKA, more pre-done. Another interesting option is the Debian (directly) /Mepis based Antix (like Antiquities, meaning old hardware.) This may be your best bet for a non-live; drive installed system. It  installs FAST! It has good online, friendly support too. If the good hardware compatibility and the upgrade ability level suits you, this may be your best and fastest route. Even if it is somewhat less flexible than a base build-up install. AntiX is done well! Yet, every person, and what they want is different.

A Puppy 2.15CE disk would be best for a live only, quick (fastest) and dirty, get the job done (whatever that is for you.) It looks nice, updated and finished. Which is cool for an old system. As I said though, things like WiFi setup are done differently with (somewhat) odd, text based (really functional) wizards. But hey, it works. BTW, Puppy (and DSL too) have long been adept at saving your stuff, even when you're running live and automatically restarts with your dynamic changes, even though your Live boot CD may be static. You don't even need a hard drive but you will need something to save on. Like an inexpensive USB drive perhaps. Use "USB 2.0" even if you have to add a port for $20 (PCMCIA or PCI). 

With all that said, I wanted less limits than Puppy could provide. Like I said, the only problem with the great Puppy 2.15CD CD, is it's old now. I find the next versions become hit or miss and I don't like to let grass grow. Do you understand? This stuff is **not** static. So considering a smoother upgrade path; if you're willing to tweak. a custom molded system, starting with Debian or Ubuntu would get you the best system, with the fewest disadvantages. You'll have much easier upgrade ability, as these things are NOT static. You may have much better hardware compatibility too and it might take less time (than Debian) to do all that with; in the long run with the Ubuntu(base).

Please let us know how it goes. See the link above for hints at which quick apps to install. Remember that is the main game (with low memory)! Stay out of swap space. It is really amazing at the nearly complete and full benefit you can achieve. It never beats almost new hardware, however. Yet, it is surprisingly close; unless you want to do movie editing or some such.

It depends. :)

Keep in mind that we **never** like running the minimum requirements. Something that works minimally with **less** will work nicely with a bit more. So to keep your sanity, use something RAM underrated (more RAM that the minimum). Then you can actually rival new systems speeds in a lot of normal situations, even on old hardware. After RAM size, try to get the fastest hard drive you can. The speed, nor size is often overlooked. Be very aware too, that while a much bigger hard drive is likely by nature the faster, way too big may not work with an old given BIOS. There are tiered difficulties to get over at varying; larger sized hard drives than came standard, on period motherboards.  

Really old hardware does **not** make (low RAM enhanced) open software look better than (old)Windows. Yet old Windows is not, supported, unsafe and as buggy as a flea bitten dog. It's not worth the much longer time and hassle. So Linux does have a better solution on old hardware but it does not make it new, nor does is encourage migration to open software (Kubuntu on 384MB >= RAM) like is seen on newish hardware.

---

### Post by K.Mandla on 2008-06-05
It'll work fine. 200Mhz is still usable. 75Mhz is a different story.

[http://ubuntuforums.org/showthread.php?t=294292](http://ubuntuforums.org/showthread.php?t=294292)

Keep your system light and clean and it will run without a hitch. 32Mb is an awfully small amount of memory though; if you can add a little more, 64Mb is much more usable.

---

### Post by Ptero-4 on 2008-10-21
You can use FreeBSD in pure cli mode and with an external HD you'll have a nice fileserver.

---

