---
title: "Cache stuff on startup"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Speed_arg on 2010-03-20
Boot time is important, but me and I think most people cares a lot more about run-time perfonmance than boot speed. 

Unlikely old windows machines which after using them for a while you were like "ok it is slowed down, gotta restart" in ubuntu in modern pcs after runing it a few hours it gets faster since stuff is saved into cache.

I don't really know much about which stuff ubuntu loads, so my opinion is kinda noob, but it would be nice that system stuff and default programs (like by default gedit, firefox, etc) were loaded to ram like some small distros (puppy linux)

Of course this should be according to systems specs. As well as using swap or disabling it (leave it just for hibernate). If you got 4gb like many people nowadays, you barely use 2gb with cache included after some hours, and this is kind of a waste of hardware which could improve stuff mainly for HDD systems.

My 0.02

---

### Post by andrewabc on 2010-03-20
You want to install and run [preload](http://sourceforge.net/projects/preload/)

Preload in 9.10 did not work for me. Hopefully it does in 10.04

It can be found in normal repository.
system->admin->synaptic

> preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times.

---

### Post by _h_ on 2010-03-20
There's a package in the repos called preload, which preloads data into memory based on the file size and uses a small % of RAM.

It even helps with getting to desktop faster too, since it's loaded on startup.

---

### Post by andrewabc on 2010-03-20
> **_h_ said:**
> There's a package in the repos called preload, which preloads data into memory based on the file size and uses a small % of RAM.

It even helps with getting to desktop faster too, since it's loaded on startup.

I wouldn't say small % of ram. It aims for a certain % of free ram space (90%?). There are lots of options you can change in a config file. I'm trying to find the manual now.

It is not supposed to help in getting to desktop (boot time) faster. In fact it may make it take an extra second or so as it has to read all those files into memory on startup.

Also you don't need to "run" preload. Once installed it will start as daemon everytime computer starts.

After a day try command
sudo tail -f /var/log/preload.log
to see how much ram and files are cached.

---

### Post by _h_ on 2010-03-20
> **andrewabc said:**
> I wouldn't say small % of ram. It aims for a certain % of free ram space (90%?).

It is not supposed to help in getting to desktop (boot time) faster. In fact it may make it take an extra second or so as it has to read all those files into memory on startup.

Also you don't need to "run" preload. Once installed it will start as daemon everytime computer starts.

After a day try command
sudo tail -f /var/log/preload.log
to see how much ram and files are cached.

The default is aimed at 30% of your total RAM, but doesn't even use it all in most cases.

I have 3072GB, 30% is 921.6MB and preload currently barely uses 10% of that.

And sometimes it does, sometimes it doesn't help with boot time, but it helps me shedding a few more seconds off boot time.

And I know I don't need to run it, since it runs by itself whenever ubuntu is going. :P

---

### Post by andrewabc on 2010-03-20
> **_h_ said:**
> The default is aimed at 30% of your total RAM, but doesn't even use it all in most cases.

I have 3072GB, 30% is 921.6MB and preload currently barely uses 10% of that.

And sometimes it does, sometimes it doesn't help with boot time, but it helps me shedding a few more seconds off boot time.

And I know I don't need to run it, since it runs by itself whenever ubuntu is going. :P

Here's my preload stats from a [while ago](http://ubuntuforums.org/showthread.php?t=1207174). 

> Preload is using an additional
[Tue Jul 7 23:52:35 2009] readaheading 2784 files
[Tue Jul 7 23:52:56 2009] 1547660kb available for preloading, using 1444600kb of it


I have 3gb of ram. And probably 500mb was being used by OS at time.
So definitely more than 30% of total ram, unless they changed defaults. If you have fresh install or recently added preload, that is why it's not using much. Or you don't run many apps. Also depends on how much ram person has and being used by programs etc (aka different for every person). :P

[Here](http://www.ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application.html) is some info on how to tweak preload to your liking.

My last comment about not needing to start preload was meant for original poster. :)

EDIT:
(Total RAM x model.memtotal) + (RAM available at start x model.memfree) + (Cached memory x model.memcached)
via my above link. based upon free mem.

---

### Post by Asmodai on 2010-03-20
Ah, so that is why I didn't notice any difference with preload - and I wondered why there was no hard disk activity right after startup where preload *should have* read a large number of files from the disk.

Although preload is great (when it works), I think Ubuntu should come with preload preinstalled and activated by default, with an option to turn it off. The average user would probably not know about preload, so they would never get its benefits. An experienced user however could easily turn it off if s/he does not like the concept of precaching.

---

### Post by lean on 2010-03-21
Using preload conflicts with the goal boot time goal of ubuntu. That is booting into the desktop in 10 seconds, and then be in a state with no disk activity.

So the design of preload must be changed. My guess is that it should be done different, depending on whether you have an spinning disk or ssd:
[LIST]
[*]sd. Integrate with ureadahead. Depending on the memory of the system the most popular programs should be loaded. This could be programs that are usually started within 5 minutes of desktop usage. For normal users I would guess it would be things like firefox and chat, and maybe email.
[*]ssd. For an SSD it is okay to load when the user is logged in, since the latency is lower and there is no sound to tick of users. More programs can be loaded after the user have logged in. openoffice e.t.c.
[/LIST]

But actually the most important thing is just to make programs start faster. The same thing optimizations has been done for the kernel, could just as easily be done for other programs.
Read less from the disk, read things in order, simply do less on startup.

---

### Post by andrewabc on 2010-03-21
> **Asmodai said:**
> Ah, so that is why I didn't notice any difference with preload - and I wondered why there was no hard disk activity right after startup where preload *should have* read a large number of files from the disk.

I assume you are referring to it not working in 9.10 for me and probably not for you?
Yah, you have to check logs to see if it is actually working. :P

---

### Post by ubername on 2010-03-21
I've just started messing with preload and am struggling to get it to recognise google-chrome, which installs to /opt/google/chrome
by default

I have changed /etc/preload.conf like this (i.e. added /opt to the start of the line)

mapprefix = /opt;/usr/;/lib;/var/cache/;!/

but I am not seeing anything in preload.state

(I include the output from 'sudo less  var/lib/preload/preload.state | grep /dev' just to show it's actually doing something)

```
john@DEllE520Karmic:~$ sudo less /var/lib/preload/preload.state | grep /opt
john@DEllE520Karmic:~$ 
john@DEllE520Karmic:~$ sudo less /var/lib/preload/preload.state | grep /dev
MAP	1410	10	0	180224	-1	file:///usr/lib/devicekit-disks/devkit-disks-daemon
MAP	1411	10	176128	4096	-1	file:///usr/lib/devicekit-disks/devkit-disks-daemon
MAP	1414	10	180224	4096	-1	file:///usr/lib/devicekit-disks/devkit-disks-daemon
MAP	1995	10	0	114688	-1	file:///usr/lib/devicekit-power/devkit-power-daemon
MAP	1997	10	114688	4096	-1	file:///usr/lib/devicekit-power/devkit-power-daemon
MAP	1999	10	110592	4096	-1	file:///usr/lib/devicekit-power/devkit-power-daemon
EXE	25	0	2350	-1	file:///usr/lib/devicekit-disks/devkit-disks-daemon
EXE	32	0	2550	-1	file:///usr/lib/devicekit-power/devkit-power-daemon
john@DEllE520Karmic:~$ 
```

I have rebooted since changing /etc/preload.conf, and set 
autosave = 360
```
john@DEllE520Karmic:~$ sudo cat /var/log/preload.log
[Sun Mar 21 13:46:37 2010] loading conf from /etc/preload.conf
[Sun Mar 21 13:46:37 2010] loading state from /var/lib/preload/preload.state
[Sun Mar 21 13:46:37 2010] cannot open /var/lib/preload/preload.state for reading, ignoring: No such file or directory
[Sun Mar 21 13:59:44 2010] exit requested
[Sun Mar 21 13:59:44 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 14:07:53 2010] loading conf from /etc/preload.conf
[Sun Mar 21 14:07:53 2010] loading state from /var/lib/preload/preload.state
[Sun Mar 21 14:13:54 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 14:19:54 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 14:25:54 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 14:31:54 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 14:37:54 2010] saving state to /var/lib/preload/preload.state
```

(and yes, chrome has been running all that time!)
Any clues?

---

### Post by Asmodai on 2010-03-21
> **andrewabc said:**
> I assume you are referring to it not working in 9.10 for me and probably not for you?
Yah, you have to check logs to see if it is actually working. :P
Yeah. My log looks like this:
> [Sun Mar 21 00:48:31 2010] loading state from /var/lib/preload/preload.state
[Sun Mar 21 01:48:32 2010] saving state to /var/lib/preload/preload.state
[...]
[Sun Mar 21 04:08:02 2010] exit requested
[Sun Mar 21 04:08:02 2010] saving state to /var/lib/preload/preload.state
[Sun Mar 21 04:09:00 2010] loading conf from /etc/preload.conf
[Sun Mar 21 04:09:00 2010] loading state from /var/lib/preload/preload.state
[Sun Mar 21 04:45:43 2010] exit requestedSo I think it's safe to say it's not doing anything on my system either.
For now, I put a small program in Gnome startup that simply reads all files that appear in preload.state (plus all files in ~/.mozilla/firefox, since "normal" files are not covered by preload).
Now Firefox starts very quickly, even though I have a large number of tabs saved :p
SMPlayer and some other programs also appear instantly.

> **lean said:**
> sd. Integrate with ureadahead. Depending on  the memory of the system the most popular programs should be loaded.  This could be programs that are usually started within 5 minutes of  desktop usage. For normal users I would guess it would be things like  firefox and chat, and maybe email.
I think ureadahead stalls the rest of the boot process until it has read all files, so this might delay boot for a few seconds.
It seems sensible to just change the design rule - once the hard disk is idle, preload should be invoked. At that point, the system would be already fully usable and preload running in the background should not have much of an impact. Especially if it's invoked at the login screen - the system basically just sits there idle for a few seconds while you're entering your password. This time could be put to better use.

---

### Post by Speed_arg on 2010-03-21
> **Asmodai said:**
> Ah, so that is why I didn't notice any difference with preload - and I wondered why there was no hard disk activity right after startup where preload *should have* read a large number of files from the disk.

Although preload is great (when it works), I think Ubuntu should come with preload preinstalled and activated by default, with an option to turn it off. The average user would probably not know about preload, so they would never get its benefits. An experienced user however could easily turn it off if s/he does not like the concept of precaching.

> Using preload conflicts with the goal boot time goal of ubuntu. That is booting into the desktop in 10 seconds, and then be in a state with no disk activity.

So the design of preload must be changed. My guess is that it should be done different, depending on whether you have an spinning disk or ssd:
sd. Integrate with ureadahead. Depending on the memory of the system the most popular programs should be loaded. This could be programs that are usually started within 5 minutes of desktop usage. For normal users I would guess it would be things like firefox and chat, and maybe email.
ssd. For an SSD it is okay to load when the user is logged in, since the latency is lower and there is no sound to tick of users. More programs can be loaded after the user have logged in. openoffice e.t.c.

But actually the most important thing is just to make programs start faster. The same thing optimizations has been done for the kernel, could just as easily be done for other programs.
Read less from the disk, read things in order, simply do less on startup.

Yes, thats what I was talking about, making ubuntu better, not just my pc faster :D:D

Ubuntu should be 100% out of the box, simple outside, but intelligent inside, should change lot of settings depending on system specs, for example for hdd and ssd like you said. 

I always wondered why not start loading user programs while he is loging in (I mean entering password etc) its a waste not using this time that could make start up experience really fast (ubuntu start up is fast in the sense that you get a very responsive desktop, unlikely xp that after you get your desktop you have to wait programs to start up. Lets make it more responsive, as soon as you touch programs load instantly :D)

Ubuntu for succeding, should:

Be free
Be really stupid simple
Be out of the box (not writing 100 commands in console after installing to get stuff working)
Be kick *** fast
Be stable

Many of them are already done, lets try finishing the other points.


My 0.02

---

### Post by ubername on 2010-03-21
So should preload.log show stuff other than? 
> [Sun Mar 21 14:07:53 2010] loading conf from /etc/preload.conf
[Sun Mar 21 14:07:53 2010] loading state from /var/lib/preload/preload.state
[Sun Mar 21 14:13:54 2010] saving state to /var/lib/preload/preload.state

---

### Post by andrewabc on 2010-03-21
> **ubername said:**
> So should preload.log show stuff other than?

Yes.

This appears to be same problem I had with preload in 9.10.

So I guess it hasn't been fixed yet and probably won't be.
Sad :(

not sure if any bugs are already there:
[https://launchpad.net/ubuntu/+source/preload/+bugs](https://launchpad.net/ubuntu/+source/preload/+bugs)

Here is the [bug report](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/299361) for this problem. Feel free to "affects me too" and if you have any other comments. I commented on it in November, seems devs don't care about it :(

---

