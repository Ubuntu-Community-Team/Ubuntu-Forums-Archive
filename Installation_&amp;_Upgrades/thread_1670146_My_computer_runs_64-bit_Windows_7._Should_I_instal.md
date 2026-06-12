---
title: "My computer runs 64-bit Windows 7. Should I install 64-bit Ubuntu?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by sirspazzolot on 2011-01-18
Or are there things that won't work with 64-bit Ubuntu? What are some pros and cons?

---

### Post by wkulecz on 2011-01-18
Unless you have, or plan to install, more than 4GB of RAM 64-bit offers no advantages.

OTOH 64-bit is pretty painless these days, but... without more than 4GB of RAM for the 64-bit system to really take advantage of you get net zero benefit for the potential risk.

---

### Post by Saghaulor on 2011-01-18
> **sirspazzolot said:**
> Or are there things that won't work with 64-bit Ubuntu? What are some pros and cons?

You won't notice much of a difference. There is a difference, but like I said, it's not very noticeable. 

That being said, however, some vendors only support 32 bit architectures. So sometimes installing 32 bit apps in 64 bit linux can be a real chore.

Also, if you have more that 4gbs of ram, then I would recommend 64 bit otherwise the remaining available ram won't be used. 32 bit processing can only use up to something like 3.5gb of ram.

---

### Post by Saghaulor on 2011-01-18
> **sirspazzolot said:**
> Or are there things that won't work with 64-bit Ubuntu? What are some pros and cons?

You won't notice much of a difference. There is a difference, but like I said, it's not very noticeable. 

That being said, however, some vendors only support 32 bit architectures. So sometimes installing 32 bit apps in 64 bit linux can be a real chore.

Also, if you have more that 4gbs of ram, then I would recommend 64 bit otherwise the remaining available ram won't be used. 32 bit processing can only use up to something like 3.5gb of ram.

---

### Post by Saghaulor on 2011-01-18
> **sirspazzolot said:**
> Or are there things that won't work with 64-bit Ubuntu? What are some pros and cons?

You won't notice much of a difference. There is a difference, but like I said, it's not very noticeable. 

That being said, however, some vendors only support 32 bit architectures. So sometimes installing 32 bit apps in 64 bit linux can be a real chore.

Also, if you have more that 4gbs of ram, then I would recommend 64 bit otherwise the remaining available ram won't be used. 32 bit processing can only use up to something like 3.5gb of ram.

---

### Post by sirspazzolot on 2011-01-18
Alright. I have 4GB and I don't plan to add more to my laptop. That makes things simpler, I already have a zillion 32-bit LiveCDs so now I don't need to make another. Thanks!

---

### Post by Saghaulor on 2011-01-18
Sorry about the multiple responses. There seems to be something lagging in the forums.

---

### Post by wkulecz on 2011-01-18
Yeah the forums are just this side of unusable today :(

Having lots of troubles today too.

---

### Post by jocko on 2011-01-18
> **wkulecz said:**
> Unless you have, or plan to install, more than 4GB of RAM 64-bit offers no advantages.

OTOH 64-bit is pretty painless these days, but... without more than 4GB of RAM for the 64-bit system to really take advantage of you get net zero benefit for the potential risk.
This is pure nonsense. A 64 bit cpu will perform better with a 64 bit os than with a 32 bit os, even if you have below 4 gb of ram. The ability to use more ram is just ONE of the benefits with 64 bit computing.

Not sure where everybody gets the outdated idea that 64 bit is still lagging behind on available software. I've been using 64 bit ubuntu since 7.04, and most of the problematic software was fixed with the 7.04 to 7.10 upgrade. Since then, the only remaining problem has been the poor performance of the 32 bit flash plugin running in a wrapper. But that's no longer any problem since adobe released their 64 bit flash plugin (still in beta, but working well).

@sirspazzalot: If you have 4 Gb ram, you will need to install 64 bit ubuntu to be able to use it all (unless you install a pae kernel, which will give you all ram back but probably degrade performance)...

---

### Post by sirspazzolot on 2011-01-18
I'm not saying I don't believe you, but I don't see why a 32-bit OS wouldn't run. Even if I do need a special kernel or whatever, I'm sure the Ubuntu installer will factor that in and such. And, seeing as how a huge portion of Windows software doesn't work on 64-bit, it wouldn't surprise me if it's the same situation for Linux. I'm not starting a Windows Vs. Linux debate, either. Honestly, I don't do anything that intense in Linux since I'm not a particularly magical programmer or anything, so now that I think about it, I should stick with 32-bit for convenience.

Thanks for the answers. :D

---

### Post by hansheijmans on 2011-01-18
I agree with jocko. My somewhat aged system has definitely benefit from using 64-bit os with regards to performance!

Nowadays you will find most software in the Ubuntu repositories and third party software which is suitable for 64-bit architecture (unlike Windows software ;))

By the way, why create zillions of Live CDs if you can create just one Live USB pen drive?

---

### Post by sirspazzolot on 2011-01-18
My friends watch too much porn and I always happen to be there when their computers finally die so I get a CD, burn Ubuntu to it, and install it for them. They have no use for the CD so I take it. They never let me use their flash drives since blah blah blah schoolwork blah blah bank information. I think that just means more porn. This has happened four times since 10.10 was released.

---

### Post by wmcbrine on 2011-01-18
I also agree with jocko, and will add that I've been running 64-bit for over five years now. The only problems used to be with Flash and Java, but those have been solved long since.

> **sirspazzolot said:**
> I'm not saying I don't believe you, but I don't see why a 32-bit OS wouldn't run.I don't think anyone has said that it wouldn't. But the 64-bit OS runs better.

> *And, seeing as how a huge portion of Windows software doesn't work on 64-bit, it wouldn't surprise me if it's the same situation for Linux.*It's *not* the same situation for Linux. Mainly because we run mostly open source software, which can be and is routinely rebuilt for platforms that its authors never even heard of. (Flash and Java were exceptions precisely because they *weren't* open. Java is now semi-open, and Flash finally got 64-bit a while ago, although it's still a laggard.)

Linux has been 64-bit-ready for a long, long time now. 64-bit is not a second-class platform for Linux.

---

### Post by sirspazzolot on 2011-01-18
> **jocko said:**
> 
@sirspazzalot: If you have 4 Gb ram, you will need to install 64 bit ubuntu to be able to use it all (unless you install a pae kernel, which will give you all ram back but probably degrade performance)...

Perhaps I misunderstood, but this is what I thought was saying that a 32-bit OS wouldn't run. I suppose I could get more opinions. I forgot about the open-source community making things work. It seems the choice between 32-bit and 64-bit is less black-and-white than I thought, heheh

---

### Post by travissparks1307 on 2011-01-18
If you're running Windows 7 in 64 bit, then you should definitely run Ubuntu in 64 bit. I have noticed a BIG difference in performance, despite what many have told me. I have compared 32 bit and 64 bit side by side on the same machine, and 64 bit wins hands down. I have had some very minor compatibility problems, but they were, *very* minor. Usually its just a matter of making sure you have the the 32 bit compatibility libraries, and if a package says "wrong architecture" just run it with "sudo dpkg --force whatever.deb" I have had ZERO problems and SUBSTANTIAL performance increase, but like all things, YMMV. 

Bottom line: 64-bit Ubuntu

---

### Post by oldos2er on 2011-01-18
If you plan on watching Youtube or similar sites, install 64-bit flash, which is not yet in the repos. Click FlashAid in my sig.

---

### Post by sirspazzolot on 2011-01-18
Awesome. I hope it's easy to add into chrome. More opinions? :)

---

### Post by travissparks1307 on 2011-01-19
If you're using Google Chrome, then you don't have to do anything. Chrome has a built-in implementation of Flash and it works on 64 bit "out-of-the-box". Have fun!

---

### Post by wmcbrine on 2011-01-20
> **sirspazzolot said:**
> Perhaps I misunderstood, but this is what I thought was saying that a 32-bit OS wouldn't run.Nope. He's just saying that you need a 64-bit OS to use all of the RAM in a 4 GB system. ("use it all", as he wrote, not "use it at all", as you might be reading it.) A 32-bit OS will run, but utilize somewhat less than 4 GB, due to reserved address space. Or you can go back to the dark days of segment registers (using the "PAE kernel"), which probably isn't really that bad, but certainly not as good as going 64-bit.

> **travissparks1307 said:**
> I have noticed a BIG difference in performance, despite what many have told me.+1

---

### Post by wmcbrine on 2011-01-20
> **sirspazzolot said:**
> Perhaps I misunderstood, but this is what I thought was saying that a 32-bit OS wouldn't run.Nope. He's just saying that you need a 64-bit OS to use all of the RAM in a 4 GB system. ("use it all", as he wrote, not "use it at all", as you might be reading it.) A 32-bit OS will run, but utilize somewhat less than 4 GB, due to reserved address space. Or you can go back to the dark days of segment registers (using the "PAE kernel"), which probably isn't really that bad, but certainly not as good as going 64-bit.

> **travissparks1307 said:**
> I have noticed a BIG difference in performance, despite what many have told me.+1

---

### Post by wmcbrine on 2011-01-20
> **sirspazzolot said:**
> Perhaps I misunderstood, but this is what I thought was saying that a 32-bit OS wouldn't run.Nope. He's just saying that you need a 64-bit OS to use all of the RAM in a 4 GB system. ("use it all", as he wrote, not "use it at all", as you might be reading it.) A 32-bit OS will run, but utilize somewhat less than 4 GB, due to reserved address space. Or you can go back to the dark days of segment registers (using the "PAE kernel"), which probably isn't really that bad, but certainly not as good as going 64-bit.

> **travissparks1307 said:**
> I have noticed a BIG difference in performance, despite what many have told me.+1

---

### Post by ste_bran on 2011-01-21
Since 64-bit is the way to go, why does this download site still have the 32-bit version as recommended?    [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by akand074 on 2011-01-21
> **ste_bran said:**
> Since 64-bit is the way to go, why does this download site still have the 32-bit version as recommended?    [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

64 bit is definitely the way to go. They recommend 32-bit because it's still perceived as (and probably still is in some cases) more stable. Better for businesses and similar applications. But for a regular user, it won't even matter. I've used 64 bit Ubuntu for over 2 years as my primary OS. Not a single architecture related problem. 64 bit Ubuntu even has the 32 bit libraries if there are 32 bit only software.

---

