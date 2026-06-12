---
title: "Some kind of Linux intolerance. Very weird."
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Glucklich on 2008-10-20
Chill. This is not a flame post. This is a serious problem in which I need help urgently.
OK, here it goes. 19/10/08, I woke up with a nasty hang over and turned on the computer as usual, it made the usual updates since I was using Intrepid beta. It told me to reboot, but I didn't since I had began working (or trying to) on a very important issue. Later that day, my computer freezes, the mouse moved but nothing else happened. Not even Ctrl+Alt+Backspace worked. Was it from not rebooting? I did it some other times and it wasn't a problem. And I had a similar problem with the nVidia drivers, but it always came back, this one didn't. The strange thing is that I had unistalled the nVidia drivers a couple of weeks before and the computer worked smoothly. But this was a freeze that didn't went anywhere. I tried boot from the old kernel and it happened the same thing, complete freeze. So, today in a desperate measure I decided to format (thank god I have an external HD where I keep important data) using XP, to check if it was a computer problem or just with the Ubuntu version. It formated, XP works great. I felt relieved because it's not the laptop. Now, I grabbed the Hardy installation Live CD but when it goes back into the Live CD desktop, the same absolute freeze again! Needless to say it is that was the CD from where I made my very first Linux installation in 24th April 08 and it worked fine until... yesterday. What happened for not even the Live CD to work? Some weird Linux intolerance or something?

---

### Post by eldragon on 2008-10-20
its definately worth checking your system ram for defects, you could try pushing the cpu under winxp too to rule thermal problems out of the equation too.

if the same live cd worked before, and there were no hardware changes, chances are your computer is having some hardware problems.

PS. i was about to bash the hell out of you for complaining a beta release was having serious issues but you shut me up real fast :D

---

### Post by beno1990 on 2008-10-20
As the last poster said, you could be having memory problems. Run Memtest86+ from the live CD and see if it shows up with any problems.

---

### Post by Glucklich on 2008-10-20
> **eldragon said:**
> its definately worth checking your system ram for defects, you could try pushing the cpu under winxp too to rule thermal problems out of the equation too.

if the same live cd worked before, and there were no hardware changes, chances are your computer is having some hardware problems.


Thanks for the quick response. 
Damn. The warranty on that laptop just expired. I hope it's not any hardware problem. But how do I check my ram for defects? Pardon my ignorance.

---

### Post by HittingSmoke on 2008-10-20
> **Glucklich said:**
> Thanks for the quick response. 
Damn. The warranty on that laptop just expired. I hope it's not any hardware problem. But how do I check my ram for defects? Pardon my ignorance.

Isnt memory test an option on the Live CD boot menu?

---

### Post by sethvath on 2008-10-20
[http://www.ibm.com/developerworks/library/l-hw1/](http://www.ibm.com/developerworks/library/l-hw1/)

Look under memtest86. The ubuntu live cd has the memtest option

---

### Post by Glucklich on 2008-10-20
Thank you for all your responses so quickly. It's doing the memtest. I really hope that isn't any hardware issue.

---

### Post by Jim March on 2008-10-21
Well if it's bad RAM, replacing it (and doing an upgrade at the same time?) won't be very expensive.

If it's the motherboard, THAT will be trouble...

---

### Post by Ptero-4 on 2008-10-21
BTW: the memtest needs to be left for IIRC like 8 or 12 hours (dunno, but I read something like that in linuxquestions) to get a reliable result.

---

### Post by Glucklich on 2008-10-21
Well, my memtest has been running for 17 hours so I think it's safe to say that it's not a RAM problem. But according to the text that Seth linked, the description of the problems are similar to what leads to a CPU problem. The solutions that the text gave are within the Linux kernel, but since I don't have any access to it, how can I figure out this problem? But the strange thing is that, if it is indeed a CPU problem, wouldn't it have impact on running XP too?

---

### Post by eldragon on 2008-10-21
you could try stressing your cpu, there is an suit in linux for that called cpuburn.
```

$ sudo apt-get install cpuburn

```

this is valid if you are able to stay unfrozen for a while.

the command in question is burnMMX

you could also do this without the X environment.
hit ctrl-alt-f1
login
type
```

$ sudo /etc/init.d/gdm stop

```

then run burnMMX

watch your laptop for excessive temperatures.

you will not be able to detect a freeze unless you login with a second terminal... to do that, hit ctrl-alt-f2

login.
and execute top to watch the processes.

good luck debugging this obscure problem :(

---

### Post by Glucklich on 2008-10-21
Thanks for the quick response eldragon. But like I said, I can't get into Linux in any way. Not even on the Live CD (and so, unable to install it again). When I still had it, the first three times or so login functioned properly (despite after one minute inside it would freeze), but then not even login would work correctly and then I decided to format using XP. Is there any other way to work it out?

---

### Post by Glucklich on 2008-10-21
> **eldragon said:**
> you could try stressing your cpu, there is an suit in linux for that called cpuburn.
```

$ sudo apt-get install cpuburn

```

this is valid if you are able to stay unfrozen for a while.

the command in question is burnMMX

you could also do this without the X environment.
hit ctrl-alt-f1
login
type
```

$ sudo /etc/init.d/gdm stop

```

then run burnMMX

watch your laptop for excessive temperatures.

you will not be able to detect a freeze unless you login with a second terminal... to do that, hit ctrl-alt-f2

login.
and execute top to watch the processes.

good luck debugging this obscure problem :(


I tried once again to install Ubuntu once again and this time I was successful. I installed cpuburn, put it to work and I'm noticing something weird. Only CPU2 is at 100%. CPU1 is around 5%-7%. What does this mean?

---

### Post by Glucklich on 2008-10-21
I'm not understanding anything about this problem. I'm completly clueless and confused. Yesterday I wasn't able to be one minute in front of the computer. It just plain froze, mouse could walk but nothing else happened. Today, I tried once again to reinstall Ubuntu, I tried to login normal but couldn't since the absolute freeze happened again. Even on LiveCD it happened. I tried what eldragon said, the "gdm stop" thing, he gave me an error on "sudo apt-get install cpuburn". But then I restart again (thanks to Hardy's alt+PrtScr+REISUB, that I wasn't able to do pos Intrepid update) and once again I'm able to be back on the desktop normally? What the hell happened here?

---

### Post by tgalati4 on 2008-10-21
Could be a battery short.  Take the battery out and run from an AC cord only.

Note:  some laptops won't run on AC cord alone.

Also, check for beer inside the keyboard.

---

### Post by Mr. Picklesworth on 2008-10-21
First of all, you should put this in the [Intrepid Ibex Testing]("http://ubuntuforums.org/forumdisplay.php?f=346") section.

That sounds like a kernel crash. Perhaps one of your drivers epically failed, or there was an issue with the latest kernel update. When that happens, usually the Caps Lock and Scroll Lock lights blink. Was that happening that you can remember?
There is a key combination to hard reset your computer *relatively* safely, using the Sys Rq key to send requests straight to the kernel. It even makes a handy mnemonic!
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Edit:
Oooh, I jumped ahead of your post there and didn't read the end. Sorry! I hate it when people do that :P
Err, yes, look for the kernel panic thing. It could hint us in the right direction. If you have Windows XP installed, you could try a [Fedora Live USB]("https://fedorahosted.org/liveusb-creator") if it isn't trouble, which would tell us if this is Linux in general. Oh, and the Live USB thing is cool. (And Fedora is great).
Run XP's device manager, too, which should say if everything is working.

---

### Post by Glucklich on 2008-10-21
> **tgalati4 said:**
> Could be a battery short.  Take the battery out and run from an AC cord only.

Note:  some laptops won't run on AC cord alone.

Also, check for beer inside the keyboard.

Most of the time, I don't run both at the same time. Only when I need to recharge the Battery. And I doubt that was the problem since I've been doing it way before this problem. And, during this problem I tried it both ways and the result was the same. With battery and AC, without the battery and AC only, with battery and without AC.

---

### Post by Gina on 2008-10-21
When you said you couldn't boot fron the CD I was going to suggest the CD integrity test (from boot menu) as CDs (and DVDs) can pick up marks that upset reading.  Also, personally I have had problems with drives failing to read perfectly good CDs.  But this doesn't seem to be the problem - it does appear to be something intermittent.  It might not happen again.  

A friend had problems with a laptop shutting down intermittently and I found it was a loose fan connector.  The plug had never been pushed completely home when the computer was assembled in the factory.  No more trouble after that.  Her's was just out of warranty too.

---

### Post by Glucklich on 2008-10-21
> **Mr. Picklesworth said:**
> First of all, you should put this in the [Intrepid Ibex Testing]("http://ubuntuforums.org/forumdisplay.php?f=346") section.

That sounds like a kernel crash. Perhaps one of your drivers epically failed, or there was an issue with the latest kernel update. When that happens, usually the Caps Lock and Scroll Lock lights blink. Was that happening that you can remember?
There is a key combination to hard reset your computer *relatively* safely, using the Sys Rq key to send requests straight to the kernel. It even makes a handy mnemonic!
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Edit:
Oooh, I jumped ahead of your post there and didn't read the end. Sorry! I hate it when people do that :P
Err, yes, look for the kernel panic thing. It could hint us in the right direction. If you have Windows XP installed, you could try a [Fedora Live USB]("https://fedorahosted.org/liveusb-creator") if it isn't trouble, which would tell us if this is Linux in general. Oh, and the Live USB thing is cool. (And Fedora is great).
Run XP's device manager, too, which should say if everything is working.

It couldn't be an Intrepid issue only. For an Hardy Live CD not to work even knowing it had flawlessly a couple of months before? Caps Lock was off and not working. I looked for other cases to relate to on launchpad, they talked about caps lock light blinking but it wasn't my case. Curiously, I knew REISUB and tried it on Intrepid but it didn't worked.
I will install once again Windows XP and try the Live CD once again. If it doesn't work I'll try the Fedora Live USB. Be back a couple of hours with the results.

---

### Post by rbmorse on 2008-10-21
There are allegations that some nVidia graphics chips are failing prematurely in the field. [http://tinyurl.com/5op2fq](http://tinyurl.com/5op2fq) contains a story about a lawsuit filed over the issue, and the links from that page contains some additional "information" although I have no idea as to its veracity or even relevance. 

In any case, if the symptoms described sound familiar, I would check with your computer's vendor and see if they have implemented some special warranty provisions that cover the problem.

---

### Post by eldragon on 2008-10-21
> **Glucklich said:**
> I tried once again to install Ubuntu once again and this time I was successful. I installed cpuburn, put it to work and I'm noticing something weird. Only CPU2 is at 100%. CPU1 is around 5%-7%. What does this mean?

cpuburn is single threaded, and you have a multicore cpu, to keep things simple, i only got you to stress one of the cores. running a second instance of cpuburn would have done it on both cores.


battery short could be your problem too, i saw this happen before but the other way around (winxp froze, ubuntu ran smoothly).  milling with a dremel the battery contacts (aka destroying the link between the battery and the notebook) fixed the issue :D

how is your battery life? got any at all?

---

### Post by Glucklich on 2008-10-21
@rbmorse:
Does that has any chance of happening even if you have no nVidia drivers installed? Because mine weren't. As I said, I've tracked down performance and display problems to it so I uninstalled it a couple of weeks ago and everything was working great.

@eldragon:
The problem is definitely not the battery. Now I'm working with AC only and it seems everything is back to normal. And I already was before formatting again to XP and it all worked OK.

@Gina:
Yeah. I think it might have been some hardware malfunction, but I don't like the chance that it might never happen again because there's always the chance that it might. And if it happens in a time where I'll be a bit more busy, I might not be so lucky as I was this time.
It was definitely not the CD integrity (since it worked again) and not the CD player (since if it was I wouldn't be able to install XP).

Anyway... this was a weird problem. Now I installed XP again, trying to reproduce the problem again and the Live CD is running! It's like nothing never happened. This is giving me a serious headache. Both CPU's seem to be handling well the pressure. I don't know... what the hell happened here?
Maybe I should take it to do a check up under professional hands because I didn't like a bit what I saw.

---

### Post by Glucklich on 2008-10-21
I've been thinking. What if the problem was some updates on Intrepid? It doesn't make sense. Because I formatted the PC with XP and Hardy's Live CD didn't work. Well... I'll get back to installing Ubuntu, update... and let's see if it happens again. If it does then I guess we can consider a programming thing, if it doesn't it was definitely an hardware thing I should take it to a professional. I'm so confused about this whole mess.

---

### Post by crjackson on 2008-10-21
> **Glucklich said:**
> I've been thinking. What if the problem was some updates on Intrepid? It doesn't make sense. Because I formatted the PC with XP and Hardy's Live CD didn't work. Well... I'll get back to installing Ubuntu, update... and let's see if it happens again. If it does then I guess we can consider a programming thing, if it doesn't it was definitely an hardware thing I should take it to a professional. I'm so confused about this whole mess.

I would be looking for a thermal problem. There are differences between MS and NX and often times, one will run hotter (or cooler) than the other.

If you have a weak system component it will behave like this when certain temps, resistance or voltages are present.

If the system has some use under it's belt, I would start with a good PM, make sure all components are tight and making a good connection, and get all the dust out of that sucker.

---

### Post by Gina on 2008-10-21
Yes, it's quite amazing how much dust collects in computers in quite a short time - and it can play havoc with cooling systems.  I had a graphics card fan seize up in a desktop a little while back - due to dust clogging it up.  The machine was in what would seem a clean environment too.

---

### Post by rbmorse on 2008-10-21
> **Glucklich said:**
> @rbmorse:
Does that has any chance of happening even if you have no nVidia drivers installed? Because mine weren't. As I said, I've tracked down performance and display problems to it so I uninstalled it a couple of weeks ago and everything was working great.

As I understand it...which isn't very well...it's a hardware problem -- actually a manufacturing defect in the chip itself.  Unfortunately nVidia isn't being forthcoming about this, but Apple and HP and Dell all have announced warranty extension programs for certain models that use nVidia chips, and HP has extended that to include some desktop models as well.  That's all I really know.

---

### Post by eldragon on 2008-10-21
> **Glucklich said:**
> 
@eldragon:
The problem is definitely not the battery. Now I'm working with AC only and it seems everything is back to normal. And I already was before formatting again to XP and it all worked OK.


the battery related issue i described occured on AC WITH the battery plugged.

this happened on an old acer with a flat dead battery which would make winxp freeze for no apparent reason. it would work ok if the battery was unplugged...

---

### Post by crjackson on 2008-10-21
> **eldragon said:**
> the battery related issue i described occured on AC WITH the battery plugged.

this happened on an old acer with a flat dead battery which would make winxp freeze for no apparent reason. it would work ok if the battery was unplugged...

The reason is simple. The PSU was expending power to charge a defective battery AND power the system. The defective or flat battery was cauusing a high current draw. As the PSU gets hotter trying to charge the battery, resistance increases (due to heat) and the available power to operate the system falls too far below specification for reliable operation. No mystry at all...

---

### Post by jerrylamos on 2008-10-21
Something to try is to turn compiz off.  Compiz does strange things with hardware and drivers to get "eye candy" even if such tricks can readily hang or lock up a pc or laptop.  Here's a way to test for compiz funnies:

1.  Try on whatever CD you wish, to do install from the first menu that comes up on the CD.  I use manual install.
2.  After install, if it completes (install doesn't use compiz) then boot in recovery mode.
3,  At the choices menu, select root prompt.
4.  sudo apt-get remove compiz
5.  sudo apt-get remove compiz-core
6.  exit
7.  resume normal boot

Now removing compiz from CD Live boot can be done, but it's time dependent.  You have to do Ctrl-Alt-F1 after X windows is up (flashing screen, X or pointer), login, then do steps 4 & 5 abomve, then Ctrl-Alt-F7 all before Gnome tries to load the desktop.

Another way to test if compiz is the problem is to try Xubuntu or Kubuntu which don't use it.

Jerry

---

### Post by Glucklich on 2008-10-22
@ crjackson and Gina:
Dust might be a reasonable explanation but I think it's a little thin. Because I haven't done anything to the laptop, not even turn it around... and its working perfectly now. So, I think it won't explain why this whole mess happened in the first place.

But I think, a graphic card problem is very probable. Because I tried to install the nVidia drivers, rebooted and the BIOS screen appeared all messed up and the GRUB loader with strange characters like the first time I had to format with XP.

@ jerrylamos:
With Kubuntu, can I expect a better compatibility with the nVidia drivers or it will be the same?
Anyway, I'll follow your suggestion and install Kubuntu to see if it is a Compiz incompatibility, because even without the drivers uninstalled and effects disabled the first time, the problem showed up.

---

### Post by crjackson on 2008-10-22
> **Glucklich said:**
> @ crjackson and Gina:
Dust might be a reasonable explanation but I think it's a little thin. Because I haven't done anything to the laptop, not even turn it around... and its working perfectly now. So, I think it won't explain why this whole mess happened in the first place.


I didn't blame dust specifically. I said start with a good PM, to include blowing the dust out... Intermittant problems are usually thermal related, connection related, or failing/defective part related. Start simple and work your way up, not down.

---

### Post by Glucklich on 2008-10-22
> **crjackson said:**
> I didn't blame dust specifically. I said start with a good PM, to include blowing the dust out... Intermittant problems are usually thermal related, connection related, or failing/defective part related. Start simple and work your way up, not down.

@ crjackson
Excuse my ignorance, but what is a PM? 
I can't make sure all components are tight because this is a laptop and I'm not an expert on this issue. On a desktop I would but not on a laptop. The best I can do is take it to a professional but I will only consider it as a last resort (due to the economic implications).
The best I could do was clean the fans (googled a couple of articles on how to do it) and made sure they were running. And it's positive. They are running normally. The computer is as hot as it was on Windows despite the fans run a little longer.

@ jerrylamos
I think it's not a Compiz incompatibility. I'm using Kubuntu 8.04 with KDE3, installed the nvidia drivers and the response was the same. When restarting, the BIOS menu was messed up and the GRUB loader was with strange characters (just as the original problem).

---

### Post by heavensblade23 on 2008-10-22
Are you installing from a pressed disc or a burned one?  CD-Rs have been known to become unreadable practically overnight in some unfortunate cases.

It could just be a random hardware fault Windows deals with better than Linux.  They're very hard to track down in some cases.  I tore my PC down to it's component parts and put it back together trying to find out why it was doing hard reboots after a random period of time.  Eventually I discovered that the problem was less complicated than I thought: the reboot button was hosed.  Disconnected the header and the problem went away.

Could also be a bug in Linux or a driver.  One time I was having a similar problem with random hardlocks, and after installing the latest driver direct from nvidia, the problem went away.

Don't feel pressured into spending a lot of time on this if you're not dead set on running Linux.  Use what works.

---

### Post by crjackson on 2008-10-22
> **Glucklich said:**
> @ crjackson
Excuse my ignorance, but what is a PM?

Preventive Maintenance - If you don't posses the skills needed then by all means take it to a professional for diagnostics and repair.

---

### Post by crjackson on 2008-10-22
> **heavensblade23 said:**
> Use what works.

Couldn't agree more...

---

### Post by Glucklich on 2008-10-22
> **heavensblade23 said:**
> Are you installing from a pressed disc or a burned one?  CD-Rs have been known to become unreadable practically overnight in some unfortunate cases.

It could just be a random hardware fault Windows deals with better than Linux.  They're very hard to track down in some cases.  I tore my PC down to it's component parts and put it back together trying to find out why it was doing hard reboots after a random period of time.  Eventually I discovered that the problem was less complicated than I thought: the reboot button was hosed.  Disconnected the header and the problem went away.

Could also be a bug in Linux or a driver.  One time I was having a similar problem with random hardlocks, and after installing the latest driver direct from nvidia, the problem went away.

Don't feel pressured into spending a lot of time on this if you're not dead set on running Linux.  Use what works.

Burned CD-RW.
I'll try to install the latest direct nVidia driver. See how it works.
Well, since April running Linux I find myself very affectionate by its ways but you're right. If nothing else works and nobody finds any use in it, that should be it.
Thanks for all your help.

---

### Post by Glucklich on 2008-10-23
> **crjackson said:**
> Preventive Maintenance - If you don't posses the skills needed then by all means take it to a professional for diagnostics and repair.

As I said before, I will only consider it if everything else fails. I'm paying for a house and the economy is not being very helpful about it, so excuse me if I like to clear all other roads first before putting that option on the table.

I installed the latest direct nVidia driver and no luck. Despite founding a specific bug on the new driver, the same freeze after a while, BIOS screen mess up and GRUB loader strange characters were there.
I think I'll try asking for some help on the nVidia forum too.
I'll try also updating my BIOS. Don't know if it help but it certainly can't hurt. Upgrading the BIOS already helped me with a sound problem in April, maybe it will help me this time too.

---

### Post by Glucklich on 2008-10-26
OK, after spending most of my free time after the cause of this issue I'm almost certain that it is a graphics card problem.
I've added this lines to my /etc/X11/xorg.config "Screen" section:

Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" “Off”

in order to stop the freezes but the strangest thing happens. I'll post a photo of the screen.

[[IMG]http://img517.imageshack.us/img517/3458/hpim1816sp5.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=hpim1816sp5.jpg)[[IMG]http://img517.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Any idea of what this is?
Thanks in advance.

---

### Post by psyke83 on 2008-10-26
> **Glucklich said:**
> OK, after spending most of my free time after the cause of this issue I'm almost certain that it is a graphics card problem.
I've added this lines to my /etc/X11/xorg.config "Screen" section:

Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;

in order to stop the freezes but the strangest thing happens. I'll post a photo of the screen.

[[IMG]http://img517.imageshack.us/img517/3458/hpim1816sp5.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=hpim1816sp5.jpg)[[IMG]http://img517.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Any idea of what this is?
Thanks in advance.

I thought you said in an earlier post that you weren't using the nvidia drivers?

It seems quite likely they are the culprit. Edit your /etc/X11/xorg.conf file.

Replace:
```
Driver "nvidia"
```
With:
```
Driver "nv"
```

Reboot for changes to take effect.

I also recommend:
1. If you have access to another machine: install SSH on your defective machine. When a system freeze occurs, attempt to connect remotely via another machine and recover any logs.
2. Post your dmesg output here, in case there are any suspicious messages or warnings.

---

### Post by Glucklich on 2008-10-26
> **psyke83 said:**
> I thought you said in an earlier post that you weren't using the nvidia drivers?

It seems quite likely they are the culprit. Edit your /etc/X11/xorg.conf file.

Replace:
```
Driver "nvidia"
```
With:
```
Driver "nv"
```

Reboot for changes to take effect.

I also recommend:
1. If you have access to another machine: install SSH on your defective machine. When a system freeze occurs, attempt to connect remotely via another machine and recover any logs.
2. Post your dmesg output here, in case there are any suspicious messages or warnings.


In the original problem I didn't. But as I couldn't reproduce the freezes again and I've had them before with the nVIDIA drivers, I doubt it was a coincidence. 
I can't use this "nv" drivers, every scroll frame takes 4 seconds. Looks like a guy cleaning the screen from top to down. Is there another way to make it work?

---

### Post by psyke83 on 2008-10-26
> **Glucklich said:**
> In the original problem I didn't. But as I couldn't reproduce the freezes again and I've had them before with the nVIDIA drivers, I doubt it was a coincidence. 
I can't use this "nv" drivers, every scroll frame takes 4 seconds. Looks like a guy cleaning the screen from top to down. Is there another way to make it work?

The open-source nv driver is a little slow, but it shouldn't be as slow as you describe - this only increases the evidence of your graphics card being the culprit.

You can try the "vesa" driver, or change it back to "nvidia", using a different version of the nvidia driver (i.e. if you're using the nvidia-glx-177 driver, downgrade to nvidia-glx-173 - or vice-versa).

---

### Post by Glucklich on 2008-10-26
> **psyke83 said:**
> The open-source nv driver is a little slow, but it shouldn't be as slow as you describe - this only increases the evidence of your graphics card being the culprit.

You can try the "vesa" driver, or change it back to "nvidia", using a different version of the nvidia driver (i.e. if you're using the nvidia-glx-177 driver, downgrade to nvidia-glx-173 - or vice-versa).

I already tried the 169.04 because of a nvnews and a topic here on UF, that said that with that driver and a change on nvidia-kernel they could work with a GeForce GO 7900 GS. But it didn't work for me.

EDIT: Nop. Vesa didn't work too. Real bad image.

---

### Post by Glucklich on 2008-10-26
Guess I'm f*cked now... right?

---

