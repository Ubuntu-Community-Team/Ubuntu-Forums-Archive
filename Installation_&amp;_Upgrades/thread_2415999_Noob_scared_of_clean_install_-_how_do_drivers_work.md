---
title: "Noob scared of clean install - how do drivers work"
date: 2019-04-03
forum: Installation &amp; Upgrades
---

### Post by sam4842 on 2019-04-03
TL DR: will my computer still fully work with all drivers if I clean install Ubuntu?  

Hello all,

I've newly just dual boot installed Ubuntu 18.04.2 LTS on my 11 yr old Vaio laptop (VGN-FJ290 their site doesn't even have drivers any more) running Win7.  I'm eventually going to go with only Ubuntu, but the memories of "upgrading" from Vista to 7 still haunt me.  I vividly remember the dread of missing drivers and having to hunt on Sony's site for drivers.  It took me 2 weeks to get my machine running smoothly.

Right now, the dual boot seems to be functioning.  All my extra media buttons on the top of the laptop miraculously works in Ubuntu (something that couldn't be said about the "upgrade" from Vista to 7).
The dual boot has 3 partitioned drives, 7, Ubuntu and another small partition that at the moment I don't remember what it was.

My question is, if I do a clean install of Ubuntu will everything still function as it is now?  
Where are drivers stored?
When I clean install Ubuntu, will I lose my drivers?
I am terrified that I will lose the drivers and things will not work.  I remember my mouse, screen, button, speakers not working when I previously "upgraded".  

Thank you in advance for any insights.  -terrified of upgrading but too cheap to go buy a Win10 machine.

---

### Post by huff2 on 2019-04-03
Drivers are files that the computer uses to communicate with hardware,  essentially. Ubuntu comes with drivers. If you are using Ubuntu  currently and are experiencing no errors with hardware such as mouse,  keypad, speakers, etc. then you are fine to have only Ubuntu on your  hard drive. If you do install it and need drivers, then they can be  installed, in Ubuntu. It's important to understand that "drivers" are plain text files (someone correct me here if I'm wrong, please) and they can always be downloaded from a server to be used. 

In essence, if you remove Windows completely and replace it with Ubuntu, then yes, your windows drivers will be gone forever along with windows HOWEVER Ubuntu has its own set of drivers that it uses. 

You should be fine but honestly there is no need to only have Ubuntu installed on your hard drive. If you have it in dual boot and access Ubuntu fine (you even said that new media buttons now work) then there really isn't any need to delete Windows. In fact, most dual-boot for various reasons. Thoughts? 

Did you want to know the file path for the drivers when you asked where they are located? If so, the path in windows or the path in ubuntu.

---

### Post by yancek on 2019-04-03
I don't understand why you would want to do a new install of the same version of an operating system you already have installed and working??
If you are planning to get rid of windows, you can simply format the windows partitions to a Linux filesystem.
Drivers for most software on Linux are in the kernel.

---

### Post by Frogs Hair on 2019-04-03
Welcome sam4842:

Windows 7 end support on  January 14, 2020 , so you have some time to think about it. Were you planing to upgrade to windows 10 or just install Ubuntu on the entire drive ?  >   -terrified of upgrading but too cheap to go buy a Win10 machine.  ??

---

### Post by Rubi1200 on 2019-04-03
Hi and welcome to the forum sam4842 :-)

As has been mentioned, native support for drivers is one of the main features in Ubuntu. I have used various Linux distros on all sorts of hardware, both old and new computers, and never once had an issue.

As Frogs Hair rightly pointed out, Win 7 support ends next year so there is time.

If you are interested, we could advise you on how to set up a dual boot system, meaning the option to have both Windows and Ubuntu on your machine. That way you would have the best of both worlds and the ability to test how you like working with Ubuntu (Linux in general).

Good luck!

---

### Post by huff2 on 2019-04-03
Here's a good link that can give you a basic overview of dual-booting in general. Wish you all the luck! [https://www.howtogeek.com/187789/dual-booting-explained-how-you-can-have-multiple-operating-systems-on-your-computer/](https://www.howtogeek.com/187789/dual-booting-explained-how-you-can-have-multiple-operating-systems-on-your-computer/)

---

### Post by sam4842 on 2019-04-04
Thank you all for the replies!  Had I known you guys would be so welcoming and helpful, I'd have made the switch before "upgrading" to Win7!

Huff2 Thank you for the confirmation that my machine should work without the dual boot.  I dual booted just to see how much of a culture shock moving from Windows to Ubuntu can be.  Just in case the Ubuntu didn't work, I can try a different Linux distribution.  I have no clue where the driver paths are in Windows or Ubuntu.  Command prompt still scares me but I am slowly learning!

Yancek I'd like to do a clean install rather than trying to delete the Windows partition from Ubuntu so there's nothing left over from Windows.  Windows seems like a really heavy OS compared to Ubuntu.  

Frog's Hair (they don't have hair?) I'm planning on using my machine exclusively as Ubuntu, as you and Rubi1200 pointed out, support for Win7 days are numbered and I'm just too darn cheap to go buy another machine.  The move from Vista to 7 permanently scarred me for life on doing another "upgrade" of Windows OS.  I've looked into cheap Chromebooks, but the specs are a huge downgrade even from my 11 yr old machine!

Rubi1200 I have dual boot set up and working now, but noticed I get BSOD from the Win7 side after I work in Ubuntu then switch back.  Since Win7's days are numbered, I'm going to permanently pull the plug for the Win7 side.  And more importantly, my machine only has 230 GB total hard drive space.  Before the dual boot, I only had 50 or so GB left of open space.  I've already moved all my personal files (movies, pictures and music about 70 GB worth of digital hoarding) onto an external hard drive.  All the programs I use have open source equivalents so I'm not too concerned about losing usability.  

I've only got a few minor things that I'm still missing from Ubuntu that I liked in Win7: sleep/hibernate, Japanese input and maybe making icons smaller.  I'll keep poking around in the forums to see if I can get these working.  But first I'll go ahead with pulling the plug on Windows tonight.

Thank you all again!!

---

### Post by Autodave on 2019-04-04
A couple of things to consider:

Ubuntu, Xubuntu, Lubuntu and a miriad of other buntus all come with the same kernel: the same basic operating system.  Depending on the specs of your machine, you may want to consider going with a lighter desktop such as Xubuntu.  ALL programs can be installed on any of the buntus: some mat come pre-installed on one version and not the other, but all are available in the repositories.

Do you know the specs on your machine: especially the RAM available?

As others have already said, most drivers are already here and you don't need to go looking for them.  Only bleeding edge hardware may have trouble for a little while, or some really old "off of the beaten path" hardware may cause issues.  I have installed Xubuntu on over 40 machines of all kinds and have never had an issue yet.

---

### Post by sam4842 on 2019-04-04
Autodave: Thank you for pointing that out!

In fact, the min specs of Ubuntu was one of the first things I looked at when switching to Linux.
I believe I have 4GB RAM, Intel Core 2 Duo T9400 (2.53GHz); it should exceed the min recommended specs.  It was toward the top of the line a decade ago.  
On paper, this machine can support Win10 but I'm about done with Microsoft's nickel and diming shenanigans in general. 

I've actually have another different Vaio laptop from 2006 that has XP on it.  I am attempting to install Lubuntu on that one since it only has .99 GB of RAM.

But first thing is first, I have to get my main 2008 Vaio machine running before I attempt to resurrect my older 2006 Vaio.

---

### Post by Autodave on 2019-04-04
Ubuntu should be fine then.  But, if you like a simpler desktop, you may want to look at Xubuntu.  You can try it and if you don't like it, all it cost you was a little time.  Personally, I like Xubuntu because I don't need a fancy desktop: all the desktop does is give you a way to your programs.  I don't sit staring at the desktop, so simpler is better.

---

