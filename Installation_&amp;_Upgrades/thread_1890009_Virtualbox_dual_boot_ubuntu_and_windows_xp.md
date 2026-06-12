---
title: "Virtualbox dual boot ubuntu and windows xp"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by internetprofiles1 on 2011-12-02
Another virus last week accidently opened by some attached .doc on my wife email was enough. I decided back to ubuntu. The dual boot worked ok, but i really just wanted to kill microsoft all together unfortunately wine is not working like i expected. Has anyone tried virtualbox? In which windows is loaded virtually inside ubuntu some of my college classes require stupid internet explorer running on a windows platform and that the user agents for firefox or opera browsers just arent recognized by my online class. I hoping that virtualbox will be my way out. Luckily ii still got my xp install disc

---

### Post by snowpine on 2011-12-02
I *love* virtual machines and encourage you to give it a try. :)

This should get you started: [https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

Note that you'll need an actual XP install disk, don't assume that a recover/OEM disk that came with your computer will work.

ps Here is a simple solution to your browser user agent problem, it may be possible to stay on Linux and trick the website into thinking you're using Internet Explorer: [https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

---

### Post by ubix on 2011-12-02
> **internetprofiles1 said:**
> ...In which windows is loaded virtually inside ubuntu...
Do not really understand your question.:confused:

Virtual box opens a window on the desktop, which behaves almost like a new screen. You can also maximize to cover the entire screen, or even share Micro$oft applications on your Linux, though I do not recommend this use. I prefer to separate the guest OS from host OS. Running more OS-es at the same time is too memory intensive, unless you can afford it. But you should read the manual about these things.

---

### Post by internetprofiles1 on 2011-12-02
well ubix, my question really is does it work and how stable is it??  Wine would freeze up after 2 seconds using internet explorer and thats  no good. I might give the dual boot another try if i have to but i had  so many problems loading ubuntu11.10 dual boot, black screen, grub error ,  busybox...
snowpine I aready have the useragent tool.I do not like to buy  pre-installed systems.I build my computers so I have all 3 original XP  professional  media center edition disks and the key 100plus bucks at  the time :( .Anyways,when using ubuntu some of my online classes  gives  me an error "your platform is not reconised, please use supported  windows or mac OS"  so the only way around that is to dual boot or  virtualboot windows.

---

### Post by NickCarriere on 2011-12-02
From my use of virtual box it works well. But it also can depend on your specs. obviously the more ram the better and the faster the CPU the better. If you have a slow single core Pentium 4 with 1GB of ram, i doubt it is going to be smooth. Might be smooth on a dual core Pentium D at 3GHz and GB of ram and past that i would assume it will be smooth. So it depends on your specs in the end. Virtual box is a smooth program.

---

### Post by oldtimer7777 on 2011-12-03
I would recommend trying VMWare Player for free.

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

> **internetprofiles1 said:**
> Another virus last week accidently opened by some attached .doc on my wife email was enough. I decided back to ubuntu. The dual boot worked ok, but i really just wanted to kill microsoft all together unfortunately wine is not working like i expected. Has anyone tried virtualbox? In which windows is loaded virtually inside ubuntu some of my college classes require stupid internet explorer running on a windows platform and that the user agents for firefox or opera browsers just arent recognized by my online class. I hoping that virtualbox will be my way out. Luckily ii still got my xp install disc

---

### Post by NickCarriere on 2011-12-03
> **oldtimer7777 said:**
> I would recommend trying VMWare Player for free.

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

Just did this and installed everything so I can use unity and wow. I can't believe this is free... It is buggy and if you have extra effects on it gets weird and as expected it isn't the smoothest but wow I love how you can have the windows in Ubuntu as if it was a windows desktop. This is better than Virtualbox.

---

### Post by oldtimer7777 on 2011-12-03
> **NickCarriere said:**
> Just did this and installed everything so I can use unity and wow. I can't believe this is free... It is buggy and if you have extra effects on it gets weird and as expected it isn't the smoothest but wow I love how you can have the windows in Ubuntu as if it was a windows desktop. This is better than Virtualbox.

Yeah I discovered how to configure it like this recently. I've been using Wine to do something like what this does, but VMWare does a superior job with desktop integration verses Virtualbox, if you need to use a Windows app in Ubuntu quite frequently. I still think Virtualbox is suffienent for occational use, but it has a long way to go with desktop menu integration so it appears more seamless when working with virtualized applications.

---

### Post by internetprofiles1 on 2011-12-04
I have an AMD 64 3700 and the processor is set to lower to 1.8GHz and 2 Gigs ram . I set XP virtual box to run with 700meg ram and its running fine.I had to figure out a few things like in settings the CD rom can be set to passthrough so no need to mount and unmont it, but otherwise the install when good.
If anyone plans on using Virtualbox NOTE the version of VirtualBox within ubuntu is version 4.1.2 and is missing some updates so I had to remove it and reinstall the deb package from 

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) version 4.1.6

doing this did not erase my virtual XP that I installed on the previous version of virtualbox.

the missing update has to do with base system drivers and installion Guest OS additions is missing from the update center. The version found on that website installs all the drivers including missing video drivers that you normally have to hunt down plus adds other features like seamless integration and files can be stored to the linux partition so if I mean WHEN windows messes up and I have to reinstall it,i wont loose anything.This is so cool I am running updates on XP right now but using ubuntu firefox. This is exactly what I was looking for, I&#7743; not a big gamer so No need for dual boot anymore I like this, to me windows is now  just a last chance bonafide bulky webbrowser for websites that do not want to accept change that Linux is taking over! lol

---

### Post by internetprofiles1 on 2011-12-09
there some issue with virtual box handing of media, seems a bit slow, I&#7743; guessing due to memory constraints. i&#314;l try vmware player.

---

### Post by ubix on 2011-12-14
> **internetprofiles1 said:**
> well ubix, my question really is does it work and how stable is it??  Wine would freeze up after 2 seconds using internet explorer and thats  no good. I might give the dual boot another try if i have to but i had  so many problems loading ubuntu11.10 dual boot, black screen, grub error ,  busybox...
snowpine I aready have the useragent tool.I do not like to buy  pre-installed systems.I build my computers so I have all 3 original XP  professional  media center edition disks and the key 100plus bucks at  the time :( .Anyways,when using ubuntu some of my online classes  gives  me an error "your platform is not reconised, please use supported  windows or mac OS"  so the only way around that is to dual boot or  virtualboot windows.

After, all you have said so far in this thread _it is safe to conclude you'd be much better off with the **VMWare Player**_. Using VB to turn it into an extended **M$ IE** application is a rather ambitious overkill. Besides you are rather short on resources, particularly memory. Why then even bother with all the latest updates and the CD rom issues you are mentioning if you plan to only solve your browser problems. Indeed, if you had sufficiently strong hw, that would then make sense, but to run two OSes just to have an extra proprietary browser available occasionally is a double waste of resources. As much as I can tell **VirtualBox** is a far superior piece of software than  **VMWare Player**. It is not meant only for an occasional application sharing from different sw platforms or to be used as Wine, but rather as a virtual machine, that behaves like an independent hardware box, and can be at any time ported to a different platform or hardware with unchanged data image and state as well as the configuration state.

---

