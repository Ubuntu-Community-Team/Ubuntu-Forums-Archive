---
title: "What should I strip to make Xubuntu faster on old machines?"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by theaceoffire on 2008-07-28
[SIZE="5"][COLOR="Blue"]Recap[/COLOR][/SIZE]
I am in the process of replacing windows 98 and 2000 on a group of older machines at work. 

These things range from 700Mhz Processor/128MB of ram all the way down to 200Mhz Processor/96MB of ram, so I guess it is obvious that it will be tough going.

Some have defective cd drives and old/unsupportive bios's, and I have been [[COLOR="Red"]working around[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5361869#post5361869") it (For others who want to know how, check out [[COLOR="Red"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") and some of the [[COLOR="Red"]alternate install stuff[/COLOR]]("https://help.ubuntu.com/community/Installation")). 

[SIZE="5"][COLOR="Blue"]Anywho,[/COLOR][/SIZE] back to my main topic: On the 700Mhz/128MB machines I got xubuntu going with 1 desktop, no wall paper, 1 menu bar with xkfc menu and a couple of other things. Most services are turned off, and I have a smaller browser installed alongside firefox for average use (called "[[COLOR="Blue"]Midori[/COLOR]]("apt://midori")")

Also, the bios is so old that ACPI is disabled (Always popsup with "Bios is older than 1999, to enable ACPI you must use force" or something). 

[SIZE="5"][COLOR="Blue"]So:[/COLOR][/SIZE]
^_^ So if anyone else has worked with old machines, what can I do to help speed it up a tad? I am open to using other desktops/programs/OS's if suggested... However I would like to stay with Ubuntu or an debian variant if possible.

---

### Post by Sef on 2008-07-28
> ^_^ So if anyone else has worked with old machines, what can I do to help speed it up a tad? I am open to using other desktops/programs/OS's if suggested... However I would like to stay with Ubuntu or an debian variant if possible.

Get more ram.  With 256 - 512 MB ram, Xubuntu will be much faster.

---

### Post by Gun_Smoke on 2008-07-28
Replace your window managers with fluxbox or the like. And there are some great how-to's on flux floating around here..

---

### Post by theaceoffire on 2008-07-28
> **Sef said:**
> Get more ram.  With 256 - 512 MB ram, Xubuntu will be much faster.

These machines are so old that its almost worth buying "new" ones... 
The cheapest computers on Newegg trounce these by a factor of *scary*.

Anywho, Boss wants as much work as I can get out of them without upgrades...

^_^ But yeah, I know what you mean... if I could just stick 512 in there, they would be better I think.

> **Gun_Smoke said:**
> Replace your window managers with fluxbox or the like. And there are some great how-to's on flux floating around here..

I heard of this before, and I will look into it (thanks). 

Do you have any browser that run well on tiny amounts of ram as well, or should I stick with Midori?

---

### Post by Gun_Smoke on 2008-07-28
Swiftfox comes to mind.. But I haven't run into the need.

You will be amazed at what you can get back from switching window managers.. xfce is pretty good but flux or icewm will be much much better for your machines..  Take a bit to set up and maybe you can get away with using partimage to install to the rest of the machines... 

[http://tinyurl.com/64m8t5](http://tinyurl.com/64m8t5)

---

### Post by snowpine on 2008-07-28
> **theaceoffire said:**
> Do you have any browser that run well on tiny amounts of ram as well, or should I stick with Midori?

The slickest browser I've seen is called Links2. It only works for simple text sites but is very, very fast. One tip I can give you is to study ultra-light distros (DSL, fluxbuntu, puppy, etc) and note which applications they use. For example, DSL uses the Dillo browser (and also firefox), and Fluxbuntu uses Kazehakase. It is instructive to see the choices others have made who have gone before you. 

Are you familiar with the Ubuntu Minimal Install CD? You type 'cli' and it installs only a command line environment, then you can add whichever packages you like. That is a good way to build up, for example, a very fast and lightweight Fluxbox system. There are some good tutorials out there, so I will not repeat them. :)

---

### Post by RedSquirrel on 2008-07-28
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Aearenda on 2008-07-28
I would be using the XFCE installation disk for Debian for this job. It is much lighter than Xubuntu in my experience, yet all the same principles apply.

---

