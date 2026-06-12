---
title: "Have minimal machine but Fiesty should install -- slooooow?"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by billcase on 2007-07-19
Hi;

I am trying to install Ubuntu 7.04 from a Live CD on a 4-5 year old (or more) IBM desktop (NetVista -- model 83136U) with 256M RAM.  This will be a dual boot system with WindowsXP as the other OS.

I know it's minimal - but should work.  Others have told me that they have successfully installed with 256 RAM.  The Ubuntu disk I am using works as a Live CD on the above machine and installs correctly on another non-IBM 640M RAM machine.

The problem is:

When I boot the Live CD then click on the Install button, the installation loads very slowly with the CD continuing to spin all the while.  It took me 1 hour to get the first intro screen; another couple of hours to get to the language selection screen; and, another couple of hours to get to the Time Zone screen.  Then I quit.

There is probably a hardware problem.  What should I look for?
Or, any suggestions how to by-pass the problem?

---

### Post by taurus on 2007-07-19
Try using the alternate CD to install it instead.

---

### Post by zach12 on 2007-07-19
or install xubuntu


ps i have 256mb ram on my laptop
and the live cd works fine

---

### Post by kerry_s on 2007-07-19
I recommend debian. Ubuntu likes to drop old drivers, as if no one would use it on older machines. :(

xfce4-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

net installer, in case you want to go custom, which is best-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

anything from 256ram down, a custom install is the best option.
What are your full specs?
if your cpu is slow, then you should consider a specialty OS like dsl or puppy.

---

### Post by LowSky on 2007-07-19
i got mine to work on a old dell insprion 8100 that 6 years old
specs included
1ghz pentium 3
256 Ram
30gb HD


Instal was slow took a while but worked,  if you can get it to work try the Alternate CD or Xubuntu as they as less demanding

---

### Post by kerry_s on 2007-07-20
> **LowSky said:**
> i got mine to work on a old dell insprion 8100 that 6 years old
specs included
1ghz pentium 3
256 Ram
30gb HD


Instal was slow took a while but worked,  if you can get it to work try the Alternate CD or Xubuntu as they as less demanding

You got better specs than mine-> [http://www.docs.sony.com/release/specs/PCGF430_mksp.pdf](http://www.docs.sony.com/release/specs/PCGF430_mksp.pdf)

i upgraded the ram to 256 and the hd to 20gig. I use debian-minimal+fluxbox.

---

### Post by ubanchaos on 2007-07-20
well i have a old comp too and it also took a long time to load fiesty but it works well now but try and alternate cd or xbuntu

---

### Post by kbman on 2007-07-20
Try creating a 500 mb swap partition on the drive before installing - that greatly improved the speed of the install for me

- Create Partition
-  mkswap /dev/hdaX
- swapon /dev/hdaX

---

### Post by RedSquirrel on 2007-07-20
> **billcase said:**
> There is probably a hardware problem.  What should I look for? Or, any suggestions how to by-pass the problem?

I think that machine might have integrated graphics, which means it uses part of your RAM for video. 256 MB is the minimum to use the LiveCD, so you're probably below that when the video is factored in.

I would agree that the alternate install CD is the way to go to at least get Ubuntu installed. However, with only 256 MB RAM, once you get it installed it may not be a very responsive system. Xubuntu might be a better option or a custom, barebones install would be marvelous:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Good luck. :)

---

### Post by billcase on 2007-07-22
Hi all:

Spent a whole day trying to get Ubuntu installed.  Left it running overnight stalled on the Timezone page.  Shut it off in the morning.  Had coffee and breakfast.  Was going to download ALT disk.  Said to myself "What the Hell, one more try."

Re-booted; clicked on Install.  Within an hour Ubuntu was up and running.

You 'splain me.

Regards Bill

---

