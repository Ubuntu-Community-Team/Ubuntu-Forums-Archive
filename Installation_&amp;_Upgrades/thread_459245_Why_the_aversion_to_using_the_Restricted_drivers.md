---
title: "Why the aversion to using the Restricted drivers?"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-05-30
Hello all.  I have been doing a lot of reading here and it seems that many here on the forum have a big aversion to using the Restricted drivers in the Restricted driver manager on Feisty.

I have (4) PCs running Feisty (Radeon XPress 200M, 7600GT, 5700 Ultra, GF2 GTS) and all run fine with the restricted drivers for the video card.  Is there some bad thing about using the Restricted drivers?  Since I do all my gaming on my XP partition I don't need the absolute latest 3D drivers for my video card.

Also when the new kernel was upgraded (-16) I had no ill effects on any of the machines.

Thanks

---

### Post by Yoooder on 2007-05-30
> **stchman said:**
> Hello all.  I have been doing a lot of reading here and it seems that many here on the forum have a big aversion to using the Restricted drivers in the Restricted driver manager on Feisty.

I have (4) PCs running Feisty (Radeon XPress 200M, 7600GT, 5700 Ultra, GF2 GTS) and all run fine with the restricted drivers for the video card.  Is there some bad thing about using the Restricted drivers?  Since I do all my gaming on my XP partition I don't need the absolute latest 3D drivers for my video card.

Also when the new kernel was upgraded (-16) I had no ill effects on any of the machines.

Thanks

The most-commonly cited issue with them is that they aren't open-source.  So they aren't *pure*.  Personally, I use them for my nVidia card because it's the only way I can use TwinView and hardware acceleration.

So far I haven't heard of any particular stability/security/efficiency issues with the Restricted modules, but I could be wrong.  I would say use them if you need them and aren't concerned with having a *pure* Linux box.

---

### Post by stchman on 2007-05-30
> **Yoooder said:**
> The most-commonly cited issue with them is that they aren't open-source.  So they aren't *pure*.  Personally, I use them for my nVidia card because it's the only way I can use TwinView and hardware acceleration.

So far I haven't heard of any particular stability/security/efficiency issues with the Restricted modules, but I could be wrong.  I would say use them if you need them and aren't concerned with having a *pure* Linux box.

"Pure"?  Ok.

I am a "just works" kind of person.  If it works and does not cost me money I will use it.

I look at it this way.  I purchased the video card so therefore I am entitled to the drivers that nvidia and ATI publish.

I am sometimes confused but I think I have drawn this conclusion.  When synaptic says that a driver is non-free that means it is not open source not that is is going to cost you money.

---

### Post by matthew on 2007-05-30
> **stchman said:**
> Hello all.  I have been doing a lot of reading here and it seems that many here on the forum have a big aversion to using the Restricted drivers in the Restricted driver manager on Feisty.

Is there some bad thing about using the Restricted drivers?There is no problem with them. I used the Restricted Drivers Manager to install the driver for my ATI card. It works, it's easy.

---

### Post by aysiu on 2007-05-30
> **stchman said:**
> 
I look at it this way.  I purchased the video card so therefore I am entitled to the drivers that nvidia and ATI publish. And no one's stopping you from installing those drivers. In fact, with Feisty, [installation of them in Ubuntu is easier than ever before.](http://www.psychocats.net/ubuntu/nvidia)

> I am sometimes confused but I think I have drawn this conclusion.  When synaptic says that a driver is non-free that means it is not open source not that is is going to cost you money. I was confused by that, too, the first time I used Synaptic Package Manager, but I quickly figured it out.

---

### Post by christhemonkey on 2007-05-30
If things go wrong, then there is no way of debugging anything as it could have been a bug in the closed drivers,

there is no way of telling.

The kernel people dont take bug reports from people who use closed drivers modules as closed drivers 'taint' the kernel.


And generally the closed source drivers could be doing anything, calling home, giving out your systems details, who knows!! (apart from nvidia/ati and people...)


And they also go against the spirit of all the open source stuff, i mean why have all this great Free stuff and then taint it with closed source drivers.



(all that said i do use the closed source nvidia drivers, just because they are useful and i like whizzy 3D acceleration and playing games. Never mind...)

---

### Post by aysiu on 2007-05-30
Ultimately, these ideological battles have little direct impact on the user, but the ideological war has a big impact.

Unless Linux developers are able to create (and they need *users* to help test and debug) working open source drivers, users are at the mercy of Nvidia and other companies. Let's say that tomorrow Nvidia decided "We're not going to make a Linux driver any more. We are also forbidding distribution of our previously published Nvidia drivers" Well, what are Linux users with Nvidia cards going to do? They'll be stuck with an underdeveloped [*nouveau* driver](http://nouveau.freedesktop.org/wiki/)... or just give up altogether and go back to Windows.

It's much the same predicament we were caught in when Adobe was slow in updating Flash for Linux. Most Flash sites were requiring Flash 8 or 9, but the Linux Flash was still 7 for almost a half year before the Linux port of Flash 9 was released.

It's also like Firefox v. Internet Explorer three years ago. A lot of users gave up on Firefox because there were a lot of sites that weren't Firefox-compatible (the ones designed to work only in IE). It's a good thing a lot of people stuck with Firefox, though. Now it's at 25% of the browser market in some parts of the world, and any web developer who makes an IE-only website is just turning away potential customers or visitors. And now you actually have browser choice.

Of course, people love to sacrifice short-term "freedom" for long-term vendor lock-in. Myself included. I don't want to be all high and mighty. I'm as proprietary-dependent as most users are.

---

### Post by stchman on 2007-05-30
> **christhemonkey said:**
> If things go wrong, then there is no way of debugging anything as it could have been a bug in the closed drivers,

there is no way of telling.

The kernel people dont take bug reports from people who use closed drivers modules as closed drivers 'taint' the kernel.


And generally the closed source drivers could be doing anything, calling home, giving out your systems details, who knows!! (apart from nvidia/ati and people...)


And they also go against the spirit of all the open source stuff, i mean why have all this great Free stuff and then taint it with closed source drivers.



(all that said i do use the closed source nvidia drivers, just because they are useful and i like whizzy 3D acceleration and playing games. Never mind...)

I can see your point.  On the other hand if Nvidia or ATI would be transmitting phone numbers, SSNs, bank account info, etc. people in the open source community would have found this out.  I would not used Restricted drivers from Nigerian spammers, but I believe we can trust Nvidia and ATI to not steal from us.

I use 2 restriced drivers on my laptop, (Atheros and ATI).  They work and there have been no reports of identity theft using them.

---

### Post by stchman on 2007-05-30
> **aysiu said:**
> Ultimately, these ideological battles have little direct impact on the user, but the ideological war has a big impact.

Unless Linux developers are able to create (and they need *users* to help test and debug) working open source drivers, users are at the mercy of Nvidia and other companies. Let's say that tomorrow Nvidia decided "We're not going to make a Linux driver any more. We are also forbidding distribution of our previously published Nvidia drivers" Well, what are Linux users with Nvidia cards going to do? They'll be stuck with an underdeveloped [*nouveau* driver](http://nouveau.freedesktop.org/wiki/)... or just give up altogether and go back to Windows.

It's much the same predicament we were caught in when Adobe was slow in updating Flash for Linux. Most Flash sites were requiring Flash 8 or 9, but the Linux Flash was still 7 for almost a half year before the Linux port of Flash 9 was released.

It's also like Firefox v. Internet Explorer three years ago. A lot of users gave up on Firefox because there were a lot of sites that weren't Firefox-compatible (the ones designed to work only in IE). It's a good thing a lot of people stuck with Firefox, though. Now it's at 25% of the browser market in some parts of the world, and any web developer who makes an IE-only website is just turning away potential customers or visitors. And now you actually have browser choice.

Of course, people love to sacrifice short-term "freedom" for long-term vendor lock-in. Myself included. I don't want to be all high and mighty. I'm as proprietary-dependent as most users are.

Nvidia and ATI COULD stop supporting Linux, but they won't.  There are enough Linux users out there that it benefits them to write drivers for their cards for Linux.

Nvidia and ATI are in the business to make money.  That being said they make money by selling hardware.  They don't care what OS you use as long as you use their hardware.  With Linux becoming more and more popular on desktops you will see smaller hardware manufacturers start supporting Linux.

I make it a point to email hardware manufacturers (Linksys - Broadcom) that I spent my money on their competition since their competition supports Linux.  The fans of Linux need to all send emails to hardware manufacturers that don't support Linux.

I migrated from XP to Linux and never did I have to pay for drivers.  I moved to Linux because the OS and applications XP uses are very expensive for what they offer.  The drivers in XP always worked, I did not want to spend $200 on Vista.

Sorry for getting off on a tangent.

---

### Post by nutz on 2007-05-30
I use them because they make my Nvidia card run it's best. I wish they were open but until an open alternative provides the same or better results I am willing to make the compromise.

---

### Post by aysiu on 2007-05-30
The point still stands that you are at their mercy and good graces.

If they suddenly get new management who decide "Nah, there aren't enough Linux users to keep up this project," then you won't have any say in the matter, and other Linux users won't either.

The number of Linux users is growing slowly, and they should try to spend their money on Linux-compatible hardware, but they are not really that significant a group as far as lot of hardware companies are concerned.

---

### Post by nutz on 2007-05-31
> **aysiu said:**
> The point still stands that you are at their mercy and good graces.

If they suddenly get new management who decide "Nah, there aren't enough Linux users to keep up this project," then you won't have any say in the matter, and other Linux users won't either.

The number of Linux users is growing slowly, and they should try to spend their money on Linux-compatible hardware, but they are not really that significant a group as far as lot of hardware companies are concerned.

That is really sad because in the end driver support has a lot of weight in my hardware buying decision. If it isn't supported by Linux I am just not interested...

---

### Post by aysiu on 2007-05-31
> **nutz said:**
> That is really sad because in the end driver support has a lot of weight in my hardware buying decision. If it isn't supported by Linux I am just not interested...
Which is why it's in your best interests to buy hardware that is supported directly by the Linux kernel instead of through third-party closed-source drivers (like Nvidia's).

---

### Post by az on 2007-05-31
> **stchman said:**
> Nvidia and ATI COULD stop supporting Linux, but they won't.  

My software modem did not work in linux in 2000.  I bought a Conexant modem because their driver was well developed and actively supported by a community of developers.

A few years later, they became Linuxant and started to sell the driver.  The free version was no longer supported and the linux driver costs a little more than the hardware itself - and that won't even survive many kernel revisions;  you have to buy the driver all over again every year or two.

That's the business model that Conexant chose for linux - sell some company the contract to maintain the linux drive.  You think ATI or Nvidia wounldn't do that too?  Sounds like a nightmare to me.


> **nutz said:**
> That is really sad because in the end driver support has a lot of weight in my hardware buying decision. If it isn't supported by Linux I am just not interested...

What's really sad is that the linux community is really good at maintaining and improving hardware drivers.  The companies could conceivably release specs (and possible "firmware") and drastically reduce their costs of developing and supporting a linux driver.  Using firmware does not taint the kernel.  The quality of the linux driver would be second to none.  Everybody wins!

Using a proprietary driver in a FLOSS OS is a temporary solution.  It is a sub-par solution to a problem that does not even really exist.

When you get down to it, FLOSS ideology is based on dealing with real-world problems.  If all software was FLOSS, life would be so much simpler.  The hardware vendors should not be interested in selling the software that goes along with their hardware, they should be concerned about selling their hardware.  Who is really winning out here?

---

### Post by stchman on 2007-05-31
> **az said:**
> My software modem did not work in linux in 2000.  I bought a Conexant modem because their driver was well developed and actively supported by a community of developers.

A few years later, they became Linuxant and started to sell the driver.  The free version was no longer supported and the linux driver costs a little more than the hardware itself - and that won't even survive many kernel revisions;  you have to buy the driver all over again every year or two.

That's the business model that Conexant chose for linux - sell some company the contract to maintain the linux drive.  You think ATI or Nvidia wounldn't do that too?  Sounds like a nightmare to me.




What's really sad is that the linux community is really good at maintaining and improving hardware drivers.  The companies could conceivably release specs (and possible "firmware") and drastically reduce their costs of developing and supporting a linux driver.  Using firmware does not taint the kernel.  The quality of the linux driver would be second to none.  Everybody wins!

Using a proprietary driver in a FLOSS OS is a temporary solution.  It is a sub-par solution to a problem that does not even really exist.

When you get down to it, FLOSS ideology is based on dealing with real-world problems.  If all software was FLOSS, life would be so much simpler.  The hardware vendors should not be interested in selling the software that goes along with their hardware, they should be concerned about selling their hardware.  Who is really winning out here?

I have never heard of people paying for drivers for hardware they purchased.  As far as your modem there are a lot of 56K hardware external modems that work out of the box in Linux.

I don't believe that nvidia or ATI will start to sell their drivers to Linux folks only.  They both know that Linux users would not pay for something like that so it would be an absolute fruitless proposition.  I could see nvidia and ATI no longer support their cards under Linux but not start selling drivers.

---

### Post by az on 2007-05-31
> **stchman said:**
> I have never heard of people paying for drivers for hardware they purchased.  .

[https://www.linuxant.com/store/](https://www.linuxant.com/store/)

the sob story:
[https://www.linuxant.com/store/faq.php](https://www.linuxant.com/store/faq.php)


> **stchman said:**
> 
As far as your modem there are a lot of 56K hardware external modems that work out of the box in Linux..

Of course.  But that is not an acceptable answer to linux hardware support.


> **stchman said:**
> 
I don't believe that nvidia or ATI will start to sell their drivers to Linux folks only.  They both know that Linux users would not pay for something like that so it would be an absolute fruitless proposition.  I could see nvidia and ATI no longer support their cards under Linux but not start selling drivers.

Considering the above, and that they have been at it for several years, you still think that?

---

### Post by jrusso2 on 2007-05-31
Linux has been held hostage by a group of FSF zealots that have turned Linux into some kind of Holy War instead of making it work for regulars users.

This is what has prevented Linux's growth on the desktop more then Microsoft even.

---

### Post by az on 2007-06-01
> **jrusso2 said:**
> Linux has been held hostage by a group of FSF zealots that have turned Linux into some kind of Holy War instead of making it work for regulars users..

Software freedom is not a holy war.  That's just what people call it when they don't have a clue.  People used to ridicule racial equality, too.

Software freedom is about preserving your freedoms.  It is not about telling anyone what software they should use.

> **jrusso2 said:**
> 
This is what has prevented Linux's growth on the desktop more then Microsoft even.

Really?  If your theory is correct, then proprietary distros like Xandros which have shipped proprietary software, proprietary drivers and multimedia codecs from the start should have taken over the world.  They have not.  Probably because it's the free-libre software development model that makes the software go Zoom!

That development model makes for better software.  Including closed-source, binary-only, closed format software in your distro is sometimes necessary, but only slows down the progress of free-libre open source software.

---

### Post by aysiu on 2007-06-01
> **az said:**
> 
Really?  If your theory is correct, then proprietary distros like Xandros which have shipped proprietary software, proprietary drivers and multimedia codecs from the start should have taken over the world.  They have not. Don't forget PCLinuxOS, Linspire, and Mepis.

---

### Post by Lord Illidan on 2007-06-01
I use the restricted drivers myself. I'd like to see opensource drivers, but I don't think they will happen anytime soon.

Also, with regards to Nvidia or ATI deciding to stop distribution of the driver, the same thing could happen with Opensource drivers if there is a lack of interest. Just because it is opensource doesn't mean that it doesn't have bugs, or that it doesn't sneak on you. Do **you** check any opensource software for bugs? Or for sneaking on you?

---

### Post by aysiu on 2007-06-01
> **Lord Illidan said:**
> I use the restricted drivers myself. I'd like to see opensource drivers, but I don't think they will happen anytime soon.

Also, with regards to Nvidia or ATI deciding to stop distribution of the driver, the same thing could happen with Opensource drivers if there is a lack of interest. Just because it is opensource doesn't mean that it doesn't have bugs, or that it doesn't sneak on you. Do **you** check any opensource software for bugs? Or for sneaking on you?
You're absolutely right, but  here's the difference:

**Closed source**
If you don't want to check the code, you don't check it.
If support discontinues, there's nothing you can do about it as a user.
If you *do* want to check the code, you can't check it.
If support discontinues, there's *nothing* you can do about it as a developer.

**Open source**
If you don't want to check the code, you don't check it.
If support discontinues, there's very little you can do about it as a user (apart from hiring a developer to code or learning to code yourself)
If you want to check the code, you *can* check it.
If support discontinues, there *is* something you can do about it as a developer.

So open source mainly benefits developers, but it still has more benefits than closed source. And, truth be told, if a video card is a popular one, there will be developer interest in it.

---

### Post by az on 2007-06-01
> **Lord Illidan said:**
> 
Also, with regards to Nvidia or ATI deciding to stop distribution of the driver, the same thing could happen with Opensource drivers if there is a lack of interest. 

In just about all cases, if a piece of hardware is popular and had free-libre drivers in the linux kernel, it will continue to be properly supported.  I have not heard of a case where a popular (not obsolete) device stopped working because it was abandoned by kernel developers.

And that's because it is a collaborative effort.  Linux developers numbers dwarf all other Unix kernel developers put together.  Why do you think BSD does not have as impressive desktop hardware support as linux does?



> **Lord Illidan said:**
> 
Just because it is opensource doesn't mean that it doesn't have bugs, or that it doesn't sneak on you. Do **you** check any opensource software for bugs? Or for sneaking on you?


I'm not a mechanic, but I'd never buy a car that had a hood welded shut, or that could only be opened by a special key owned by the manufacturer.

I like having the choice of bringing my car for service anywhere I want.  The same advantage applies to FLOSS and the non-developer.  If I would want to modify some code and I didn't have the skill, I would'nt have to look very far, nor get permission from the "owner" of the software.

Yes, all software has bugs.  Nothing new here.

---

### Post by dwingojr on 2007-06-01
Just like Nutz, I use the Nvidia driver on my Dell D8xx series. I wanted to run Beryl, and needed the GL thing poppin' to use that. It's not just cool, it is pretty handy when I'm running a couple of Virtual machines performing admin duties. 

A lot of valid points made here, especially with regards to driver support. I figure I bought the driver when I got the machine, so I don't have an ethical problem with it not being free (of cost). 

If you're a "just works" guy, I say go for it. If we were _*all*_ about "purity" we'd be using Unix and KDE.

---

### Post by aysiu on 2007-06-01
> **dwingojr said:**
> 
If you're a "just works" guy, I say go for it. If we were _*all*_ about "purity" we'd be using Unix and KDE. I don't think those are the only two options. And freedom isn't about purity (unless you're Richard Stallman). Freedom is about freedom. I care about software freedom because I believe it indirectly affects the end user immediately and directly affects the end user in the long term. At the same time, I am a "just works" guy, and I use proprietary software, as do 96% of forum members who hang out in the Community Cafe.

---

### Post by stchman on 2007-06-01
> **az said:**
> [https://www.linuxant.com/store/](https://www.linuxant.com/store/)

the sob story:
[https://www.linuxant.com/store/faq.php](https://www.linuxant.com/store/faq.php)




Of course.  But that is not an acceptable answer to linux hardware support.




Considering the above, and that they have been at it for several years, you still think that?

If hardware manufacturers start doing this, then we as Linux users will tell these companies that we will take our money elsewhere.

---

### Post by stchman on 2007-06-01
> **az said:**
> In just about all cases, if a piece of hardware is popular and had free-libre drivers in the linux kernel, it will continue to be properly supported.  I have not heard of a case where a popular (not obsolete) device stopped working because it was abandoned by kernel developers.

And that's because it is a collaborative effort.  Linux developers numbers dwarf all other Unix kernel developers put together.  Why do you think BSD does not have as impressive desktop hardware support as linux does?






I'm not a mechanic, but I'd never buy a car that had a hood welded shut, or that could only be opened by a special key owned by the manufacturer.

I like having the choice of bringing my car for service anywhere I want.  The same advantage applies to FLOSS and the non-developer.  If I would want to modify some code and I didn't have the skill, I would'nt have to look very far, nor get permission from the "owner" of the software.

Yes, all software has bugs.  Nothing new here.

While the car analogy is a good one, cars are still very proprietary.  If you buy a Toyota Corolla you are not going to be able to install a 460 Turbo Diesel engine in it.  Ford parts don't fit Chevys.  The code that controls the computer in your car is closed source proprietary.  DO we know for a fact that the computers on cars don't rat us out to the cops when we speed.

---

### Post by az on 2007-06-01
> **stchman said:**
> While the car analogy is a good one, cars are still very proprietary.  If you buy a Toyota Corolla you are not going to be able to install a 460 Turbo Diesel engine in it.  Ford parts don't fit Chevys.  . 

Yes, but you often can buy and original ford piece or go for a lower-cost part from a generic manufacturer.  You get the choice.

> **stchman said:**
> 
 DO we know for a fact that the computers on cars don't rat us out to the cops when we speed.

Actually, more and more vehicles record events and are able to play back the last few moments before an impact.  More and more cars come with satelite driver assistance hardware built-in...

---

### Post by lingnoi on 2007-06-20
There are plenty of reasons for having open source graphics drivers.

[LIST]
[*]Security - How can you audit the code if you can not see it?
[*]Faster Debugging Time - Increased knowledge of what the graphics driver does for developers means faster debugging time
[*]Runs on more platforms - There is no PPC version of the nvidia drivers
[*]Older card support - There is no support for older cards that have been dropped.
[*]Less bugs - The nvidia developers are very smart but more people looking at the code means less problems.
[*]Better Integration into the OS - An open source driver would just work without distribution problems.
[*]Possible advancement of features - Looking at the code would allow developers to stand on the shoulders of giants to do there small bit.
[/LIST]

This will never happen though unless projects like [Nouveau]("http://nouveau.freedesktop.org/wiki/") succeed because Nvidia will never release any source code. There are multiple reasons for this such as..

[LIST]
[*]They have patented code from other companies in their source code.
[*]They have signed contracts with the government, etc saying that their hardware works. If there was a problem found in the code they could get in trouble.
[*]They wouldn't be able to make you buy a new graphics card to keep receiving updates.
[*]Microsoft are paying them not to. (I am guessing)
[/LIST]

---

