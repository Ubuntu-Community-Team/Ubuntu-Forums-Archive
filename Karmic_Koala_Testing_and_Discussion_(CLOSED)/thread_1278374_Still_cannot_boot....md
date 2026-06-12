---
title: "Still cannot boot..."
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carfield on 2009-09-29
With this problem... [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272)

Anyone know how can I check for more information?

---

### Post by jmmL on 2009-09-29
I also had this problem, but I've fixed it now and I've only just seen this bug report.

To fix it I chrooted into karmic from a LiveCD (you could use another distro on your HDD, but I didn't have any). Then, run ```
sudo update-grub2
``` and let it do it's thing. Et voila, you should now have a booting system.

Hope this works.

---

### Post by carfield on 2009-09-29
> **jmmL said:**
> I also had this problem, but I've fixed it now and I've only just seen this bug report.

To fix it I chrooted into karmic from a LiveCD (you could use another distro on your HDD, but I didn't have any). Then, run ```
sudo update-grub2
``` and let it do it's thing. Et voila, you should now have a booting system.

Hope this works.

thanks a lot... but I don't have update-grub2, what package I should install? BTW, if I figure out logging to the system with single user mode, I should able to just run it, right?

---

### Post by bacardiandwatermelon on 2009-09-29
Did this not work for you?
[http://ubuntuforums.org/showthread.php?t=1268160&highlight=chrooted](http://ubuntuforums.org/showthread.php?t=1268160&highlight=chrooted)

---

### Post by jmmL on 2009-09-29
> **carfield said:**
> thanks a lot... but I don't have update-grub2, what package I should install? BTW, if I figure out logging to the system with single user mode, I should able to just run it, right?

Wait, if you can log in, then you're booted? I thought your problem was that your boot froze just after the /scripts/init-bottom message?

"update-grub2" should come with grub, the default bootloader for ubuntu. Grub changed from version 1 to version 2 in the karmic development process. However, because the change is so big, you'll only have grub2 if you did a fresh install of karmic alpha 3 or later. If you've upgraded from jaunty or from an early karmic alpha then I think I'm right in saying that you won't have grub2. Instead, try running ```
sudo update-grub
```

---

### Post by ranch hand on 2009-09-30
"update-grub" is also for grub2.

All you need to do to check what grub you have is to go to /boot/grub and wee if you have a "menu.lst" on a fairly short list of files of a LARGE bunch of files and a "grub.cfg" file.

The grub.cfg file is a generated file every time you run update grub.  This should work fine if you are running Debian based OS' and Win JerryLewis Pro, or whatever they are foisting off on the suckers now.  Grub may not pick up everything on installation but should if you run "sudo update-grub".

There has been a problem with os-prober (part of grub2) and some other distros (Fedora, Gentoo and Mandriva to mention a few). 

You can add custom entries to grub2 in /etc/grub.d.

You can set your preferences for hidden menu and timeout in /etc/default/grub.

There are a lot of threads telling how to do this in this forum.  A search engine is your friend.

  	 	 	 	 	 	  Some grub2 links;
 

 [http://grub.enbug.org/](http://grub.enbug.org/)
 

 [http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)
 

 [http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)
 

 [https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202]("https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202")
 

 [http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")
 

 [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
 

 [http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback")

---

### Post by carfield on 2009-10-01
> Did this not work for you?
[http://ubuntuforums.org/showthread.p...light=chrooted](http://ubuntuforums.org/showthread.p...light=chrooted)No, it doesn't... thx

---

### Post by carfield on 2009-10-01
Thanks, however after running update-grub it still fail... I guess this bug also affect

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901)

But why those directories under /dev/ will fail?? I've also tried to reinstall udev but again it doesn't help....

---

### Post by carfield on 2009-10-03
Juts upgrade to beta... this problem still there :-(

---

### Post by cariboo on 2009-10-04
Could you explain what your problem is, when you cannot boot, does the system freeze? Can you start in recovery mode? What happens? It's pretty hard to solve a problem, when we don't know what it is.

---

### Post by carfield on 2009-10-04
> **cariboo907 said:**
> Could you explain what your problem is, sure> **cariboo907 said:**
> when you cannot boot, does the system freeze? It stop and doesn't go further after it print for /scripts/init-bottom > **cariboo907 said:**
> Can you start in recovery mode? What happens?Yes, I can, after I press alt+ctrl+del to restart, I can go to grub:

"e" to edit
replace the boot parameters from ro xxxx xxxx to "rw init=/bin/bash" then I can boot in single user mode> **cariboo907 said:**
>  It's pretty hard to solve a problem, when we don't know what it is.Here are two problem I can see:

1) Some /dev directory are missing - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901)
2) Upstart is not working, always say [start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused]

Or , will my mount option hurt? I use writeback mode```

UUID=7b566603-851c-43f0-8ec5-2098655bb611 /               ext4    noatime,data=writeback,barrier=0,nobh,errors=remount-ro 0       1
```

---

### Post by ranch hand on 2009-10-04
Are the /dev directories you are missing present on the LiveCD?  I would check that.

If they are I think that I would do an "apt-get dist-upgrade" because that would probably get them in place.  If they are not on the LiveCD, they are probably not in yet and will arrive with updates.

---

### Post by carfield on 2009-10-04
> **ranch hand said:**
> Are the /dev directories you are missing present on the LiveCD?  I would check that.Thanks a lot, but I don't use LiveCD at all...

> **ranch hand said:**
> If they are I think that I would do an "apt-get dist-upgrade" because that would probably get them in place.  If they are not on the LiveCD, they are probably not in yet and will arrive with updates.

I have done "apt-get dist-upgrade" many many times already....

And again, thanks a lot for looking into the problem

---

### Post by ranch hand on 2009-10-05
You really should have some sort of liveCD on hand.  They are just too handy at times to not have one.

If you don't have one now I would wait a while because, as I am sure you have noticed, the repos are a little bogged down at this time.

---

### Post by carfield on 2009-10-05
> **ranch hand said:**
> You really should have some sort of liveCD on hand.  They are just too handy at times to not have one.

If you don't have one now I would wait a while because, as I am sure you have noticed, the repos are a little bogged down at this time.

Thanks but why I need to have one? I can use single user mode to start the system then init most service manually. However, I just want to fix that so that I don't need to init services manually.

Or do you mean start with liveCD will fix?

---

### Post by ranch hand on 2009-10-05
No, I am saying that you should have a LiveCD for emergencys.  It would be nice to know, for instance if the files you are missing are on the Live CD.

Also, you can recover grub-legacy or grub2 from a live CD if something should go wrong and things just won't boot.  I had to do that yesterday on a test platform myself.

Live CDs do not take up a lot of room and they can be very handy in times of need.

As far as 9.10 goes, I have a .iso of it on my main Desktop and update it daily with rsync.  This way I can burn it if I need to and check to see what is on it compared to what I have on my drive.

---

### Post by carfield on 2009-10-05
> **ranch hand said:**
> No, I am saying that you should have a LiveCD for emergencys.  It would be nice to know, for instance if the files you are missing are on the Live CD.

Also, you can recover grub-legacy or grub2 from a live CD if something should go wrong and things just won't boot.  I had to do that yesterday on a test platform myself.

Live CDs do not take up a lot of room and they can be very handy in times of need.

As far as 9.10 goes, I have a .iso of it on my main Desktop and update it daily with rsync.  This way I can burn it if I need to and check to see what is on it compared to what I have on my drive.Thanks a lot, will do. However... I hope someone can provide suggestion to solve my issue....

---

### Post by ranch hand on 2009-10-05
Can you get into the files on this bugger?  What happens if you just create the directories (empty)?

---

### Post by VMC on 2009-10-05
> **carfield said:**
> Thanks a lot, will do. However... I hope someone can provide suggestion to solve my issue....

carfield, according to the [**Bug#430272**]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272") , the status is "Fixed". Have you read and tried the various solutions recorded there?

---

### Post by carfield on 2009-10-05
> **ranch hand said:**
> Can you get into the files on this bugger?  What happens if you just create the directories (empty)?

I can manual create /dev/pts, /dev/snd, /dev/shm in order to make my machine work properly, but when I restart those directories missing again...

Will anyone know how does /dev structure defined, so that I can fix the root cause?

---

### Post by carfield on 2009-10-05
> **VMC said:**
> carfield, according to the [**Bug#430272**]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272") , the status is "Fixed". Have you read and tried the various solutions recorded there?

all I can see is running update and dist-upgrade and new package will fix the problem. Which I've done that everyday already. And this problem still there..... for me.....

---

### Post by ranch hand on 2009-10-05
I think that you are going to have to keep doing that.

A couple of weeks ago we had some boot problems and I had one install that would not boot for about 6 days.  I wonder why they tell you not to use it for production machines?

---

### Post by carfield on 2009-10-07
> **ranch hand said:**
> I think that you are going to have to keep doing that.

A couple of weeks ago we had some boot problems and I had one install that would not boot for about 6 days.  I wonder why they tell you not to use it for production machines?

That is very pity.... can someone help to suggest possible root cause?

---

