---
title: "Edgy to Fiesty upgrade breaks Gnome and TTY"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Niomi on 2007-04-24
I upgraded from Edgy to Fiesty using Update Manager. Towards the end of my upgrade, X went down. I used the prompt at CTRL-alt-F1 to complete the upgrade. The first time I tried to use apt it told me that dkpg had been interrupted and suggested a command, I ran that command (I remember it being *sudo apt-get --configure -a*) and followed with a dist-upgrade. This returned that there were no packages to be updated, so I rebooted. Since rebooting, I can't get into gnome or even into bash. Upon booting, the Ubuntu screen will hang without filling at all, and then send me into something called Busybox, with an error message:

```
/bin/sh: can't access tty; job control turned off
```

The prompt looks like this:

```
(initramfs) _
```

My machine is an AMD Athalon 2.8 with a gig of RAM, a Nvidia 6600 GPU, and a via motherboard.

---

### Post by dannyboy79 on 2007-04-24
join this thread instead of starting your own. same issue.

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by Niomi on 2007-04-24
I've seen this thread in my searches and I'm not sure if that thread applies to me, since I've upgraded from Edgy instead of using a LiveCD. If I understand what's going on correctly, the feisty liveCD doesn't co-operate with certain kinds of disk drives. However, since I've downloaded everything and am running it all off of my HDD, my problem while exhibiting similar symptoms should be different.

But if I'm misunderstanding the other thread please explain.

Since I make the original post, I discovered that I can get into X if I boot into the 2.6.20-15 generic kernel, but if I try 386 (which is first on my list) I am sent to busybox. However, I can't get proprietary Nvidia drivers to work on the generic kernel, X crashes every time I change from "nv" to "nvidia". I've tried purging and re-installing the three different nvidia drivers with no luck, I suspect the nvidia drivers will only work in the 386 kernel since one of the nvidia packages appears to depend on the 386 kernel. So, even though I can get into X with the generic kernel, it's important to get the 386 kernel functioning properly if I want the proprietary nvidia drivers to run.

---

### Post by dannyboy79 on 2007-04-24
stick with the generic kernel because they stopped using the 386/686 kernel in dapper, if you have a newer processor, you'll be fine with the generic kernel as far as optimizations for your cpu etc etc.

you can even read about it here: (it's from this thread, [http://ubuntuforums.org/showthread.php?t=85917&page=25&highlight=686+generic+kernel%3F](http://ubuntuforums.org/showthread.php?t=85917&page=25&highlight=686+generic+kernel%3F))

I just installed Ubuntu 6.10 Edgy (default install) on Jan 20 2007. On a Athlon XP 2600.

$uname -a
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

I am a new user, but this is what i understand. Correct me if wrong, cos many newbies read these posts.

** For all those who visited this forum thread looking to use processor specific kernels, the current version (6.10 default/generic) has made the k7/686/686-smp kernels OBSOLETE (only for upgrades). I think it applies to all the other processor specific kernels.

**As proof, refer to the "uname -a" output (in Ub 6.10). It says SMP, i686 in the default installation.
Also In Synaptics Pkg Mgr (Ub 6.10), search for "linux-k7". It will describe as OBSOLETE by linux-generic. Same for linux-686/linux-686-smp.

** edit -This might explain why some of the late2006/2007 kernel modifications by users don't show any changes in GRUB. The initial "processor specific kernels" thread was made in year 2005.




As far as the Nvidia driver, it's been a very common problem, see here: [http://ubuntuforums.org/showthread.php?t=421243&page=3](http://ubuntuforums.org/showthread.php?t=421243&page=3)

I think you'll have to use the driver just prior to 9755, was that 9746? that should work.

---

### Post by Chamelion on 2007-04-24
I tried to update my daughter's computer to Edubuntu Feisty from Edgy and was not able to boot anymore. Just to be on the safe side I previously had downloaded the Edubuntu Feisty Live CD.
Then I tried to do the clean install and got what a lot of you are getting.
[HTML]/bin/sh: can't access tty; job control turned off[/HTML]
That basically means that Feisty is not available for her and for a lot of other people.
I already have re installed Ubuntu Feisty twice on my computer. Both times it broke after a few hours. Different problem.
[http://ubuntuforums.org/showthread.php?p=2527806#post2527806](http://ubuntuforums.org/showthread.php?p=2527806#post2527806)
I know that I am being sneaky here, but I really would like an answer. I do love Ubuntu, but I think Feisty might have been released a bit early. 
I am new to Linux and Feisty dangles quiet a few carrots in font of people. I would have been happy to wait a bit longer for a **stable** system but as Linux is free there are other distros that might deliver what they promise.
i might install Ubuntu Feisty a third time onto my computer if I do not get any help and then possibly look towards Sabayon etc. :sad: Thank you for your help.

---

