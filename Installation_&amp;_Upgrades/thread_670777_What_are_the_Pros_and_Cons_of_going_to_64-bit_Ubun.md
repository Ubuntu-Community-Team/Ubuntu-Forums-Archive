---
title: "What are the Pros and Cons of going to 64-bit Ubuntu?"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2008-01-17
Most people I know with newer PCs (Core 2 Duo & Quad) are running 32-bit Ubuntu and loving the speed compared to Windows. But, correct me if I am wrong, they are quite eligible to run the "amd64" version... so wanted to know from others who have already switched to this what the upside and downside is.

**Benefits**: Since i386 works fine on these PCs, is the speed difference noticeable when going to optimised 64-bit? Where is it most noticeable? Everywhere, or just with programs that tax the CPU? What are the other benefits you can think of?

**Drawbacks**: Just looking around I see a few people complaining about there not being 64-bit versions for certain things like programs and even usplash and gfxboot splash images. Would I be correct in assuming you can still use the i386 versions of these things quite fine, but that people are just waiting for optimised versions? Or do some apps not run properly on 64-bit? Why do I see people calling for 64-bit versions of boot splashes... does that matter at all? (I didn't think that would be a concern, but I am ready to be educated otherwise).

So while I am looking to forward to reading about the benfits you have encountered moving to 64-bit, I am perhaps more interested in the negative aspects, as this will probably have a greater impact on my decision on which Ubuntu to go with when I upgrade my PC soon.

Also note it would probably be more appropriate if you have had the same PC running i386 before switching to amd64, for the comparison. I mean, don't know if *"I had i386 on my Pentium 3 and I switched to amd64 when I got my new Core 2 Quad... and it is SO much faster!!*" will help anyone, hehehe!

Also happy to have your opinion (based on your own experiences) on whether I should just stick with i386 for now. I would also like to know** if it is possible to update/upgrade a system from i386 to amd64** (how to do it, and what your experiences were, if you did it).

---

### Post by pytheas22 on 2008-01-17
I built a machine with a Core 2 Duo last summer and used the 32-bit version of Feisty, and now Gusty in 64-bit.  I can't say that there's a noticeable difference in speed between the two...in both cases, the machine was plenty fast.

Since going to 64-bit, there have been no major issues.  One thing to keep in mind is that sometimes it's hard to find debian packages compiled for 64-bit architectures, and you can indeed use 32-bit just as well, but the Gdebi package installer will complain if you try installing a 32-bit package on a 64-bit system and refuse to install it.  You can get around it by installing from the command line and giving it an argument to force install, but that's annoying and is not user-friendly.  Hopefully Gdebi will be improved so that you can install whatever you want with a warning, instead of having it refuse to do it when it still could if it tried hard enough.

---

### Post by OzzyFrank on 2008-01-17
Great bits of info there... yeah, one would think Gdebi would be more used to this situation, since many have gone to 64-bit only to find most of the software is still 32-bit. Obviously this needs to be addressed, as I can imagine a whole bunch of newbies out there trying to come to terms with not being able to install much software. And I would rather not have to force install everything, so thanks for that info. I'll have to try and keep an eye on when/whether this gets addressed.

---

### Post by pytheas22 on 2008-01-17
Well, it's not a huge problem, because everything in the official software channels (e.g. what you can install via Synaptic) always has a 64-bit version.  It's just with third-party stuff, like Skype for instance, whose creators don't bother building a 64-bit binary (or giving away the source code so that other people could do that).  I wouldn't hold off on 64-bit just because of this, because it's rarely an issue, but when it is it can be frustrating.

And I should have mentioned that, although having 64-bit in general doesn't make a noticeable difference in speed, it is useful when you want to do things compile stuff or brute force passwords, because being able to multi-thread there is very useful...it makes the process go faster and helps keep the rest of your system responsive.  Or if you just try to open a lot of different stuff all at the same time, having two processors will make it go faster.

---

### Post by zvacet on 2008-01-18
You will feel speed difference only if you have more then 4GB of ram.And you can not upgrade from 32 to 64.

---

### Post by Sef on 2008-01-18
> You will feel speed difference only if you have more then 4GB of ram.And you can not upgrade from 32 to 64.

32-bit can only use 4 gb ram, but it can only use around 3.7 gb.  If you want more, you have to use 64-bit.

---

### Post by mrazster on 2008-01-18
> **Sef said:**
> 32-bit can only use 4 gb ram, but it can only use around 3.7 gb.  If you want more, you have to use 64-bit.

I mean no disrespect but....*no you don't*...you can use 4gb in a 32bit enviroment perfectly fine...you just have to recompile the kenrel to support 4gb+ memory allocation.

---

### Post by OzzyFrank on 2008-01-25
Thanks for all your great advice, guys. Looks like at the moment one could go either way, but good to hear 64-bit versions of software isn't too much of an issue. I'd be interested in getting more info on how to force a 32-bit app to install, for those times I have no choice (an example of a command would suffice). Also, recompiling the kernel is as alien to me as... aliens. Sure glad these days it isn't something all Linux users have to get used to, but i am interested on knowing more on what one would have to do to recompile it (ie a 32-bit system) to work fine with more than 4Gb RAM.

Also, I gather in a 32-bit environment it will still basically be using what the chip has to offer, or am I being too optimistic here? Like, won't normal 32-bit Ubuntu use both (or all 4 in the case of quad) processors, just not as efficiently as 64-bit Ubuntu? I gathered the 64-bit version would be better just for cpu-intensive programs, but am I being naive? Would a lot of my cpu power be left untouched in Ubuntu 32-bit? Cheers

---

### Post by Bert_2 on 2008-01-28
eg. sudo dpkg -f install foo.deb
It will probably look like this.

I'm also on a 64bit system here and I've heard that it is a lot faster at things like video encoding, iso generating, brute forcing, compiling big programs and encryption (like PGP encrypting serveral GBs).

But I haven't really tested anything, I made a jump from a 1.6Ghz system to a 64 X2 2.8Ghz so I can't really say. I'm planning to install a 32bit system and test it though ;)

When I had this system I just thought this: the repository works, so why not, if there's a difference, great, if there's not whatever, it can't be bad, it's ubuntu :P

---

### Post by oldos2er on 2008-01-28
I switched to 64-bit Ubuntu about a month ago. I was doing some video encoding (with DeVeDe--great program), and wanted to see if I could gain some speed from switching, which I did. Overall the system feels slightly faster, but that's just a subjective impression, so take it for what it's worth.

 I have all the same programs installed on 64-bit as I did on 32-bit; no problems or complaints there. I used a script ([http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)) to install Flash, no problems there either.

---

### Post by mcasaroli on 2008-02-01
I am now using Gutsy 64 bits and I am sure there is a big performance improvement in fglrx ati (8.433.1) driver

---

