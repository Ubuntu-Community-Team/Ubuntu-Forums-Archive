---
title: "[SOLVED] Why is Sidux so much quicker? What can we do to help Ubuntu?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2008-10-25
OK. Before I get shouted down for saying this, I've been using Ubuntu on-and-off since Breezy and as my primary OS since Feisty Herd 3 (Edgy was just too unstable).

I just installed [Sidux](http://www.sidux.com/) 2008-3. It's quick. Really quick. And it does everything as well as Ubuntu - wireless is up, web camera is detected, sound works fine (uses ALSA). Boot time is about 15 seconds - for comparison, with my tweaks I've got Intrepid down to 45.

Apart from boot time, power usage is lower (16-17W compared to 19-21W) and the whole system feels quicker and more responsive. Some of this may be down to using plain KDE3 rather than GNOME (Compiz makes no difference), but still, even if I use something like Fluxbox or FVWM Ubuntu still feels slower (e.g. even an 'aptitude update' or 'aptitude search' takes longer). Installation of Sidux took three-and-a-half minutes on my laptop. This compares to anywhere around 10-20 minutes with Intrepid - I never timed it, I just left it to get on.

Why is Sidux so much quicker?

How can we help Ubuntu?

---

### Post by plun on 2008-10-25
Well... something is making Intrepid slower for the moment.:confused:

Can you please install **bootchart** and show us from a sidux boot/start ?

---

### Post by cantormath on 2008-10-25
[http://www.liliputing.com/2008/06/ubuntu-netbook-remix-to-boot-in-5-10.html](http://www.liliputing.com/2008/06/ubuntu-netbook-remix-to-boot-in-5-10.html)

---

### Post by iKonaK on 2008-10-25
```
~$ uptime
 18:40:57 up [COLOR=Red]4 days[/COLOR],  3:20,  2 users,  load average: 0.99, 1.16, 1.10

```i have a desktop pc, 
do you really think it matters that much the boot time  ?
probably if i'd had a laptop would matter...but still....

---

### Post by jfernyhough on 2008-10-25
Boot time is only one aspect (and probably not hugely useful as Ubuntu front-loads the system with services that Sidux doesn't). The whole Sidux system is faster. I've been testing this afternoon - even the Firefox jerky scrolling issue doesn't exist (Compix+Nvidia 177.80).

I'm going to try and do some quantifying.

Sidux:
```
j@sidux:~$ time aptitude search singleton
p   libapache-singleton-perl        - Singleton class for mod_perl
p   libclass-singleton-perl         - implementation of a "Singleton" class

real    0m0.912s
user    0m0.876s
sys     0m0.032s
```

Rebooting to Ubuntu now.

---

### Post by jfernyhough on 2008-10-25
Ubuntu:
```
j@t7200:~$ time aptitude search singleton
p   libapache-singleton-perl        - Singleton class for mod_perl              
p   libclass-singleton-perl         - perl Class::Singleton - Implementation of a "Singleton" class

real	0m2.091s
user	0m1.940s
sys	0m0.136s
```A full second longer - and I don't believe the Ubuntu repo list can be that much larger than the full Debian+Sidux list to take that much longer to search through.

Rebooting to Sidux for bootchart.

---

### Post by OutOfReach on 2008-10-25
It's probably faster because Ubuntu starts up more daemons and processes. (A lot of which are unnecessary)

---

### Post by jfernyhough on 2008-10-25
Bootcharts will go here.

Sidux is first (finally worked out why it wasn't working; had to add init=/sbin/bootchartd to the kernel options). It's a little slower than first boot, I think due to my adding network-manager.

---

### Post by MacUntu on 2008-10-25
I guess that's the downside of a "one size fits all"-OS. Not that I'd say Intrepid is slow, but after turning off all those services and startup programms I don't need, the boot time not only dropped to 25 seconds but also the whole OS feels faster - not very different than Sidux.

PS: Don't touch the default readahead list. Seems it got optimized and it saved a lot of time vs. the one I created using the "profile" kernel parameter.

---

### Post by jfernyhough on 2008-10-25
I must admit I've yet to try trimming the extra services from Ubuntu - I'll give this a go and see what happens, though I'm not sure how this will affect, e.g., the 1-second difference in 'aptitude search'

What's the best way to stop services now? boot-up-manager?

---

### Post by syko21 on 2008-10-25
I usually use sysv-rc-conf but it can really mess your system up if you don't know what you are doing. This guide is a nice starting point [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by InfinityCircuit on 2008-10-25
Compiz Fusion in Ubuntu is far faster than Compiz Fusion in Sidux...it runs much cleaner with less jerking on all of my hardware.  Try setting up Sidux the way Ubuntu is set up and consider the speed gap there.  If you want a simpler system then go use Sidux.

---

### Post by jfernyhough on 2008-10-25
> **InfinityCircuit said:**
> Compiz Fusion in Ubuntu is far faster than Compiz Fusion in Sidux...it runs much cleaner with less jerking on all of my hardware.Complete opposite on my hardware.> Try setting up Sidux the way Ubuntu is set up and consider the speed gap there.That wasn't quite the point of what I was getting at, and I'm not sure you even can. It would probably be possible to set up Ubuntu like Sidux, though.> If you want a simpler system then go use Sidux.That's completely unhelpful. I'd even argue that Sidux has a greater complexity due to its disparate utilities for setup, upgrading, driver installation etc.

What I was asking is, why is Sidux quicker, and how can this be brought into Ubuntu? Is it simply the services started automatically on Ubuntu? How does this explain other performance differences?

I'm picking on Sidux rather than, for example, Fedora as has been done already - for the simple reason that Sidux is, like Ubuntu, based on Debian Sid, the difference being that Ubuntu takes the Sid packages and freezes them for six months.

---

### Post by shafin on 2008-10-25
I got this on my intrepid machine
```
time aptitude search singleton
p   libapache-singleton-perl        - Singleton class for mod_perl              
p   libclass-singleton-perl         - perl Class::Singleton - Implementation of 

real    0m0.931s
user    0m0.880s
sys    0m0.028s

```
Can anyone enlighten me on these? And How do I see a bootchart, I see them everywhere, but cant dig out how to see one for my machine

---

### Post by MacUntu on 2008-10-25
sudo apt-get install bootchart

*reboot*

then look in /var/log/bootchart

---

### Post by wyth on 2008-10-25
I'd really like to know what services people are turning on and off in sysv-rc-conf.  I've used that [linked How To]("http://ubuntuforums.org/showthread.php?t=89491") above for a few years, but there are a number of new and different services in play now, and I'm just not clear on what's absolutely necessary and what's just cruft.  Anyone who's had any luck with trimming the fat care to share what they sheared?

---

### Post by myddewji13 on 2008-10-25
talking about needed/unneeded services...anyone have a link to a list as to which ones do what and which ones are absolutely essential/nonessential?

---

### Post by heavensblade23 on 2008-10-25
Jaunty Jackalope is going to work on boot speed.

---

### Post by syko21 on 2008-10-25
> **heavensblade23 said:**
> Jaunty Jackalope is going to work on boot speed.
Doesn't mean we can't ask the questions now.

---

### Post by chefweb on 2008-10-25
compare 8.10 to 8.04.1

8.10: 31s
8.04.1: 45s    
measured with bootchart
Thinkpad X61t, 4GB, Samsung M6 320GB

---

### Post by jfernyhough on 2008-10-27
Ok. So.

I remembered about disk access being quicker at the start of the disk.

I replaced the Sidux install with an Ubuntu Daily Live (fewer updates to download). This was living in a primary partition I made way back for Mac OS X, first 20GB of the disk.

Installed Nvidia drivers and bootchart.

28 second boot.

*cough*

I'll have a go with Deadline and Shell-style concurrent boot.

--edit
26 seconds with Deadline, concurrency, disabling apmd, usplash, vbe-save services.

---

### Post by Mazza558 on 2008-10-27
This is my desktop on Hardy:

> real	0m7.756s
user	0m1.448s
sys	0m0.156s


Ouch.

---

### Post by philinux on 2008-10-27
Mine.
```
real    0m2.046s
user    0m1.344s
sys    0m0.064s
```I find firefox slow scrolling a pain on some website and when scrolling through
about: plugins

---

### Post by jfernyhough on 2008-10-27
Hmm...

Is Ubuntu Getting Slower?
[http://linux.slashdot.org/article.pl?sid=08/10/27/1212214&from=rss](http://linux.slashdot.org/article.pl?sid=08/10/27/1212214&from=rss)

---

### Post by philinux on 2008-10-27
Whoa that site scrolls way to slow. Like treacle. Yak.

---

### Post by MJWitter on 2008-10-27
Not sure about boot time, but Intrepid feels much snappier than Hardy for me.  My Intrepid No's:
```
real	0m0.510s
user	0m0.480s
sys	0m0.020s
```

---

### Post by d_skillz on 2008-10-27
> **chefweb said:**
> compare 8.10 to 8.04.1

8.10: 31s
8.04.1: 45s    
measured with bootchart
Thinkpad X61t, 4GB, Samsung M6 320GB

If that is really an accurate boot time I am really impressed

---

### Post by DavidONE on 2008-10-28
```
bubba@purgatory:~$ time aptitude search singleton

p   libapache-singleton-perl            - Singleton class for mod_perl                                                                               
p   libclass-singleton-perl             - perl Class::Singleton - Implementation of a "Singleton" class                                              

real	0m1.474s
user	0m1.224s
sys	0m0.076s

```

There's a large range of figures being posted - but without machine specs they're meaningless.  Curious to know what MJWitter is using that makes his three times quicker than mine.

---

### Post by MJWitter on 2008-10-28
> Curious to know what MJWitter is using that makes his three times quicker than mine.
Using Core 2 Quad Q9300, 4 GB Ram, nVidia 8800 GT 512MB, 2x 500GB drives in raid 0.
I Have also disbaled a couple of things like bluetooth and Tracker, and enabled others such as MySQl.

---

### Post by jfernyhough on 2008-10-28
When I first did those numbers it was a comparison between Hardy and Intrepid - same machine, same setup, same services installed, but Intrepid was a whole second slower.

I'm now running the same Intrepid with a Kernelcheck-compiled 2.6.28-rc2 and get these numbers:

```
j@t7200:~$ time aptitude search singleton
p   libapache-singleton-perl        - Singleton class for mod_perl              
p   libclass-singleton-perl         - perl Class::Singleton - Implementation of 

real	0m1.061s
user	0m0.992s
sys	0m0.064s
```I'm also running Deadline as scheduler, not CFQ (added elevator=deadline to GRUB boot options).

The Intrepid kernel can't be causing this much of a slowdown, surely?

---

### Post by DavidONE on 2008-10-28
> **MJWitter said:**
> Using Core 2 Quad Q9300, 4 GB Ram, nVidia 8800 GT 512MB, 2x 500GB drives in raid 0.
I Have also disbaled a couple of things like bluetooth and Tracker, and enabled others such as MySQl.

OK - so your results can be explained by extra horsepower.  I've disabled Bluetooth, Tracker, Login Sound, Remote Desktop, Visual Assistance in Sessions and Bluetooth in Services.

Overall, 8.10 feels much snappier than 8.04, although I've not done comparative tests so it could be just the warm glow of the new release fooling me.

---

### Post by philinux on 2008-10-28
Same machine.

[FONT=Fixedsys]Intrepid
real    0m2.046s
user    0m1.344s
sys    0m0.064s

Hardy
real    0m1.837s
user    0m1.568s
sys    0m0.076s

The trouble is if you keep repeating the search you get different numbers each time. 
[/FONT]

---

### Post by DavidONE on 2008-10-28
> **philinux said:**
> The trouble is if you keep repeating the search you get different numbers each time.

You're right - I just retried and got:

```
real	0m0.584s
user	0m0.536s
sys	0m0.044s

```

And I'm now consistently getting those figures.  Is the search cached?

---

### Post by Wolki on 2008-10-28
> **DavidONE said:**
>  Is the search cached?

The search itself probably isn't, but apt-cache needs to read the apt-database from the disk, and the linux kernel will cache disk reads in RAM.

---

