---
title: "Installation problems"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by caddy400ex on 2010-03-24
Hello,
 
Just to start I am new to Linux and Ubuntu. I have probably spent more hours reading about linux the past 2 weeks than I actually spent doing work <.< . I have a hp pavilion zv6000 running windows xp. I have the HD partitioned with xp on one partition and am using wubi on the other partition. I know I should just do a regular install of Ubuntu on the second partition but I read that it is a really long process to uninstall Ubuntu unless you are using wubi, which is really easy to uninstall through XP. Sorry for the rambling. Ok I did the install on my second partition and everything worked fine. I did some minor customizing through some of the forums on ubuntuforums. After the customizing I realized that Ubuntu is amazingly better than Windows. I rebooted and everything was fine. I then went and did an update and everything still worked good. Rebooted after that and still no problems. I just turned on my computer today and everything was booting up fine until I just got a black screen with the Ubuntu symbol and then I got a straight black screen that said:
 
Init: udevtrigger main process (448) terminated with status 1
Init: udevtrigger post-stop process (449) terminated with status 1
Init: udevmonitor main process (447) killed by term signal
fsck from util-Linux-ng 2.16 /dev/loop0: clean, 137604/1073152 files, 807615/4286464 blocks
Init: networking main process (481) terminated with status 1
 
Cany anybody please explain what this means and if there is a solution besides uninstalling Ubuntu and reinstalling it?
 
Also does anybody knows an easy way to be able to uninstall Ubuntu I would gladly just do an install from a cd iso rather than through wubi. thanks for your help and please remember that I am realllllllllyyyyyyy new to linux and the whole concept behind it.....but I am learning and learning to love it!! lol

---

### Post by caddy400ex on 2010-03-24
also forgot to mention when the black screen shows up I tried typing some commands on it and they will type out but when I hit enter nothing happens....I have tried exit, reboot, and some others.....mostly because I do not know too many commands yet...still a noob

---

### Post by bcbc on 2010-03-24
> **caddy400ex said:**
> Hello,
I have the HD partitioned with xp on one partition and am using wubi on the other partition. I know I should just do a regular install of Ubuntu on the second partition but I read that it is a really long process to uninstall Ubuntu unless you are using wubi, which is really easy to uninstall through XP. Sorry for the rambling. Ok I did the install on my second partition and everything worked fine.

Actually wubi installs ubuntu as a file under your windows file system, not to a separate partition. So unless you're doing something special, your wubi install is likely sitting on your xp partition under c:\ubuntu\...

If you're using ubuntu 9.10 then there is a bug in the wubildr that can cause bootup problems, however I haven't seen the particular problem you are having so don't know if this will help, but here is the [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") anyway. 

If you can't fix it, but have some data you don't want to lose, note that it's possible to mount the file containing your wubi install and pull off data, e.g. after using the liveCD to boot. Or you can back up the entire root.disk file and mount it later to pull off data. Here's an [example]("http://ubuntuforums.org/showthread.php?t=1037874").

---

### Post by caddy400ex on 2010-03-24
Thanks for the help....ubuntu is installed on the other partition...when running the install it asked for the "C:" or "D:" drive and I put it on the D: which is the second partition...thanks for the help again.  I heard that if I just do an install on the second partition rather than use wubi that ubuntu will run faster..do you know if this is true or not?

---

### Post by bcbc on 2010-03-24
> **caddy400ex said:**
> Thanks for the help....ubuntu is installed on the other partition...when running the install it asked for the "C:" or "D:" drive and I put it on the D: which is the second partition...thanks for the help again.  I heard that if I just do an install on the second partition rather than use wubi that ubuntu will run faster..do you know if this is true or not?

That shouldn't make any difference to the performance. I think what you read was referring to installing ubuntu as a dual boot (direct to the second partition), not installing wubi to the second partition. The performance issue is more to do with loop mounting the operating system from a file - whether that file is c:\ubuntu\disks\root.disk or d:\ubuntu\disks\root.disk doesn't matter.

Having said all that, I ran ubuntu using wubi and didn't have any performance problems - but there are other limitations e.g. cannot hibernate, which I use - and potential ntfs corruption.

---

### Post by caddy400ex on 2010-03-24
Yes I did notice that problem with the hibernate....which I constantly use so I am probably going to do a clean install on the second partition not using wubi.  I am having many more problems with other stuff (ie broadcom 4318 wireless drivers) but I believe I can solve them through the other forums.  Thanks again for your help.

---

### Post by bcbc on 2010-03-24
> **caddy400ex said:**
> Yes I did notice that problem with the hibernate....which I constantly use so I am probably going to do a clean install on the second partition not using wubi.  I am having many more problems with other stuff (ie broadcom 4318 wireless drivers) but I believe I can solve them through the other forums.  Thanks again for your help.

You're welcome :) 
If you got the wireless working through wubi there should be no difference with a native install. If you want to hibernate, make sure you have a big enough swap partition when you install - sometimes the default install doesn't give enough (you'll need at least as much swap as your RAM). Getting it to work after installing is possible but painful.

Good luck.

---

### Post by caddy400ex on 2010-03-24
Ok I will keep that in mind when I do the install.  I was NOT able to get the wireless to work though.  I was pretty confused to trying to get ndiswrapper and getting it to run properly.  There are some more posts and routes I am going to try though.

---

### Post by bcbc on 2010-03-24
> **caddy400ex said:**
> Ok I will keep that in mind when I do the install.  I was NOT able to get the wireless to work though.  I was pretty confused to trying to get ndiswrapper and getting it to run properly.  There are some more posts and routes I am going to try though.

For my one machine I use ndiswrapper - I just installed ndisgtk directly from the livecd, and then I had my windows driver on another partition, which I loaded - from menu 'System', 'Administration', 'Windows wireless drivers'. (But that worked on my card which isn't a broadcom so not sure how it would work on yours).
 
Also as I recall I have to rmmod on it prior to hibernating and do a modprobe on resume - otherwise the wireless doesn't start again. I don't hibernate a lot on that machine, so doesn't bug me, but you might want to create a script if you are doing this a lot.
Here's a snippet I found somewhere that worked for me:
Once you have identified the module, create a file called 12modules under /etc/pm/sleep.d and paste this text inside: 

```
#!/bin/bash
    case "$1" in
        hibernate|suspend)
                        rmmod <your module> #insert your module's name
            ;;
        thaw|resume)
            modprobe <your module> #insert your module's name
            sleep 1
            ;;
        *)
            ;;
    esac
```
Then you have to make 12modules executable for it to work.

---

