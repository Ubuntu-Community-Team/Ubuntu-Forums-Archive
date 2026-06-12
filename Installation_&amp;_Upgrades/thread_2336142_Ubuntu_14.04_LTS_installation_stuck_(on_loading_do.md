---
title: "Ubuntu 14.04 LTS installation stuck (on loading dots)"
date: 2016-09-05
forum: Installation &amp; Upgrades
---

### Post by n.triple.a on 2016-09-05
Hello, I am currently trying to install Ubuntu (for a dual boot) on a new drive that I bought for my laptop (it is internal) but it gets stuck on the loading screen. This is the screen with the white and orange dots in it. The dots start changing color but when they are somewhat half white, half orange they all turn orange and then the installation won't respond to anything forcing me to do a force shut down on the machine. I am using a USB drive for this since my laptop does not have an optical drive. I have also tried downloading and burning the ISO time after time to no avail. However, I tried running the installation on another computer to see if it worked and it did right off the bat so that discards the USB or the ISO being the problem here. Could I get a suggestion here? Because I have been trying all weekend and am starting to give up. 


If this helps anyone, my computer is a Clevo Laptop with:


intel i7 6700HQ CPU @ 2.6GHz
Nvidia Geforce GTX 970
16 gb RAM
1 tb HDD
256 gb m.2 San Disk SSD (the one I want to install Ubuntu on)
480 gb m.2 MyDigitalSSD SSD (the one I have Windows installed on)

---

### Post by Bucky Ball on 2016-09-05
*Thread closed.*

Please don't post duplicate, triplicate, OR quadruplicate threads on the same topic. 

*And reopened. *

... as your three others have now been closed and the confusion is sorted out. Again, please stick to one thread on one topic, bump it after 12 hours if you get no action and patience is key. Repeated posting on the same topic will do nothing but dissipate community effort and attract staff attention. Reason? I have just spent five minutes cleaning this up only to see another staff member is doing the same.

Thanks for your understanding.

Now I can actually give you some support. :) When you boot the machine using the Ubuntu install media, USB or disk, and get to the purple screen with the icons at the bottom, press F6. You should get the options 'Try Ubuntu', 'Install Ubuntu', etc. Hit F6 again and a menu should pop-up. Choose the 'nomodeset' option and proceed to 'Try Ubuntu'. Success?

I haven't used this method for awhile so getting there might be slightly different now, but the bottom line is you want to be using the 'nomodeset' option to try or install Ubuntu. 

Let us know. If that works, you can install that way then install the correct NVidia drivers once you're installed.

I have virtually the same hardware as yours and an identical graphics card, the NVIDIA 970. CPU a 6700, but not the HQ, 16Gb RAM: yep.

* We are an international forum covering a lot of timezones. Therefore, the person who can help you may not have seen your thread yet or even be awake (I've just been away from the computer since an hour before your *first* thread about this, as an example). Again, patience is key here. If after 12 hours or so you haven't had any help, by all means, just post 'bump' in a new post on the thread and that will put your thread at the top of 'New posts' again. Be advised, though, that excessive bumping will attract the same as duplicate, triplicate and quadruplicate posting: staff attention. ;)

Good luck and let us know how you go.

---

### Post by sudodus on 2016-09-05
Interesting that NVIDIA 970 is working for you BB :-) I was interested in that card, but saw several web pages saying it does not work with linux. If I remember correctly, some of them are fairly recent and from our Ubuntu Forums. Please tell us some details:

- operating system (version and flavour of Ubuntu)
- graphics driver
- and if you think we need more information to succeed ...

---

### Post by Bucky Ball on 2016-09-05
> **sudodus said:**
> Interesting that NVIDIA 970 is working for you BB :-) I was interested in that card, but saw several web pages saying it does not work with linux. If I remember correctly, some of them are fairly recent and from our Ubuntu Forums. Please tell us some details:

- operating system (version and flavour of Ubuntu)
- graphics driver
- and if you think we need more information to succeed ...

Works faultlessly and with CUDA support. I've been editing and rendering video in Blender with it. Rocks. I have the ASUS Strix, which uses the GTX 970.

[LIST]
[*]OS is an odd one because I never use a standard install. Used to go with a mini and xfce4, more recently, this machine is running Xubuntu-core 16.04 LTS.
[*]The driver is the 361.42. It's right there in Addtional Drivers. No need to go hunting, compiling, downloading from third-parties. Doubt it makes any difference, but *_I'm using HDMI from the card. Wonder what the OP is using?_* ...
[*]Don't think there's anymore info needed, at least there's no more I can give. In my experience this card worked fine from the get go. Don't even remember having to use nomodeset, but this is a custom box so the hardware config combination is probably diff, even though some is identical. No idea about whether I'm using the same motherboard as OP, for instance. 
[/LIST]

Just a note. When I first set up this machine, I too went hunting about thinking I was going to need to jump through hoops to get graphics and other things happening. Basically, I just switched it on, it worked, I installed the driver from Additional Drivers and that, as they say, was that. Not sure what more I can add, but feel free to ask.

PS: I did design this box myself with Linux in mind and went to some effort to make sure all was going to work together and with Linux. Maybe that's the difference between myself and some of the users that are having issues. An off the shelf box that wasn't designed to run Linux in the first place. :-k From what I can see from the OP's hardware listed in the first post, their machine should work fine with Ubuntu, unless there's an unco-operative motherboard involved.

---

### Post by sudodus on 2016-09-05
Excuse my ignorance, but what is CUDA, and how can I provide CUDA support?

Yes, I can search the internet for it, but it might help several people, it you tell us here :-P

---

### Post by Bucky Ball on 2016-09-05
[Bang]("http://www.geforce.com/hardware/technology/cuda") and [bang]("https://en.wikipedia.org/wiki/CUDA"). Easier to read about there than me regurgitate here. :)

The first link pretty much says it all. The second pretty much confirms what the first one says and gives a few other details. :)

---

### Post by sudodus on 2016-09-05
Thank you :-)

I guess it means, that it comes with the graphics card, and *I need not provide any CUDA support*, for the graphics card to work.

---

### Post by Bucky Ball on 2016-09-05
> **sudodus said:**
> Thank you :-)

I guess it means, that it comes with the graphics card, and *I need not provide any CUDA support*, for the graphics card to work.

Correct. All taken care of by card and driver. :) 

I didn't even know about CUDA until *after* I was using the card then started to panic and furiously hunt for how to enable. It was simple. I set Blender to use CUDA in the config there! That is about the only thing. The app itself needs to know it's present and how to negotiate it *I think*. But we digress ...

Any luck, n.triple.a?

---

### Post by n.triple.a on 2016-09-05
> **Bucky Ball said:**
> Correct. All taken care of by card and driver. :) 

I didn't even know about CUDA until *after* I was using the card then started to panic and furiously hunt for how to enable. It was simple. I set Blender to use CUDA in the config there! That is about the only thing. The app itself needs to know it's present and how to negotiate it *I think*. But we digress ...

Any luck, n.triple.a?

Nope, I tried using nomodeset and it does proceed to the installation but it gets stuck at the "Preparing to Install" screen. I tried combinations of not ticking/ticking the "Install Third Party apps" and the "Install Updates", to no success. It just gets stuck in that particular screen. I tried going into "Try Ubuntu" and removing ubiquity (something I found on google) but nothing. I also let it sit to see if it just needed time, but nope, 4 hours and it was still on that screen. I am on the verge of giving up. 

Also, I want to install Ubuntu 14.04 LTS.

---

### Post by Bucky Ball on 2016-09-05
Ok. Not sure about 14.04 and that card. At least I can't confirm it. As I say, I have virtually the same setup as you and that is why I installed 16.04: very new hardware so taking no chances.

The drives: they are new? Or is the drive you are attempting to install on an old Win or other drive? Have you tried with the combination of nomodeset and untick third-party apps and updates (don't tick them anyway as you don't need them, can be problematic and install wrong drivers or ones you don't need - install what you need and where you need later).

At least we know nomodeset gets you somewhere and there will be others that can get you further, so don't give up yet (although I think I can speak for all of us when I say I understand your frustration). You've only been at it ten hours, at least here, and we are an international forum across a lot of timezones and with a lot of users. The person that can help you may not be awake yet! :)

BTW, if you have no action in 12 hours after the last post on your thread feel free to post 'bump' on the thread. That will advance it to the top of the 'new posts' list again.

---

### Post by n.triple.a on 2016-09-05
> **Bucky Ball said:**
> Ok. Not sure about 14.04 and that card. At least I can't confirm it. As I say, I have virtually the same setup as you and that is why I installed 16.04: very new hardware so taking no chances.

The drives: they are new? Or is the drive you are attempting to install on an old Win or other drive? Have you tried with the combination of nomodeset and untick third-party apps and updates (don't tick them anyway as you don't need them, can be problematic and install wrong drivers or ones you don't need - install what you need and where you need later).

At least we know nomodeset gets you somewhere and there will be others that can get you further, so don't give up yet (although I think I can speak for all of us when I say I understand your frustration). You've only been at it ten hours, at least here, and we are an international forum across a lot of timezones and with a lot of users. The person that can help you may not be awake yet! :)

BTW, if you have no action in 12 hours after the last post on your thread feel free to post 'bump' on the thread. That will advance it to the top of the 'new posts' list again.

The laptop itself is relatively new (one month old). It came with the 256 gb and the 1 tb. The 480 gb is like 2 days old. However, I already got the 480 gb to run Windows (via cloning) and formatted the 256gb one (it had Windows previously). Also, yes, I have indeed tried using nomodeset and not ticking any of the options. It still gets stuck in that screen

---

### Post by sudodus on 2016-09-05
+1 for a new version. I suggest that you start with ***Ubuntu 16.04.1 LTS amd64***, which works for Bucky Ball, and read his tips very carefully.

If it 16.04.1 LTS does not work, you can try the next version, still in the development phase. It might work better, because there are newer versions of the kernel, drivers etc. It is called ***Yakkety Yak***, and will be released in October as 16.10 (a short-lived version, but if it helps running the graphics ...). This version might have temporary problems for two more months. Because of the development things are changing a lot, and the different pieces of software do not always match.

Links:

[Ubuntu 16.04.1 LTS amd64](http://www.ubuntu.com/download/desktop)

[Ubuntu Yakkety Daily iso files amd64](http://iso.qa.ubuntu.com/qatracker/milestones/360/builds/130525/testcases)

---

### Post by n.triple.a on 2016-09-05
> **sudodus said:**
> +1 for a new version. I suggest that you start with ***Ubuntu 16.04.1 LTS amd64***, which works for Bucky Ball, and read his tips very carefully.

If it 16.04.1 LTS does not work, you can try the next version, still in the development phase. It might work better, because there are newer versions of the kernel, drivers etc. It is called ***Yakkety Yak***, and will be released in October as 16.10 (a short-lived version, but if it helps running the graphics ...). This version might have temporary problems for two more months. Because of the development things are changing a lot, and the different pieces of software do not always match.

Links:

[Ubuntu 16.04.1 LTS amd64]("http://www.ubuntu.com/download/desktop")

[Ubuntu Yakkety Daily iso files amd64]("http://iso.qa.ubuntu.com/qatracker/milestones/360/builds/130525/testcases")

Well, I could try Ubuntu 16 but I really want to exhaust my chances with 14.04. Because in my work and college, the version used and suggested is 14.04.

---

### Post by Bucky Ball on 2016-09-05
> **n.triple.a said:**
> Well, I could try Ubuntu 16 but I really want to exhaust my chances with 14.04. Because in my work and college, the version used and suggested is 14.04.

... until it reaches end of life and then they'll suggest 16.04 LTS and you'll be one step ahead! :)

Seriously, unless you are needing 14.04 specifically because you are going to have some kind of tech class where 14.04 will be specifically used, understood. If, on the other hand, the only reason you are not going for 16.04 is because someone or someones recommended 14.04, forget it. For the user, they are pretty much identical above the hood, and pretty similar under it, and it will also have much more chance of having the drivers for you machine.

As I mentioned previously, the last point is the exact reason I went for 16.04. In actual fact, and I forgot, I installed 15.10 to start with, no longer supported so don't go there, because it was the newest stable and supported release at the time, 16.04 was still a couple of months away. 

This may not sound like a big deal, but I, too, am a student doing my masters and NEVER go for wet behind the ears releases and NEVER install interim releases for my work computers. Simply can't afford downtime. So, installing 15.10 was radical for me. It worked, but was a little glitchy, so, gulp, I installed 16.04 about a month before it was released with a great deal of trepidation. I had everything setup on 14.04 on my laptop, though, so there was a safety net.

You know what? 16.04 worked without a glitch and I never used 15.10 again. There have been some oddities along the way, but to do with USB peripherals, not the hardware in the box.

PS: I can give you general support with Ubuntu 14.04 on that box, but as you know, I have no experience of it. 'nomodeset' and my other suggestions are about it for now.

---

### Post by n.triple.a on 2016-09-06
Yeah, I never go with new updates neither. However, I did want to install 16.04 but, as you said, 14.04 is the one specifically used for one of my classes. And 'nomodeset' gets me somewhere, but not far enough. I can't figure out what is making the installation to get stuck on that particular "Preparing to install" screen. And believe me, I have tried any possible combination of ticking/unticking the options. All by entering via nomodeset

---

### Post by sudodus on 2016-09-06
At this stage you have to  ***try*** 16.04.1 LTS. You need not start by installing it, but try it ***live*** (and if necessary use nomodeset).

See this link: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

If 16.04.1 LTS works live, you should be able to install it. After installation you can (also use nomodeset) install the proprietary nvidia driver (that was recommended by Bucky Ball in a previous post), and it is likely to work well after rebooting. I think it is really worth trying.

-o-

If you think you need 14.04, you can make a dual boot system and install 16.04.1 alongside 14.04.

---

### Post by n.triple.a on 2016-09-06
> **sudodus said:**
> At this stage you have to  ***try*** 16.04.1 LTS. You need not start by installing it, but try it ***live*** (and if necessary use nomodeset).

See this link: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("https://ubuntuforums.org/showthread.php?t=2230389")

If 16.04.1 LTS works live, you should be able to install it. After installation you can (also use nomodeset) install the proprietary nvidia driver (that was recommended by Bucky Ball in a previous post), and it is likely to work well after rebooting. I think it is really worth trying.

-o-

If you think you need 14.04, you can make a dual boot system and install 16.04.1 alongside 14.04.

I want to dual boot 14.04 and Windows. 14.04 is the Ubuntu version that we use in class in my college. I mean, I have used both 16 and 14 but I just want to stay on the safe side. However, I would be willing to ***try ***installing 16.04. If it does install, does that mean that my laptop's hardware is not compatible with 14.04?

---

### Post by sudodus on 2016-09-06
- If the runs nicely live, it means that your laptop's hardware is compatible with 16.04.1 LTS.

- If it runs even better when installed and with a proprietary driver installed into it, I would say that you should use 16.04.1 LTS.

- There may still be a chance to use 14.04 LTS, but I am afraid, that it might be hard to find a solution for it.

- I suggest that you ask your teacher, if it is OK to use 16.04 instead of 14.04. Ask *why*, if 'not possible', and invite to a discussion here :-)

---

### Post by n.triple.a on 2016-09-06
Ok, I asked my professir and he told me that he preferred 14 because it was stable. However, he told me that I would not have any problems in the class by having 16.04. That said, I installed 16.04 and it went smoothly. However, ubuntu will freeze either when I shut down, Restart or lock the screen. It seems it's just one problem after the other

---

### Post by ubfan1 on 2016-09-06
Did you install the Nvidia proprietary drivers, (from the Software Updater/settings button/additonal drivers tab) or are you still running the (open source) nouveau driver?

---

### Post by Bucky Ball on 2016-09-06
Back to the beginning. Go to Additional Drivers and install the driver I referenced in a previous post, the 361 from memory. Restart. You should then be able to open the NVIDIA x server setting config app and tweak the screen if you need to. 

Almost there. Take a few deep breaths. Yes, this is a learning curve. :)

One thing to keep in mind is that Ubuntu can't legally include the NVIDIA drivers in the Ubuntu kernel. You must install them manually. They are third-party drivers from NVIDIA, not Canonical, so the ease or otherwise of installing the drivers has not a lot to do with Ubuntu. Email NVIDIA and ask them to make it different! :)

Let us know how that goes. If your prof is a Ubuntu whizz (they're running a class in it so they must have some idea what they're on about) they will have some tips. Don't be afraid to ask them, and I'm glad you did with the release options. :)

If you run 'sudo lshw -C video' and the driver says 'nouveau', then you're using the wrong driver. Your resolution is probably out, or other problems ...

---

