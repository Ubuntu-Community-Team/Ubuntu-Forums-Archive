---
title: "The Dreaded Kernel-Upgrade!"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by webworldx on 2007-09-03
Well I noticed yesterday that a linux-image-2.6.20-16-generic was available in the Software Updates, and instantly fear ran through me!  I've been on the wrong end of every kernel image upgrade so far, and having to downgrade, modify menu.lst, put up with Ubuntu not booting at all and such... so I just wanted to confirm that this one **won't** break my current setup, cause it to only recognise one of my two CPU cores, disable fglrx or turn off my wireless.

Am I hoping for too much?

---

### Post by JBAlaska on 2007-09-03
I upgraded to 2.6.20-16-generic when it showed up (Very hesitantly lol) and it went off without a hitch on my old FIC-K8-800T AMD64 3200+, Ati 9600Pro system running Feisty and XGL+Compiz Fusion+Emerald. 
I don't have a wireless card nor duel core so I can't help on that.

When in doubt..Take a deep breath...and click LOL

Good luck.

---

### Post by Sef on 2007-09-03
> so I just wanted to confirm that this one won't break my current setup, cause it to only recognise one of my two CPU cores, disable fglrx or turn off my wireless.

There is no way to guarantee 100% that the kernel won't break your system.

---

### Post by oOMartinOo on 2007-09-03
Unfortunately the kernel upgrade has in fact broken my wireless, it no longer detects my NETGEAR WPN511 wireless card (ath0) which used to work brilliantly before the upgrade.

any1 know of a solution to the problem?

---

### Post by cjax1 on 2007-09-03
Hi.

Until this last kernel update none of the others have ever broken anything that I know of. But this last one screwed up GRUB, the menu.lst file. When I rebooted, the entry for Windows XP was no longer there. Ubuntu booted fine and seems to be OK but I've been reading about several other strange problems on these forums with this update but then there's always someone that has trouble with kernel updates. I fixed GRUB OK, luckily I know how to edit grub and put the entry for XP back manually.

That's been my experience. I'm always a little hesitant myself when a new kernel comes out. I think the chances are you'll be fine but you never know.

---

### Post by zero244 on 2007-09-03
I have a Feisty machine and a Edgy machine.
After the initial install of Feisty I haven't done any updates not even software updates. Its running fine so I am going to leave it alone.
With my Edgy machine I installed it and did the initial updates right after install. I dont plan on doing anymore updates with Edgy either.
I think even the security updates have minimal importance, unless your running some kind of server.

---

### Post by Gremlinzzz on 2007-09-03
I thought there was some thing buggy about 2.6.20-16-generic . so i didn't install it either . I went straight to 2.6.22-10-generic
I haven't had any problems with 2.6.22-10-generic

---

### Post by webworldx on 2007-09-03
> **Sef said:**
> There is no way to guarantee 100% that the kernel won't break your system.

That is bad news - as it's the one operation I **least** look forward to.  Is there no way of making this upgrade process easier for end users?  It seems a lot of people have the same problem as I do - and I understand that most of the time it's because users have recompiled the kernel with extras, but it'd be great if there was an option when you uprgaded that said something like "Looks as if you've compiled the kernel with xxx, yyy and zzz on top of it's usual configuration - would you like to enable this for the current kernel upgrade?"


I think i'll be leaving my current version of 2.6.20-16, ignoring the "updates available" icon and waiting for Gutsy...

---

### Post by soma4me on 2007-09-04
Hi,

Just trying to share my experience -- Yeah, the kernel upgrade did break my Feisty Fawn!

Until last night, Feisty Fawn kernel 2.6.20-15 was working flawlessly for me, after the upgrade, it wouldn't load nVidia driver anymore, even after I upgraded the driver from nvidia-glx to nvidia-glx-new, it still wouldn't load it.

Here is the detail thread:

[http://ubuntuforums.org/showthread.php?t=542215](http://ubuntuforums.org/showthread.php?t=542215)

But I must admit, on Dapper Drake (Ubuntu 6.06 LTS), I've never have any issue upgrading kernel, well, not yet anyway....

I've also seen other threads discussing sound card, wireless devices or GRUB stopped working after the upgrade.

It is unfortunately that I read people are hesitant in upgrading kernel, a great operating system shouldn't be like this....But, it is still better than Windows -- at least all I have to do is select the prior version of kernel and I'm back in business!

Personally, I would still select to upgrade kernel the next time it pops up -- hopefully, it'll correct all these problems.....:)

---

### Post by epee on 2007-09-04
Yeah, the last kernel 'upgrade' (a term that can only be losely used to describe the process...) doesn't work for me either. It starts up, then there is some sort of X-term problem and I'm left with a console for login.

So I reboot and pick the earlier (-15) kernel, as every update since has been useless.

I'm disliking Windows XP less and less as time goes by.

---

### Post by PORCODIO on 2007-09-04
DO NOT DO IT!!

I've just upgraded my kernel (I'm on 6.10 i386) and the system is now UNBOOTABLE with the newly installed kernel.

I can choose to boot with other kernels in GRUB, but even with the other kernels my Atheros card is not recognized!!! I don't know how the *** this is even possible, as the older kernels wouldn't have a problem with it before! *** unbelievable, man,,, leave the kernel alone!

---

### Post by webworldx on 2007-09-04
A bit of a feedback since I started this thread... 

I was editing my sources.list last night to upgrade to the latest WINE, and of course, I did a apt-get update, then an apt-get upgrade without thinking, and of course it downloaded the latest kernel images.

I decided to go to sleep with the laptop on and leave the restart for the morning (I hate having to deal with bad problems after midnight), but... on restarting in the morning.... it all works... perfectly.  Wow. I know! I suppose it was just a minor version change rather than a new kernel version (so i'll have to wait for .17 or 22.10 for full confirmation the system breaking doesn't occur anymore), but... it's success from this camp - *and a lot of relief*!

---

### Post by maxfacta on 2007-09-04
My laptop (Satellite Pro P100) fails to boot after upgrading the 2-6-20-generic kernel.
By "fails to boot" I mean just locks up with a black screen, seconds after grub hands over control.

2-6-15-generic still boots, thankfully. No observable side effects.

---

### Post by zurn on 2007-09-04
Since upgrading to the new kernel I get a CRC ERROR - SYSTEM HALTED but I can still boot fine with the previous kernel in the grub menu.

---

### Post by BLTicklemonster on 2007-09-04
Every Kernel upgrade I've ever done messes up X and I have to reconfigure and spend forever trying to get it working again.

Thank God for Envy.

---

### Post by rsambuca on 2007-09-04
PORCODIO, please refrain from using profanity in the forums.

Thank you.

---

### Post by PORCODIO on 2007-09-04
SOLVED!!!

I've "fixed things" by (re)installing the following packages:

* linux
* linux-386
* linux-generic
* linux-restricted-modules-386
* linux-restricted-modules-common
* linux-restricted-modules-generic

some are probably unneeded. YMMV

---

### Post by PORCODIO on 2007-09-04
> **rsambuca said:**
> PORCODIO, please refrain from using profanity in the forums.

Thank you.

I had my system made unbootable by an upgrade and here you come all outraged by my "profanity".

Wow, my "profanity" really must have hurt your feelings, didn't it? You are so sensitive and fragile that a little 4 letter sequence is enough to make you all upset.

Please excuse me for spoiling your day with my "profanity". I hope you will get over it soon.

---

### Post by rsambuca on 2007-09-04
Actually, if you re-read my post that you quoted, nowhere does it say that I was "outraged", "upset", or that I "had my feelings hurt".  I merely politely asked you to refrain from using profanity in the forums.  I also tried to thank you in advance.  

The first two points in the ubuntu forums Code of Conduct are "Be Respectful", and "Be Courteous".  Perhaps you should have a read through the Code prior to posting any more messages.  You can find the [[COLOR="Red"]link to the Code of Conduct here[/COLOR]]("http://www.ubuntu.com/community/conduct").

---

### Post by soma4me on 2007-09-04
> **PORCODIO said:**
> SOLVED!!!

I've "fixed things" by (re)installing the following packages:

* linux
* linux-386
* linux-generic
* linux-restricted-modules-386
* linux-restricted-modules-common
* linux-restricted-modules-generic

some are probably unneeded. YMMV

PORCODIO,

I'd like to get a bit more detail on your solution.    Did you use Synaptic (or apt-get) to uninstall all the 20-16 version of packages?   Did you simply reverse the process to reinstall them?

Interested in giving it a try....Thanks for sharing the information.:)

---

### Post by BLTicklemonster on 2007-09-04
Porcodido, thanks for being kind enough to post that you'd found a solution. Please share it, because you will be helping a lot of people out.

---

### Post by PORCODIO on 2007-09-04
> **soma4me said:**
> PORCODIO,

I'd like to get a bit more detail on your solution.    Did you use Synaptic (or apt-get) to uninstall all the 20-16 version of packages?   Did you simply reverse the process to reinstall them?


I didn't need to uninstall stuff: the packages I mentioned are meta-packages that depend on the latest available versions of the things they install. Just installing them (or in some cases reinstalling, using the Adept Manager)  solved my problem. 

A look at 'dmesg' showed that the kernel wouldn't boot b/c it couldn't find its modules. I still don't know why the earlier kernels no longer could see my wifi card, though.

---

### Post by soma4me on 2007-09-04
PORCODIO,

Thanks for sharing the information.    More questions, sorry ::???: Are you using KDE?   I'm not familiar with Adept Manager, do you use it after you get into KBuntu?   If so, it won't help me much, my x-server won't even start!!

I would have to use 'apt-get install' each one of the the package you've mentioned in 'recovery' mode command line-- unless you (or someone else reading this thread) have other suggestions.....

Thanks again.

---

### Post by PORCODIO on 2007-09-04
Yes, I'm actually on Kubuntu. Anyway, if I hadn't got the Adept Manager, I would do it with "apt-get" on the command line, as you mentioned. "apt-get update" first and then "apt-get install" the packages.

---

### Post by soma4me on 2007-09-05
PORCODIO,

Thanks.    I will give it a shot tomorrow -- getting a bit late.    Will update this thread if it works out -- Fingers crossed........

---

### Post by suntiger on 2007-09-06
>  Originally Posted by PORCODIO  View Post
SOLVED!!!

I've "fixed things" by (re)installing the following packages:

* linux
* linux-386
* linux-generic
* linux-restricted-modules-386
* linux-restricted-modules-common
* linux-restricted-modules-generic

I had the same problem, 2.6.20-16 would lock at the nvidia driver, 2.6.20-15 would load fine.

Using Adept on Kubuntu 7.04 Feisty I reistalled just the following...

* linux-generic
* linux-restricted-modules-common
* linux-restricted-modules-generic

THANKS PORCODIO

---

### Post by soma4me on 2007-09-07
The re-install did NOT work for me I ran the following commands from the 20-16 recovery mode:

```
apt-get update
apt-get install linux-generic
apt-get install linux-restricted-modules-common
apt-get install linux-restricted-modules-generic

```

All 3 "apt-get install" returned the same thing, it says I already have the latest version, nothing removed, nothing installed.

The only way I can get into 20-16 kernel now is by changing xorg.conf file and change driver from 'nvidia' to 'nv', but I also lost all the OpenGL features.

I'm stuck with 2.6.20-15 now.....:(

---

### Post by soma4me on 2007-09-07
Hey Guys,

I finally fixed the problem by re-installing the restricted modules for 2.6.20-16.   Here is what I did -- I specified '--reinstall' and the package name for the specific kernel release: 

First boot into the recovery mode from GRUB menu.    At command line, do the following:

```
apt-get update
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

now I can boot into the new kernel normally :)

Hope this help other frustrated people out there -- Ubuntu is great, but without the helping people in this forum, Ubuntu is nothing!

---

### Post by maxfacta on 2007-09-09
I haven't tried the re-install yet. Not sure if it will help me, as my problem seems different from yours. That is, my 2.6.16 kernel won't even boot.

That said, 2.6.15 is running fine - so here's a question - What's the difference? Nothing obvious to me.

Who can shed light on the difference between 2.6.15 and 2.6.16, and more importantly, should I care enough to try to fix the 2.6.16 kernel?

---

### Post by soma4me on 2007-09-09
maxfacta,

Looking back at your problem, you're right, the re-install may not help you.   But you are seeing grub menu, correct?    Have you try recovery mode?   If you can get into recovery mode, can you check out xorg.0.log file and see if you have any error?

---

### Post by maxfacta on 2007-09-10
yes, Grub is OK, and I'm using it to boot with the 2.6.15 kernel.
After attempting the 2.6.16 kernel, having a lockup, then booting the 2.6.15 kernel, an inspection of logs under /var/log/ shows *nothing* from the 2.6.16 boot.
This makes me suspect the initrd.

---

### Post by soma4me on 2007-09-10
maxfacta,

Wow, you can't even get into 20-16 recovery mode? Maybe enabling boot log will help determining the problem?

HOWTO: Log Boot Messages
[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by maxfacta on 2007-09-11
> **maxfacta said:**
> an inspection of logs under /var/log/ shows *nothing* from the 2.6.16 boot.

I mean, there is no output whatsoever, not even from the kernel.

---

### Post by soma4me on 2007-09-11
maxfacta,

Wow!  This obviously is beyond my capability....If I were in your shoes, I'll probably try uninstalling kernel 20-16 completely, and manually remove 20-16 from grub if it is not automatically removed from uninstallation -- and wait for the next upgrade....Sorry....

---

