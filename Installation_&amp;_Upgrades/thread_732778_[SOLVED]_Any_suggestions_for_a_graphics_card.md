---
title: "[SOLVED] Any suggestions for a graphics card?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by aaron01 on 2008-03-23
To my disappointment I think I am ready to wipe the hard drive clean and reinstall windows as it at least run well. I built this system for a friend and I can't tie up the machine much longer. I have had nothing but problems of not running linux at all to finally getting ubuntu to run from the live cd, only to fail to boot or run again from the cd. Here is the system:

Asus M2N-MX SE Plus motherboard
AMD 64 X2 3600 cpu
Onboard Nvidia graphics
160 GB SATA HD

The problems are many including the fact that I can not even run the live cd since the installation. I can only get to the screen to choose which os to load from and it only loads windows. I get a blank screen trying to go into ubuntu. I appreciate all the posts and reading of all of my problems has not led me to a solution. I can't keep pouring more countless hours trying to get this to work anymore. I was almost tempted to get a separate Radeon graphics card to see if it works, but if I have my friend purchase it and it doesn't work she won't be happy. If I knew the graphics card would straighten this out I would do it. I am so tempted to use killdisk and start over with just windows.

Any last minute suggestions on the graphics card?

---

### Post by aysiu on 2008-03-23
First of all, when you get the blank screen when trying to load Ubuntu, can you press Control-Alt-F1 and see if any text appears? If so, what does the text say?

Secondly, I doubt ATI Radeon will yield better results than Nvidia. Intel is the most Linux-friendly, but Nvidia is generally less trouble than ATI, as far as I know.

Frankly, if you aren't willing to keep pouring hous into getting this to work, I think you should go back to Windows and save up for buying Linux preinstalled (a Dell Ubuntu computer or Eee PC). Installing and configuring a new operating system from scratch is not supposed to be an easy activity.

---

### Post by fela on 2008-03-23
> **aysiu said:**
> 

Frankly, if you aren't willing to keep pouring hous into getting this to work, I think you should go back to Windows and save up for buying Linux preinstalled (a Dell Ubuntu computer or Eee PC). Installing and configuring a new operating system from scratch is not supposed to be an easy activity.

exactly.

perhaps your grub config file is f**ked, can you boot into recovery mode?

---

### Post by TheWizzard on 2008-03-23
> **aysiu said:**
> Installing and configuring a new operating system from scratch is not supposed to be an easy activity.

yeah, but in my experience ubuntu is a lot easier than windows.

---

### Post by aaron01 on 2008-03-23
When the screen goes blank pressing Control-Alt-F1 does nothing.

"can you boot into recovery mode?" NO, all I get is text which is not lined up. That is to say it looks like text is to the left, midddle, and right of the screen. It was because of this that lead me to believe that it may be a graphics driver. I would have installed the Nvidia graphics driver if I could have ever got to a point where it would have let me.

I did at least boot the first time from the disc and install. This is further than I got with Debian which also just gave me the first screen then text which was all over the screen and wouldn't load the kernal at all.
I also had tried my Knoppix disc which wouldn't run either, same thie past the first screen text to the left, middle, and right.

All this lead me to believe a graphics problem, but I don't know for sure.

Thanks for all the help.

---

### Post by scottro on 2008-03-23
The whole NVidia (as well as, for example, Atheros wireless) is an aggravating issue in trying to escape Windows.  No, you shouldn't have to pour hours into it--Ubuntu's stated number one bug is that WIndows is more popular.  :)

I thought that NVidia's can use a basic nv driver without the black screen thingie.  (I just got a new quad core and made the mistake of getting an NVidia card--right now, I can use FreeBSD on it with the basic generic nv driver, but it won't work through a KVM.  

Doing some googling, you'll find that

Some people get nvidia working functionally (though not with all features out of the box.)
Some people get ATI working without problem.
Some people get Intel working out of the box

Some people never get their NVidia to work
Some people never get ATI to work
Some people never get their Intel card to work. 

So it's really a lottery, I fear.  With the older AGP cards, I 've had no trouble with Matrox and ATI, but these days, few computers have AGP slots.  

The only advice I can give is that if you're using a KVM switch, try attaching directly--and I only learned that yesterday.  :)

---

### Post by Pumalite on 2008-03-23
You might want to try this:
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by aaron01 on 2008-03-23
I took the new machine I had built to my friends house and was booting up and going to show her how the graphics were messed up on the Ubuntu install. When I booted it up everything worked great and I was amazed. It turns out that it was my monitor that was causing the conflicts. 

I am not sure if Linux just doesn't like my monitor with this setup, or if it had to do with the fact that the monitor was hooked up to two different computers. I always leave my monitor hooked up with a dvi cable to my personal computer and then hook up a computer I am working on through the vga cable. I have never had a conflict before because only one computer is accessing the monitor at a time. My friends computer that I put this install on was hooked up through the vga on my monitor so who knows. I am just stoked that I can run the dual boot fine now, and I am using Ubuntu right now as I type!

:)

---

### Post by Pumalite on 2008-03-23
Great! Use the thread tools and mark this thread solved.

---

