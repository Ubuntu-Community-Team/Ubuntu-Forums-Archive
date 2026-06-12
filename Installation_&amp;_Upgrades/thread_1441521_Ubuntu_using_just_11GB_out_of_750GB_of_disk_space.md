---
title: "Ubuntu using just 11GB out of 750GB of disk space"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by ArtemNY on 2010-03-28
**I currenty run Ubuntu 9.10. When I was installing the OS I've probably just didn't pay an attention to this step when it asked me how much of free space to use for Ubuntu. Now it's using just 11 GB and I want it to use 100% of space of this partition. Installed it with Wubi ***(btw when installing using Wubi, can I just dump the Windows OS and run Linux itself or when I install it with Wubi the windows and linux are connected in any way?)*[B].
I've checked other threads on this topic but they provided help for older versions of Ubuntu. 
What method should I use for 9.10?[/B]


[I]Thanks a lot for help and... welcome me to this greate forum and greate OS.
This is actually my 1st day of using Linux. Before that over 15 year Windows user (since Windows 3.1x).
So far I love it much more thn Windows.[/I]

---

### Post by RedSingularity on 2010-03-28
Hey buddy, welcome to linux and the forums :)  Good to see another happy user.

---

### Post by srs5694 on 2010-03-28
If you want to completely ditch Windows, don't install using WUBI. Download a conventional installer, delete the Windows partition(s) on your disk, and have Linux take over the whole disk. WUBI is intended for just testing Linux without making a major commitment to it.

---

### Post by stlsaint on 2010-03-28
As stated in above post you must actually boot into the livecd to install ubuntu. Doing a wubi install only installs ubuntu INSIDE of windows. You can have the option of dual booting thus you will have the option to boot either ubuntu or windows at startup of system. Please see signature for helpful links on your specific topic needed.

---

### Post by ArtemNY on 2010-03-28
Actually, I've tried to install it from the CD but there was so much stuff I'm not familiar with that I decided to run a Wubi. 
When I opened an CD installation documentation it was looking so easy to do, but when I actually started an installation there was completely different process.
Where can I get an ISO with understandable (for Windows user) installation process? And BTW I need to run a server on this PC so which server version is better to choose?


PS thanks everyone for comments and warm words. I'm sure I'll have a greate time using this OS and this board. :)

---

### Post by stlsaint on 2010-03-28
Your installation procdure depends on how customizing a install you want. You can choose to do most defualt options and have a fully functional install. IE: If you choose to use the entire hdd for ubuntu than you dont have to worry about manual partitions. Download a livecd from ubuntu.com and burn to disk...boot to the cd and follow the onscreen instructions. Remember that using the livecd allows you to have internet if you are running it on ethernet cable. So if you get stuck you can come back here to forums or go a google search for answers to your issues.

---

### Post by oldfred on 2010-03-29
Some of these show you the screens you will see as you install, so you have a better idea of what is envolved. Server installs are command line/text based but similiar. They do not install any windows and expect you to do everything at the command line but you can install gnome or kde on top of the server install if you want. You also can use the standard desktop install and later add in the server components. 

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by ArtemNY on 2010-03-29
JEEEEEZ! So much info a bit confusing. But thanks everybody anyway. Not going to give up! It becomes more and more interesting. 
When I get more and more questions on some topic, it sucks me in and I'm like: oh what's this, and how this thing work, and... why my PC smells like it's burning :D Well you know stuff like this!
 
So I've decided to use desktop version, after that I'll install server components. Collected all possible (let's see how it'll help) info on an installation process.
 
Just one question left. 32 or 64? No really, I've read some threads here and everyone thinks differently. I mean I have 64-bit core and running 64-bit Vista. So what should I choose for the Linux? 64 or 32 bit option? The most important thing for me above everything else is stability and security. It may not look so good (well there's always a chance to install some cool looking mods), it may not work so fast (well there's always a chance to install some fast hardware) but it **HAS** to be stable! 
 
 
**So between 32-bit and 64-bit which one is the most stable?**

---

### Post by oldfred on 2010-03-29
64bit.

Three or four years ago I bought a 64 bit capable pc and then the 64bit server was ok but certain desktop apps had issues running in 64bit. I think all the issues have been resolved. With Karmic I converted to 64bit and have had less problems (virtually none that I can tell related to 64bit) than with previous installs.

---

### Post by gadolinio on 2010-03-29
If you want to install Ubuntu alone, getting rid of windows, and you don't need to make different partitions (at least not right now), the installation process is really easy. Boot with the LiveCD (the one you burn with the .iso file you download), then a menu appears; choose install, and follow the steps, or choose "try ubuntu without making changes...", and then when the live session desktop appears double click the install icon in it. Either way, you just follow the steps... When asked about where to install, select the entire disk option.

---

### Post by ArtemNY on 2010-03-29
> **gadolinio said:**
> If you want to install Ubuntu alone, getting rid of windows, and you don't need to make different partitions (at least not right now), the installation process is really easy. Boot with the LiveCD (the one you burn with the .iso file you download), then a menu appears; choose install, and follow the steps, or choose "try ubuntu without making changes...", and then when the live session desktop appears double click the install icon in it. Either way, you just follow the steps... When asked about where to install, select the entire disk option.
 
Yeah yeah yeah already did it. Before that I just probably downloaded a text version.

---

### Post by ArtemNY on 2010-03-29
> **oldfred said:**
> 64bit.
 
Three or four years ago I bought a 64 bit capable pc and then the 64bit server was ok but certain desktop apps had issues running in 64bit. I think all the issues have been resolved. With Karmic I converted to 64bit and have had less problems (virtually none that I can tell related to 64bit) than with previous installs.
 
So you are saying that 9.10 64-bit as stable as 9.10 32-bit is?
So why should I choose 64 over a 32? I'm not trying to be boring, I just want to understand what's the difference.

---

### Post by oldfred on 2010-03-29
If you do not have more than 3GB of memory it will not make much difference. 

There are many posts with many opinions here in the forums. I did a quick Google and was overwhelmed with posts. There used to be a sticky that I was looking for.

---

### Post by ArtemNY on 2010-03-29
> **oldfred said:**
> If you do not have more than 3GB of memory it will not make much difference.
What if I have 8GB RAM? Will it make difference?

---

### Post by Slim Odds on 2010-03-29
> **ArtemNY said:**
> So you are saying that 9.10 64-bit as stable as 9.10 32-bit is?
So why should I choose 64 over a 32? I'm not trying to be boring, I just want to understand what's the difference.

In my experience, the 64 bit versions are at least as stable as the 32 bit versions, maybe even more so.

The 64 bit will make better use of your CPU if it's 64 bit. Also, if you have 4GB or more RAM, them the 64 bit will make full use of it, whereas the 32 bit will not.

I'm running the 64 bit and it's great. The Adobe flash 10 alpha driver works perfectly for me (flash is something a lot of people are concerned about). 

I even dual boot my 1.3GHz Intel SU7300 based laptop (with 4GB RAM) with Lucid 64 bit and it runs very well.

There are very, very few reasons to run 32 bit on the 64 bit processors.

---

### Post by srs5694 on 2010-03-29
I wrote [this article](http://www.linux-mag.com/id/1699) for Linux Magazine (registration required to read the whole article) six years ago about the differences between 32-bit (x86) and 64-bit (x86-64/AMD64) computing. Today's computers are more sophisticated and the 64-bit distributions are more mature, but the basic issues still apply. In brief, you'll get slightly better speed (about 5-15%, on average) on some applications with 64-bit, and with 8GB of RAM that effect may be enhanced. Six years ago, a few 32-bit applications caused problems on 64-bit systems, but this is much less common today. I believe Flash is the main stumbling block today, but I think there are solutions even for it. (I *hate* Flash, so I've not looked too deeply into this issue.)

---

### Post by Slim Odds on 2010-03-29
> **srs5694 said:**
> I wrote [this article]("http://www.linux-mag.com/id/1699") for Linux Magazine (registration required to read the whole article) six years ago about the differences between 32-bit (x86) and 64-bit (x86-64/AMD64) computing. Today's computers are more sophisticated and the 64-bit distributions are more mature, but the basic issues still apply. In brief, you'll get slightly better speed (about 5-15%, on average) on some applications with 64-bit, and with 8GB of RAM that effect may be enhanced. Six years ago, a few 32-bit applications caused problems on 64-bit systems, but this is much less common today. I believe Flash is the main stumbling block today, but I think there are solutions even for it. (I *hate* Flash, so I've not looked too deeply into this issue.)

I hate flash too, but sometimes (youtube) it's hard to completely avoid it. But, as I mentioned, their alpha 10 flash plugin has worked fine for me for 8.10, 9.04 and 9.10 (I have not updated to 10.04 yet).

The "problem" 32 bit applications are very few now and there are ways to make just about everything work even in those problem cases.

---

### Post by ArtemNY on 2010-03-29
As many comments as many oppinions. :)
I'll try 32-bit for a while then I'll try 64-bit myself. That's the best choice I guess.

---

### Post by Slim Odds on 2010-03-29
> **ArtemNY said:**
> As many comments as many oppinions. :)
I'll try 32-bit for a while then I'll try 64-bit myself. That's the best choice I guess.

That's your choice.

Personally, I'd go 64 bit first. That way you'll know right away if you have any issues. Then you can always move back to 32 bit.

Just make sure you use a separate partition for /home
Then you can switch without a problem.

---

### Post by ArtemNY on 2010-03-29
> **Slim Odds said:**
> That's your choice.

Personally, I'd go 64 bit first. That way you'll know right away if you have any issues. Then you can always move back to 32 bit.

Just make sure you use a separate partition for /home
Then you can switch without a problem.
Well I already installed 32 that's why I'll use it 1st.

---

