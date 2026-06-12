---
title: "64-bit definitely faster than 32-bit?"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by fuzzylogic25 on 2010-06-02
according to this article i read, its definitely faster. this is what i read:

===================================================================
Since 64-bit systems can process twice as many instructions per second as a comparable 32-bit system, 64-bit systems are definitely faster than their 32-bit counterparts. 
===================================================================

it was from this article link:

[http://www.windowsnetworking.com/articles_tutorials/64-Bit-Computing.html](http://www.windowsnetworking.com/articles_tutorials/64-Bit-Computing.html)


Is this true? I always thought it wouldnt make a difference, besides more memory addressing?

---

### Post by jaakan on 2010-06-03
> **fuzzylogic25 said:**
> according to this article i read, its definitely faster. this is what i read:

===================================================================
Since 64-bit systems can process twice as many instructions per second as a comparable 32-bit system, 64-bit systems are definitely faster than their 32-bit counterparts. 
===================================================================

it was from this article link:

[http://www.windowsnetworking.com/articles_tutorials/64-Bit-Computing.html](http://www.windowsnetworking.com/articles_tutorials/64-Bit-Computing.html)


Is this true? I always thought it wouldnt make a difference, besides more memory addressing?

64bit means you can deal with bigger numbers and larger datasets.
here is the BUT, if the program is not made to take advantage of the hardware you will not see a difference clock for clock.

so "Since 64-bit systems can process twice as many instructions per second as a comparable 32-bit system, 64-bit systems are definitely faster than their 32-bit counterparts. " is just not correct. they are not telling you the full story.

---

### Post by Linuxforall on 2010-06-03
On proper multi core PCs with more than 4GB RAM, it will run memory and CPU intensive programs far better than x32 as shown by Phoronix bencharks on encoding, compiling etc.

---

### Post by varunendra on 2010-06-03
I'm not an expert in this but here's what I've experienced so far-

In any case, a 64bit system would be either equivalent or better than 32bit. Some facts to support this:

64bit hardware can run 32bit OS as good as a 32bit hardware. GOOD!
64bit OS can run (almost) all the 32bit applications as good as a 32bit OS. GOOD!
The only case where problems may arise is when using 32bit drivers with 64bit OS. :(

The final equations:
:) 64bit hardware + 32bit OS = No problem
:) 64bit hardware + 64bit OS + 32bit application = No Problem (negligible exceptions)
:) 64bit hardware + 64bit OS + 32bit (multi-core, cpu-intensive) application = Great!
:P 64bit hardware + 64bit OS + 64bit application = Great-Great-Great!!
:confused: 64bit hardware + 64bit OS + 32bit driver = Ouch!!

So the summary is:[COLOR=Red]** if 64bit drivers are available,**[/COLOR] 64bit system is always a better choice.

---

### Post by uRock on 2010-06-03
I think if they made Lubuntu for 64bit, it would prove me wrong. So far 32bit Peppermint outruns Ubuntu on my system.

---

### Post by jocko on 2010-06-03
> **uRock said:**
> So far 32bit Peppermint outruns Ubuntu on my  system.
So far a 50 hp motorcycle outruns a 250 hp bus? Are you surprised?
Either strip the bus (ubuntu) down to the same weight as the motorcycle (peppermint), or put some extra weight on the motorcycle. Then compare their performance.
Or even better: put a 250 hp engine on the motorcycle (=make peppermint 64 bit) and a 50 hp engine on the bus (= make ubuntu 32 bits).

> **uRock said:**
> I think if they made Lubuntu for 64bit, it would prove me wrong.
Prepared to be proven wrong. It's just one command away:
```
sudo apt-get install lubuntu-desktop
```But to make the comparison to 32 bit lubuntu fair, you would probably need to do a minimal install of ubuntu 64 bit and install lubuntu-desktop from there to make the two systems as identical as possible.

---

### Post by uRock on 2010-06-03
> **jocko said:**
> So far a 50 hp motorcycle outruns a 250 hp bus? Are you surprised?
Either strip the bus (ubuntu) down to the same weight as the motorcycle (peppermint), or put some extra weight on the motorcycle. Then compare their performance.


Prepared to be proven wrong. It's just one command away:
```
sudo apt-get install lubuntu-desktop
```
But to make the comparison to 32 bit lubuntu fair, you would probably need to do a minimal install of ubuntu 64 bit and install lubuntu-desktop from there to make the two systems as identical as possible.

The Lubuntu team specifically designed their packages for 32bit. Though it may work, there are still too many bugs in the wild. I would love to see it built for 64bit systems.

---

### Post by v1ad on 2010-06-03
even if i had 2gb of ram i would still install 64 bit, please stop using the reference of more than 4 gigs. 32 bit supports ram all the way up 2 like 3.7 gb in windows not sure if they made something different in ubuntu. if your processor is 64 bit, install 64 bit for the maximum that you can get out of your computer.

(warning was drinking during this post...)

---

### Post by gradinaruvasile on 2010-06-03
Well maybe in ideal cases there is speed improvement, but for all round use it doesnt seem to worth it. Many 64 bit programs are not written right (if they even have 64-bit versions) also drivers tend to have 64-bit specific problems.
This is maybe because most people use 32 bit systems and the bugs are found more rapidly. Nonetheless the fact is thet some programs require extra fiddling with libraries etc to make them work in 64 bit environment in essentially 32-bit emulation mode (that means there is little, if any, speed improvement).
The bottom line is that 64-bit is faster in a purely 64-bit environment, but in real world this is not the case because the aforementioned sloppy application designers.
And i think the memory usage is higher in 64-bit applications.

I personally dont run specific benchmarks to see how fast my computer is - i only look at the touch and feel and responsiveness of the OS in general - that is the real world test. And i have not seen any visible improvements in 64-bit versions i tried briefly.


BTW 32-bit Linux can use 4 GB RAM - and it seems also that can access all 4GB of it  and up to 64 GB unlike Windows (including vista/7)  - just use the "bigmem" kernels.

---

### Post by varunendra on 2010-06-03
> **jocko said:**
> So far a 50 hp motorcycle outruns a 250 hp bus? Are you surprised?Can't help laughing my head off!!:):):)

> **v1ad said:**
> even if i had 2gb of ram i would still install 64 bit, please stop using the reference of more than 4 gigs. 32 bit supports ram all the way up 2 like 3.7 gb in windows not sure if they made something different in ubuntu. if your processor is 64 bit, install 64 bit for the maximum that you can get out of your computer.

(warning was drinking during this post...)True! I installed Win7-64bit on a system with 1GB RAM a month ago & so far it is working as smooth as it was with 32bit version. It mainly runs the following: Firefox, VLC for VCD/DVD playing, Avira Antivirus, Foxit Reader, DaemonTools, Nero, WinRAR, etc. And yes, all of these applications are 32bit versions!
(CLARIFICATION: Was NOT drinking during this post:) )

> **gradinaruvasile said:**
> The bottom line is that 64-bit is faster in a purely 64-bit environment, but in real world this is not the case because the aforementioned sloppy application designers. Maybe you're right. But in the above example of mine, I didn't notice any slow down either.

Undoubtedly the support for 64bit is accelerating day-by-day. But maybe I'm being over-optimistic!

---

### Post by Grenage on 2010-06-03
Bear in mind that the article is 6 years old.

---

### Post by varunendra on 2010-06-03
> **Grenage said:**
> Bear in mind that the article is 6 years old.

And the support for 64bit has been growing all the while. It'll soon be a default standard.
I think this thread can become really valuable if we can share some real world examples & experience rather than sharing views & opinions.

---

### Post by fuzzylogic25 on 2010-09-02
I think it is time i write my opinion on all this, which i do believe to be accurate. give me a few weeks as I am quite busy sorry!

---

### Post by Termaim on 2010-09-03
Ok, so I'm getting ready to do a clean / install of 10.04 from 8.10 32bit, I have a separate /home partition that I won't be formatting.  Should I switch to 64 bit at the same time, or will the /home partition create issues?  I'm running on an Athlon 64 4800+, 2GB ddr2, and a GeForce GT 240.  Would I need to redo my wine install for the 64 bit version, etc?  I don't know enough about actually running a 64bit OS (which is the only reason I didn't install 64bit 8.04 a couple years ago... didn't want compatability issues with vid/sound card drivers, and wine, etc as I use my machine for feeding my WoW and Eve Online addictions ;) )  Anyway, any suggestions would be awesome.  Thanks in advance.

---

### Post by varunendra on 2010-09-03
> **Termaim said:**
> Ok, so I'm getting ready to do a clean / install of 10.04 from 8.10 32bit, I have a separate /home partition that I won't be formatting.  Should I switch to 64 bit at the same time, or will the /home partition create issues?  I'm running on an Athlon 64 4800+, 2GB ddr2, and a GeForce GT 240.  Would I need to redo my wine install for the 64 bit version, etc?  I don't know enough about actually running a 64bit OS (which is the only reason I didn't install 64bit 8.04 a couple years ago... didn't want compatability issues with vid/sound card drivers, and wine, etc as I use my machine for feeding my WoW and Eve Online addictions ;) )  Anyway, any suggestions would be awesome.  Thanks in advance.
Can't say precisely about 32bit Vs 64bit version. It depends upon your available hardware and your software requirements. I'd suggest to make a detailed search/query regarding Ubuntu 64bit support specifically for your graphic / network cards, and in general for the applications you need.

Adobe Flash player for example, isn't good enough yet for 64bit Ubuntu as far as I know, and have noticed on the forums issues regarding proprietary drivers for some graphic/network cards on a 64 bit system.

As you are going to make a clean install (which is a good idea) I'd suggest to make a live installation on a USB thumb drive first, update it and do whatever you want with your (to be) native install, and see if it supports everything you need. If it satisfies you, you know your answer then, else try 32 bit and compare both yourself. I think this is the best thing about Ubuntu that you have chance to try everything before performing any critical change.

As for a separate /home compatibility, see this-
> **oldfred said:**
> The boot partition is just where the boot files  are including most of grub. But grub (or a boot loader) has to be in the  MBR to start booting. If that boot loader cannot directly boot the  kernel in another partition then you have to have another boot loader in  that partitions boot sector or PBR.

I do not believe in sharing /home either. Some do it and if the verisons  are all the same it will mostly work. If upgrading from one version to  another it is fine for the new verision will update settings. But if you  have systems using different versions of software you may get  conflicts. My /home is only about 1GB of mostly hidden folders &  settings as all my data is in a /data partition (including firefox &  thunderbird profiles and some other (normally) hidden data folders). 

I do believe in creating a /data partition and moving all your data  folders to that partition if you have multiple systems. Then you have no  conflicts and can easily mount your data in each system. I use linking  after mounting it.

Hope that helps.

---

