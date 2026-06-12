---
title: "What's the Min. of RAM to run 64 bit OS ???"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Alexdelpiero1974 on 2010-09-04
What's the Min. of RAM to run 64 bit OS ???

---

### Post by jocko on 2010-09-04
Depends on what 64 bit OS you ask about, but for ubuntu I don't think there is any reason why the minimum requirements would differ between 32 and 64 bit...
But I don't think there are many (any?) 64 bit computers that have less ram than the recommended minimum of one Gb anyway, so I think your question is quite pointless.
If you have a 64 bit computer it will run a 64 bit OS... because... that's what it's built for...
Ubuntu 64 bit will probably run on 512Mb, if you manage to find or build a 64 bit computer with that little ram...

**EDIT:** Just tried booting my ubuntu 10.10 (beta) 64 bit in a virtual machine with only 256 Mb of ram, and it seems to run unexpectedly fine (except it's using the swap partition a lot, so it's not very fast...).
**EDIT 2:** It even runs on only 128 Mb... But very noticeably slow and choppy (I had a computer with 512 Mb ram that ran about as slowly with windows XP as ubuntu 64 bit does with only 128 Mb).

---

### Post by Alexdelpiero1974 on 2010-09-04
> **jocko said:**
> Depends on what 64 bit OS you ask about, but for ubuntu I don't think there is any reason why the minimum requirements would differ between 32 and 64 bit...
But I don't think there are many (any?) 64 bit computers that have less ram than the recommended minimum of one Gb anyway, so I think your question is quite pointless.
If you have a 64 bit computer it will run a 64 bit OS... because... that's what it's built for...
Ubuntu 64 bit will probably run on 512Mb, if you manage to find or build a 64 bit computer with that little ram...

sorry , i didnt mean to ask pointless questions :( , i just dont know much about Ubuntu
anyway , what do you mean about 64bit computers ??? how do i know if my pc is 32 or 64  ????

i have 1.25 GB RAM

---

### Post by jocko on 2010-09-04
> **Alexdelpiero1974 said:**
> anyway , what do you mean about 64bit computers ??? how do i know if my pc is 32 or 64  ????

i have 1.25 GB RAM
To be able to run a 64 bit operating system, you have to have a 64 bit cpu... What cpu do you have?

---

### Post by Alexdelpiero1974 on 2010-09-04
> **jocko said:**
> To be able to run a 64 bit operating system, you have to have a 64 bit cpu... What cpu do you have?

i think my cpu is 32x , but i'm not sure , how to verify that ????

---

### Post by jocko on 2010-09-04
> **Alexdelpiero1974 said:**
> i think my cpu is 32x , but i'm not sure , how to verify that ????
For starters you could say exactly which cpu you have. If you run ubuntu (or any other linux distro), run this command in a terminal and post the output here:
```
cat /proc/cpuinfo
```If you run windows or any other non-*nix os, I have no idea how to check...

---

### Post by crichard on 2010-09-05
> **Alexdelpiero1974 said:**
> i think my cpu is 32x , but i'm not sure , how to verify that ????

Have a look at [here]("http://ubuntuforums.org/showpost.php?p=8920688&postcount=5")

---

### Post by peptobismal on 2010-09-05
I was thinking of trying to run the a64 version of Ubuntu, but I am concerned as to program efficiency. How well does Ubuntu handle 32bit programs or can it even handle them? I know Windows 7 runs 32bit pretty well with their WOW64 or whatever they call it. I just want to get the most out of my Quad Core, but if my 32bit programs aren't going to work there's not really any point.

---

### Post by crichard on 2010-09-05
> **peptobismal said:**
> I was thinking of trying to run the a64 version of Ubuntu, but I am concerned as to program efficiency. How well does Ubuntu handle 32bit programs or can it even handle them? I know Windows 7 runs 32bit pretty well with their WOW64 or whatever they call it. I just want to get the most out of my Quad Core, but if my 32bit programs aren't going to work there's not really any point.

You can run 32 bit apps inside 64 bit OS without any problem. I'm using 64 bit Ubuntu 10.04, If I couldn't catch a 64 bit version of an application, at that time only I prefer 32 bit version of that application. For that, I wont switch my OS. Install 64bit & utilize your QuadCore well.

---

### Post by linux18 on 2010-09-05
64 bit runs in text mode at 60MB of ram (I have a remix just for that), graphically it will run in 74MB.
32 bit runs in text mode in 40MB of ram and graphically in 54MB

note: this is the minimum before kernel panic, it's not very usable at these levels

---

### Post by qyot27 on 2010-09-05
I'm guessing the idea expressed in the OP that the minimum amount of RAM for 32 and 64 bit OSes differ is likely because Windows 7's specs make a point of saying that the 32-bit version requires 1GB, while the 64-bit requires a minimum of 2GB.  I severely doubt this from an operational standpoint, but Microsoft may have a RAM check that will refuse to let Win7 64 install on a system with less than 2GB - I don't know; I'm still back on XP.  In any case, this is most certainly untrue of Ubuntu; AFAIK the specs for the fully-featured versions are the same, with the exception of 64-bit obviously needing a 64-bit capable processor.

And I can separately confirm that 64-bit Ubuntu works just fine with 512MB or less - my grandparents have a comp with an Athlon64 Orleans and only 448MB (reported; at other times it reports 512MB) of RAM, and 8.10 64-bit ran without issue on there* (it was on a dedicated partition, though; I later tried the 64-bit versions of 9.10 and 10.04 with Wubi and got all sorts of random wonky freezing, often right in the middle of trying to update the kernel, which would then seemingly corrupt everything necessary for it to even boot...fun times, and a very valid lesson in why it's not a good idea to put too much trust in Wubi).

*not to mention running laps around the 32-bit XP Home it was dual-booted with.

---

### Post by peptobismal on 2010-09-08
> **crichard said:**
> You can run 32 bit apps inside 64 bit OS without any problem. I'm using 64 bit Ubuntu 10.04, If I couldn't catch a 64 bit version of an application, at that time only I prefer 32 bit version of that application. For that, I wont switch my OS. Install 64bit & utilize your QuadCore well.
Ugh, haha, now I am probably going to have to image to my other partition and all that stuff... Oh well, I'm going to wait on getting a new harddrive and new motherboard/RAM (2 months old). Even though, it's not old stuff the harddrive is and the disk utility says that I am getting a max of 80MB/sec read-time. I just want the motherboard and RAM for VirtualBox so I can allocate more than a gig (without red flags) of my 4GB for Windows 7.

---

### Post by peptobismal on 2010-09-08
> **qyot27 said:**
>  I severely doubt this from an operational standpoint, but Microsoft may have a RAM check that will refuse to let Win7 64 install on a system with less than 2GB - I don't know; I'm still back on XP.
Nope, it installs fine with 1024MB of RAM in VirtualBox. I just can't get it to run now, because I am on 32bit Ubuntu, haha. Recommended minimum requirements, key word is usually recommended; however, I wouldn't have second guessed Microsoft doing something like that had I not saw for myself. I mean they have a history of being the scum of computers. Dating all the way back to the good old no-privacy Windows 98 days.

---

