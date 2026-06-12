---
title: "Will a 64bit sun java 6 browser plugin appear in Intrepid."
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-09-04
Here's hoping.

---

### Post by pferraro on 2008-09-04
Not until Intrepid+1 at the earliest.
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)
"The date for JRE 6 update release which has this 64bit JRE support will be early 2009."

---

### Post by dinxter on 2008-09-04
note the date on that thread. as of then sun has been actively working on open sourcing java using openjdk which is now all but done apart from snmp. amd64 users can install icedtea-gcjwebplugin which uses openjdk for full 64bit ( in effect ) firefox java support.

---

### Post by Radiera on 2008-09-05
I gave up on 64 bit Linux(after using itmore then a year). There are just too many annoyances and just too few advantages.
For desktop, I say no to x64. I'll switch back to it when 64 bit is fully supported.

---

### Post by FrancoNero on 2008-09-05
> **Radiera said:**
> .... when 64 bit is fully supported.

I say it's about d--ed time for that to happen ;-)

---

### Post by phenest on 2008-09-05
> **Radiera said:**
> I gave up on 64 bit Linux(after using itmore then a year). There are just too many annoyances and just too few advantages.
For desktop, I say no to x64. I'll switch back to it when 64 bit is fully supported.

Have you ever thought that, a developer only supports something if they think people are using it. If you don't use it, why should they support it?

I say yes to 64 bit, and keep pestering developers to support it more.

(Save any debates on this for another thread please.)

---

### Post by Radiera on 2008-09-07
Right, I have to get headaches with installing java or whatever just for developers to feel pretty and useful. Nice thinking!
Nobody should recommend 64 bit Linux for an average user! My grandma doesn't give a damn about 64 bit or the amount of memory the OS can adress. She needs an OS that runs smooth.

I need Java to run perfectly, because I use Compiere. That you won't see on 64 bit.

---

### Post by ronacc on 2008-09-07
> **Radiera said:**
> Right, 
Nobody should recommend 64 bit Linux for an average user! My grandma doesn't give a damn about 64 bit or the amount of memory the OS can adress. She needs an OS that runs smooth.

Good thinking I'll go dust off my C64 nobody needs more than 8bits and 64k of memory .

---

### Post by Nullack on 2008-09-07
> **Radiera said:**
> Right, I have to get headaches with installing java or whatever just for developers to feel pretty and useful. Nice thinking!
Nobody should recommend 64 bit Linux for an average user! My grandma doesn't give a damn about 64 bit or the amount of memory the OS can adress. She needs an OS that runs smooth.

I need Java to run perfectly, because I use Compiere. That you won't see on 64 bit.

what specifically cant you do? jre? java in abrowser?

---

### Post by xlinuks on 2008-09-07
Does writing for 64bit require to write the whole Java platform (or any other software for that matter) from scratch? I thought like 5% of code should be rewritten, the rest is basically crossplatform C language (which most of Java is written in), but since it takes years for Sun to do that they either don't care much or it's that difficult (or both?).

---

### Post by dinxter on 2008-09-07
just to clarify, 

- the openjdk/sun collaboration to provided the 100% free java implementation is also in the repositories and is now the default-jdk since it is now 99.something complete. Look [here]("http://www.sun.com/software/opensource/java/index.jsp") for more information.

- the sun java 6 jdk is in the amd64 repositories (and has been for a while ) should you want it. 

- the icedtea-gcjwebplugin provides support for java in firefox for 64bit users.

in other words, there should be no problems with full java support for ubuntu amd64 users

---

### Post by philinux on 2008-09-08
But some applets will not work.

A sample. The top 4 work but the bottom 4 do not. This what people complain about.
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

---

### Post by Gina on 2008-09-08
> **ronacc said:**
> Good thinking I'll go dust off my C64 nobody needs more than 8bits and 64k of memory .:lolflag: Well... Bill Gates declared that nobody could want more than 640KB - so there you go! :lolflag:

I well remember the ZX81 with 1K RAM though I did buy the extra wobbly 16K - WOW such extravagance :lolflag:

---

### Post by Slug71 on 2008-09-08
Damn you got enough computors there Gina?

But yes, the more people that use 64 bit, the more support there will be for it.

---

### Post by dinxter on 2008-09-08
about [http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

although its true that the top 4 work and the bottom 4 dont on firefox amd64 with icedtea (its the first i can remember in a long time) , at least on my computer, its the same on internet explorer and chrome on windows xp (32 bit), at least on my computer :) so it doesnt seem to be specific to amd64 linux java

---

### Post by Kilz on 2008-09-08
How about getting rid of the 32bit version. 32bit processors are no longer made. Heck it was done with ppc when apple went to intel.

---

### Post by Nullack on 2008-09-08
Java on 64 bit is fine for everything I have tried. Really the only limits I find are:

Lack of a native flash plugin
Some multimedia decoders that dont have OSS versions dont have 64bit binaries as a workaround

---

### Post by philinux on 2008-09-09
> **Kilz said:**
> How about getting rid of the 32bit version. 32bit processors are no longer made. Heck it was done with ppc when apple went to intel.

I agree. But until MS only release a 64bit OS version the world may only change slowly.

---

### Post by Kilz on 2008-09-10
> **philinux said:**
> I agree. But until MS only release a 64bit OS version the world may only change slowly.

So the Linux world is tid to what MS does?

---

### Post by philinux on 2008-09-10
> **Kilz said:**
> So the Linux world is tid to what MS does?

Nah, we need everyone with a 64bit machine using the 64 os.

i was linking change in non linux users to MS.

---

### Post by Sef on 2008-09-10
> I agree. But until MS only release a 64bit OS version the world may only change slowly. 	

Gateway has [shipped]("http://www.tgdaily.com/content/view/37279/135/") retail PCs with 64-bit Windows Vista.

---

### Post by philinux on 2008-09-10
> **Sef said:**
> Gateway has [shipped]("http://www.tgdaily.com/content/view/37279/135/") retail PCs with 64-bit Windows Vista.

Excellent. Lets hope more do it.

---

### Post by phenest on 2008-09-10
Someone correct me if I'm wrong, but isn't the reason most 64 bit machines ship with 32 bit Windows, because there are bugs in the 64 bit versions rendering them unstable?

---

### Post by Nullack on 2008-09-10
> **phenest said:**
> Someone correct me if I'm wrong, but isn't the reason most 64 bit machines ship with 32 bit Windows, because there are bugs in the 64 bit versions rendering them unstable?

No. not at all

In fact the  64bit Vista is more secure than the 43 bit variant

---

### Post by cariboo on 2008-09-10
I have to agree with Nullack, I have Vista Ultimate Edition 64bit, and from what I can tell it seems to be more stable then 64bit XP. Mind you the longest I have used it at one time was 6 hours, and my total usage in a month is probably only 1 hour at the most.

Jim

---

### Post by Nullack on 2008-09-10
I dont run Vista at all anymore but I know there is tangible facts to why 64bit is more secure:

* They turfed legacy support for many windows platform stuff that isnt needed anymore and hence the attack surface area is reduced
* There is specific x64 features with security that is only implemented on x64

With WOW - windows on windows you can run 32bit apps no problems and in fact I ran 32bit IE for sometime on x64 vista due to adobe's flash.

I see no reason at all why someone would want to run 32bit Vista.

For Ubuntu, you could consider that some multimedia codecs havent been reverse engineered and some binary decoders arent available on 64bit. Thats the chief reason in my view why 32bit Ubuntu might still be needed on modern hardware.

---

### Post by phenest on 2008-09-11
> **Nullack said:**
> No. not at all

In fact the  64bit Vista is more secure than the 43 bit variant

You hear stories, you make assumptions... Personally, I only use Ubuntu, so I don't know.

So then, why do all these manufacturers ship 32 bit Windows with a 64 bit machine? It's not exactly helping to promote new technology, is it?

---

### Post by pferraro on 2008-09-11
> **phenest said:**
> So then, why do all these manufacturers ship 32 bit Windows with a 64 bit machine? It's not exactly helping to promote new technology, is it?

Because of the lack of 64-bit drivers for many devices, e.g. printers, winmodems, webcams, etc.

---

### Post by nanog on 2008-09-11
I've bought boxes with 64bit vista from HP. In fact, I think all of their boxes with >4 gig ram are 64 bit.  Anyone doing serious computing needs 8-16 gigs to take full advantage of modern 4-8 core boxes.

---

### Post by mobrien118 on 2008-10-13
> **pferraro said:**
> Because of the lack of 64-bit drivers for many devices, e.g. printers, winmodems, webcams, etc.:KS

I agree. It isn't that 64-bit windows doesn't support running 32-bit programs well...it does. It also isn't a lack of Microsoft's development effort in Vista 64-bit...it was there.

The issue is 3rd party driver support. My understanding is that since device drivers run in Kernel space (rather than user space) you cannot emulate 32-bit for a 32-bit driver. The driver must be written to run on a 64-bit processor. Since windows can't force device manufacturers to wrangle up their developers and make 64-bit drivers, companies aviod 64-bit windows until driver support is more universal.

This is also why many companies are able to use 64-bit Windows Server 2003, because there is a much smaller pool of device drivers needed on servers than in consumer/desktop PCs.

The difference with Linux is that device drivers can be tweaked and re-compiled by users, who then resubmit their changes upstream and thus an entire OS can be more quickly adapted for 64-bit. This is one of the benefits of FOSS.

--mobrien118

---

### Post by 73ckn797 on 2008-10-13
> **Nullack said:**
> Java on 64 bit is fine for everything I have tried. Really the only limits I find are:

Lack of a native flash plugin
Some multimedia decoders that dont have OSS versions dont have 64bit binaries as a workaround

I wanted to use the 64 bit Ubuntu Hardy but there are several java photo upload applets (Aurigma Image Uploader) that will not work at all with the provided Javas. The 32 bit Firefox trick would not work either. I am one that wants it all to be 64 or it is useless for my needs. Java works fine in 32 bit Hardy.

I can wait, however. 

Not complaining but would use the 64 bit if that was working. Why have a 64 bit Mobo when full potential cannot be realized, IMHO?

---

### Post by phenest on 2008-10-16
> **philinux said:**
> But some applets will not work.

A sample. The top 4 work but the bottom 4 do not. This what people complain about.
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

All 8 applets work for me now.

---

