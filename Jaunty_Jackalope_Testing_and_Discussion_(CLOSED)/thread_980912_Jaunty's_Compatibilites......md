---
title: "Jaunty's Compatibilites....."
date: 2008-11-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andras artois on 2008-11-13
Don't know whether this belongs here but will Jaunty be fully comaptible with quadcore processors, (Nvidia) BFG 9800GT OC Edition 512MB Dual DVI HDTV Out PCI-E Graphics Card, a bluray drive and a Hauppauge WinTV-NOVA-T DVB-T digital freeview USB TV Tuner Stick? 
And will flash and java be fully compatible with 64bit processors by june?
Will 64bit vista detect all 4GB of ram?

I'll be getting a new PC about 2 months after Jaunty's released that's why I'm asking.

Many thanks!

---

### Post by Bölvaður on 2008-11-13
> **andras artois said:**
> Don't know whether this belongs here but will Jaunty be fully comaptible with quadcore processors

What do you mean by that?
Like that every program that you are able to use will be multithreaded? Or if it will just be able to run Jaunty on quadcore?

btw what graphic card was that you was thinking of, so some one can check ati or nvidia website driver section.

From what I understand Hauppauge tuner cards work well, but you should check out linux media forums on exact details on your brand (the chipset changes from one year to the other I think, so it can be difficult to know if it will work without more info or test)

Cuadcores will be able to run flash, but on 32 bits, not 64. You would be able to run it on 64 if flash would be open source project....

I dont know about blueray, but there was a post on this forum with positive signs about blueray on linux, but it is very new medium, you should search for it here to get more detail... ok Im off to work now

---

### Post by andras artois on 2008-11-13
I meant will Jaunty be able to use to quad core processers to their full extent rather than just a fraction of their processing power? And before I confuse myself some more are Intel core 2 Quad processors 64 bit?

[This is the graphics card.]("http://www.ebuyer.com/product/148491")

I remember checking a few threads that said someone had made an unofficial flash 10 package for 64bit processers that worked well but I've been seeing posts saying that Java doesn't work on 64bit systems yet.

I will be using the 64 bit version of Jaunty btw.

Thank you for your help.

---

### Post by Bölvaður on 2008-11-13
I think you will find all the answers you need on this forum:

the graphic card is a yes:
[http://ubuntuforums.org/showthread.php?t=904509]("http://ubuntuforums.org/showthread.php?t=904509")

Multithreading is just like in any other os. The biggest part is done by the people making the software, but there is very few multithreaded programs in the world still. Often you might have to enable multithreading inside the program also.

If you will be using 64 bit I am not sure how flash will be. Perhaps there is some fix now, but when I used 64 bit version almost 2 years ago I had to install 32 bit version of firefox and install flash on there. There will definitely be tutorials for you if you search.


I'd say try it and dont worry about hardware until you pop the cd in. Then you'll get to know what might work and what might not. The nvidi card is unlikely going to be problem at the first boot, but after installing the driver it will be a charm probably.
Then later when you have become used to ubuntu you could tweak the system to do the most crazy things (big performance boosts).

---

### Post by doorknob60 on 2008-11-13
Flash works fine on 64 bit with nspluginwrapper. nspluginwrapper simple makes 32 bit Mozilla plugins work in 64 bit browsers. Nspluginwrapper doesn't work with Java, but OpenJDK works with pretty much everything now. If you install Flash using sudo apt-get install flashplugin-nonfree (exactly like you would in 32 bit), it will set it up for you with nspluginwrapper. ALso, I think OpenJDK is preinstalled with Ubuntu, but if not it's easily installable with Add/Remove, Firefox built in plugin finder, Synaptic, or apt-get :-) BTW it was all like that in Hardy and Intrepid, not just for Jaunty. And yes, all Core 2 processors are 64 bit.

---

### Post by snova on 2008-11-13
Linux has always supported Quad-core processors. There's nothing technically different about SMP.

If your processor isn't being used to it's "full potential", it means you need to give it more to do, not that Linux is failing to use it somehow. CPU's are idle much of the time anyway.

---

### Post by jpeddicord on 2008-11-13
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by Cloud79 on 2008-11-14
> **doorknob60 said:**
> Flash works fine on 64 bit with nspluginwrapper. nspluginwrapper simple makes 32 bit Mozilla plugins work in 64 bit browsers. Nspluginwrapper doesn't work with Java, but OpenJDK works with pretty much everything now. If you install Flash using sudo apt-get install flashplugin-nonfree (exactly like you would in 32 bit), it will set it up for you with nspluginwrapper. ALso, I think OpenJDK is preinstalled with Ubuntu, but if not it's easily installable with Add/Remove, Firefox built in plugin finder, Synaptic, or apt-get :-) BTW it was all like that in Hardy and Intrepid, not just for Jaunty. And yes, all Core 2 processors are 64 bit.

I don't think that i agree with that it works good with flash on 64bit. I have to restart my browser several times every day because flash stops working in the browser (get a gray background instead of the flash).

I have the same problem on all 3 computers and has been a problem since i started using 64bit releases.

---

### Post by gnomeuser on 2008-11-14
> **andras artois said:**
> Don't know whether this belongs here but will Jaunty be fully comaptible with quadcore processors, (Nvidia) BFG 9800GT OC Edition 512MB Dual DVI HDTV Out PCI-E Graphics Card, a bluray drive and a Hauppauge WinTV-NOVA-T DVB-T digital freeview USB TV Tuner Stick? 
And will flash and java be fully compatible with 64bit processors by june?
Will 64bit vista detect all 4GB of ram?

I'll be getting a new PC about 2 months after Jaunty's released that's why I'm asking.


The two problem areas would be your nvidia card and flash. Both can be made to work, the nvidia card will currently require a proprietary driver which is likely to cause some instability of your platform. Flash does not have native 64bit support but you run it just fine, multilib enables you to wrap it nicely in 32bit and execute it that way (I have done this for years) or you can try swfdec (or gnash) which are free software alternatives which have 4 bit support.

Your blu-ray drive will likely have issues playing blu-ray movies, we do not yet to the best of my knowledge have software capable of doing this. The drive as such will be fine though, you should be able to use it.

Java is a solved problem, Sun freed the platform under the GPLv2+classpath exception license and Red Hat invested a lot of money finishing the support to reach 100%. So you should have full 64 bit Java now.

The TV tuner I don't know, odds are in favor, I know we support a lot of these. quick research indicates that it would work, if it does not you can add it to the list of unsupported hardware at the [Linux Driver Project](http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded) (generally this is a good place to go to check for incompatible hardware)

Vista should detect (and gobble up) all of your impressive amount of ram.

---

