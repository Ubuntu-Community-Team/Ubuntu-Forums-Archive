---
title: "Facebook boned on Intrepid"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by saracen on 2008-09-12
Does anyone else have a serious problem using Facebook on Intrepid?  My CPU spikes to 100%, scrolling is really really slow, the whole UI becomes very slow to respond, and Firefox sometimes crashes... what's going on?  :confused:

---

### Post by Nullack on 2008-09-12
What specific process(es) is taking the CPU? - you could study top to see.

What video driver do you use?

---

### Post by saracen on 2008-09-12
The process that's taking up CPU is Firefox.

I'm using the 'nvidia' driver - version 173 and running compiz.

---

### Post by OliW on 2008-09-12
Use the latest beta driver (177.70).

You'll need to reinstall it every kernel upgrade (which can be a bit of a pain in the behind - takes about three minutes each time once you know what you're doing) but you'll get blazing performance improvements.

You can get it from their Linux support forums:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

To install, drop to a hard terminal and:
```
# kill gdm
sudo /etc/init.d/gdm stop

# run the driver install (defaults are fine)
sudo sh NVIDIA-Linux-x86-177.70-pkg1.run

# start gdm again
sudo /etc/init.d/gdm start
```

There is a performance thread that suggests adding some stuff to your xorg.conf. I HIGHLY suggest doing this. For me, it gave me a 50% performance boost (on top of the improved driver performance!)

It's a little more tricky when you have a kernel update. I suggest booting to the kernel's recovery mode, and:
```
# moving xorg.conf out the way
mv /etc/X11/xorg.conf /etc/X11/bak.xorg.conf

# getting to the right runlevel
telinit 3

# that starts GDM so once you're in X, kill, as before, drop to a terminal, and:
/etc/init.d/gdm stop

# if you're root, cd to wherever the file is, for me:
cd /home/oli

# install, as before.
sh NVIDIA-Linux-x86-177.70-pkg1.run

# then move your xorg.conf back into play
mv /etc/X11/bak.xorg.conf /etc/X11/xorg.conf

# and start gdm up again
/etc/init.d/gdm start
```

There might well be a less fiddly way of doing upgrades but I don't know it.

---

### Post by saracen on 2008-09-12
OliW: Did you have the problem I am facing and did the driver upgrade solve that problem?  I don't think it's a driver issue - I think it's a firefox / flash issue.

---

### Post by klim8 on 2008-09-12
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/113184](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/113184)

Add [www.facebook.com](www.facebook.com) as a new testcase.

---

### Post by OliW on 2008-09-12
I did have the same problem. I tried upgrading to Flash 10 first and that did make a difference on some sites, but it didn't help with the new Facebook design.

Then the beta nvidia driver made life worth living again.

I should add that the performance problem was mainly localised to the 8*** and 9*** series cards. If you have one of those, chances are this is definitely your problem.

If you're on a later card, it's worth checking out the nvnews forums, perhaps even posting there. They're probably going to suggest you upgrade too though.

If you're on a 6***, your hardware might not be supported by the latest driver. 7*** should be fine, but as far as I know, it's not effected by the same bug so performance increase might be minimal.

---

### Post by Nullack on 2008-09-12
> **OliW said:**
> Use the latest beta driver (177.70).

You'll need to reinstall it every kernel upgrade (which can be a bit of a pain in the behind - takes about three minutes each time once you know what you're doing) but you'll get blazing performance improvements.

You can get it from their Linux support forums:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

To install, drop to a hard terminal and:
```
# kill gdm
sudo /etc/init.d/gdm stop

# run the driver install (defaults are fine)
sudo sh NVIDIA-Linux-x86-177.70-pkg1.run

# start gdm again
sudo /etc/init.d/gdm start
```

There is a performance thread that suggests adding some stuff to your xorg.conf. I HIGHLY suggest doing this. For me, it gave me a 50% performance boost (on top of the improved driver performance!)

It's a little more tricky when you have a kernel update. I suggest booting to the kernel's recovery mode, and:
```
# moving xorg.conf out the way
mv /etc/X11/xorg.conf /etc/X11/bak.xorg.conf

# getting to the right runlevel
telinit 3

# that starts GDM so once you're in X, kill, as before, drop to a terminal, and:
/etc/init.d/gdm stop

# if you're root, cd to wherever the file is, for me:
cd /home/oli

# install, as before.
sh NVIDIA-Linux-x86-177.70-pkg1.run

# then move your xorg.conf back into play
mv /etc/X11/bak.xorg.conf /etc/X11/xorg.conf

# and start gdm up again
/etc/init.d/gdm start
```

There might well be a less fiddly way of doing upgrades but I don't know it.

I dont recommend compiling your own kernel module.

Use the repo's package for the driver.

---

### Post by OliW on 2008-09-12
That's a fair point, Nullack. 

I've been doing this since Hardy so I never thought to look for an Ubuntu sanctioned 177.* release. 

Install nvidia-glx-177 (I'm not sure if there are any other steps). You'll probably still want to follow the performance instructions detailed on nvnews, as they do bring hefty improvements.

---

### Post by klim8 on 2008-09-12
I think that flashplugin non-free is the real offender here. I'm having the same problems with an Intel 945 graphics chip

---

### Post by super.rad on 2008-09-12
I have flashplugin, nvidia 177 driver and firefox all installed from intrepid's repos and have no problems at all on facebook (or pretty much anyother flash site)
For the nvidia driver i just installed nvidia-glx-177 and then as root ran "nvidia-xconfig"

---

### Post by OliW on 2008-09-12
Here's an almost superb page for telling if it's Flash or not. Scroll down to the bottom of this page:
[http://eu.starcraft2.com/artwork.xml](http://eu.starcraft2.com/artwork.xml)

It does use some Flash at the top but that should be negated by scrolling it off the page. You could disable Flash too if you want to make sure.

But if that transparent PNG at the bottom causes Firefox to melt down, upgrading the driver and adding the performance tweaks will probably fix it.

If that page works fine, the driver might not do anything for you and it could well be Flash.

---

### Post by Jazzva on 2008-09-12
Hi. I was wondering if you have nspluginwrapper installed. Thanks for the answer.

---

### Post by psyke83 on 2008-09-12
> **saracen said:**
> Does anyone else have a serious problem using Facebook on Intrepid?  My CPU spikes to 100%, scrolling is really really slow, the whole UI becomes very slow to respond, and Firefox sometimes crashes... what's going on?  :confused:

It's absolutely, 100% because of Flash. Intrepid still uses beta 2 of the plugin with well-known performance problems and stability problems. Do a search of this subforum for either Flash, PulseAudio or Facebook, and you'll see threads discussing it.

A newer version of Flash without these issues will be released soon:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14)

---

### Post by inportb on 2008-09-12
I'd just disable Flash (with flashblock) for now; you don't need Flash to use Facebook...

---

### Post by Nullack on 2008-09-12
> **psyke83 said:**
> It's absolutely, 100% because of Flash. Intrepid still uses beta 2 of the plugin with well-known performance problems and stability problems. Do a search of this subforum for either Flash, PulseAudio or Facebook, and you'll see threads discussing it.

A newer version of Flash without these issues will be released soon:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14)

13 days since the libs were said to be in progress. Hope this gets done soon.

---

### Post by dasunst3r on 2008-09-12
I'm on Hardy Heron, and the same issue happened to me as well.  In Firefox, I installed the FlashBlock extension to reduce processor usage, but good-listed Facebook.  After removing Facebook from the "good-list," processor usage dropped back down to 0.  You should try it.

---

### Post by Nullack on 2008-09-12
> **dasunst3r said:**
> I'm on Hardy Heron, and the same issue happened to me as well.  In Firefox, I installed the FlashBlock extension to reduce processor usage, but good-listed Facebook.  After removing Facebook from the "good-list," processor usage dropped back down to 0.  You should try it.

I'm not sure this is the way to go. Some items please:

* Intrepid uses a flash revision that is quite different to hardy
* Since flash's code remains unchanged with this plugin, you dont get something for nothing. What is the plugin actually doinh to npviewer.bin? At what expense is less utilisation for npviewer.bin costing to the flash end user experience?

---

### Post by autocrosser on 2008-09-12
Where is the link to the performance thread?

Thanks mate!!

Never mind--I found it--thanks for the information!!!!

> **OliW said:**
> That's a fair point, Nullack. 

I've been doing this since Hardy so I never thought to look for an Ubuntu sanctioned 177.* release. 

Install nvidia-glx-177 (I'm not sure if there are any other steps). You'll probably still want to follow the performance instructions detailed on nvnews, as they do bring hefty improvements.

---

### Post by dizzogg on 2008-09-13
I removed flashplugin-nonfree and installed the latest flash 10 plugin from adobe and all the problems you guys mentioned above have disappeared.

---

### Post by Robertjm on 2008-09-13
Not just Firefox. I was having big problems with FF and so installed Opera. Some of the same issues too. Also, I've been using the "new" Facebook page and they seem to be messing with locations of items, so it wouldn't surprise me if its on FBook's side.

Robert

> **saracen said:**
> Does anyone else have a serious problem using Facebook on Intrepid?  My CPU spikes to 100%, scrolling is really really slow, the whole UI becomes very slow to respond, and Firefox sometimes crashes... what's going on?  :confused:

---

