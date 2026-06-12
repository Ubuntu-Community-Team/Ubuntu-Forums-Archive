---
title: "Surprise of today's upgrade"
date: 2009-10-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-10-29
well..of course this is about karmic, since that forum is closed, I might as well put this here...Todays update just made me love ubuntu more:popcorn::
Today's sreadahead and ureadahead update just make my system boot FASTER!..i donno if this is true for everyone, but it surely did become faster in my case..I just want to shout WOW...
It used to take about 1 min to boot from grub to gdm, now it takes about 30 secs, and login takes about the same amount of time as before(slightly less).


This surely is a surprise ON the release day!

can't wait for lucid testing.....im all itchy now..


for those who havn't get this update: use main server and upgrade...

Am I too emotional?


edit: not to mention the feeling that my system is runner snappier...

---

### Post by MacUntu on 2009-10-29
Mr. Remnant seems to be at boot time hacking again. :D

But that's nothing official in Karmic (yet?). Are you using a PPA or did you build ureadahead from bzr?

---

### Post by Vanishing on 2009-10-29
> **MacUntu said:**
> Mr. Remnant seems to be at boot time hacking again. :D

But that's nothing officially in Karmic (yet?). Are you using a PPA or did you build ureadahead from bzr?

oh..i totally forgot about the ppa...
lol..yea i had the ppa...:popcorn::p

---

### Post by flipper9 on 2009-10-29
Willing to share the link to the PPA? ;)

---

### Post by Vanishing on 2009-10-29
> **flipper9 said:**
> Willing to share the link to the PPA? ;)

sure..why not:
but proceed with caution:
[https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa)

---

### Post by dresden on 2009-10-29
I thinks this is the one i will test it too see 

[https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa)

---

### Post by paul_in_london on 2009-10-29
You can find it on this page:

[http://www.tuxradar.com/content/vista-windows-7-ubuntu-904-and-910-boot-speed-comparison](http://www.tuxradar.com/content/vista-windows-7-ubuntu-904-and-910-boot-speed-comparison)

---

### Post by Vanishing on 2009-10-29
> **paul_in_london said:**
> You can find it on this page:

[http://www.tuxradar.com/content/vista-windows-7-ubuntu-904-and-910-boot-speed-comparison](http://www.tuxradar.com/content/vista-windows-7-ubuntu-904-and-910-boot-speed-comparison)

this one is without this ppa, the "original" version of karmic.
this ppa provides more of an "on the edge but official" boot experience...give it a try.
correct me if im wrong..
thank you!

---

### Post by paul_in_london on 2009-10-29
> UBUNTU WANTZ MOAR FASTER COOKIEZ PLZ!

Scott James Remnant (not verified) - October 29, 2009 @ 6:41pm

I guess you're using a rotational hard drive rather than SSD?

If so, out of interest, could you try the following on Ubuntu 9.10 and see what kind of change it makes:

sudo apt-add-repository ppa:ubuntu-boot/ppa
sudo apt-get update
sudo apt-get dist-upgrade

This should install a new kernel image and replace sreadahead with ureadahead. Give it a reboot to reprofile, then the next reboot may be faster.

I'd like to know the results (scott@ubuntu.com)
err

Anonymous Penguin (not verified) - October 29, 2009 @ 6:43pm

that should be add-apt-repository ;-)


The result is a customised 2.6.31-14, but I'd need to add an entry in my grub.cfg because I use the /vmlinuz and /vmlinuz.old symlinks to pick up the two most recent kernels.

In my case these are:

```
lrwxrwxrwx 1 root root 37 2009-10-14 02:25 /vmlinuz.old -> boot/vmlinuz-2.6.32-020632rc3-generic
lrwxrwxrwx 1 root root 37 2009-10-16 20:19 /vmlinuz -> boot/vmlinuz-2.6.32-020632rc5-generic
```

---

### Post by Vanishing on 2009-10-29
> **paul_in_london said:**
> The result is a customised 2.6.31-14, but I'd need to add an entry in my grub.cfg because I use the /vmlinuz and /vmlinuz.old symlinks to pick up the two most recent kernels.

In my case these are:

```
lrwxrwxrwx 1 root root 37 2009-10-14 02:25 /vmlinuz.old -> boot/vmlinuz-2.6.32-020632rc3-generic
lrwxrwxrwx 1 root root 37 2009-10-16 20:19 /vmlinuz -> boot/vmlinuz-2.6.32-020632rc5-generic
```

what im saying is :the vid is before using the ppa, and james actually tried to tell him to test with the ppa..o.o right?

---

### Post by MacUntu on 2009-10-29
Holy crap! Went down from 31s to 22s (Core Duo T2400, 2.5" 7200rpm HDD). *stunning*

---

### Post by Vanishing on 2009-10-29
> **MacUntu said:**
> Holy crap! Went down from 31s to 22s (Core Duo T2400, 2.5" 7200rpm HDD). *stunning*

just love this..
im using a shitty sony vaio atm..so its not as fast, but its way faster than before.:p


more plz!

---

### Post by paul_in_london on 2009-10-29
Yeah, I just meant I haven't tried the modified 2.6.31-14 yet.

Cheers.

---

### Post by MacUntu on 2009-10-29
I mean I know this machine is able to do ~20s but that was with a tailored kernel, boot files moved together, and readahead list sorted by blocks - now I'm just using a default installation with the PPA. Good job!

---

### Post by Vanishing on 2009-10-29
> **paul_in_london said:**
> Yeah, I just meant I haven't tried the modified 2.6.31-14 yet.

Cheers.

oh..
strange that i cant see the new kernel in my system, just sreadahead and ureadahead, but the boot experience is definitely better..o.o

---

### Post by jpmelos on 2009-10-29
Wow, I sure want to test that! :D Thank you for the info! :D

---

### Post by paul_in_london on 2009-10-29
Hmm. This is part of the ouput I got from aptitude when I updated/upgraded:

```
Setting up ureadahead (0.90.2-1) ...

Setting up sreadahead (1:0.90.2-1) ...
Removing obsolete conffile /etc/init/sreadahead.conf
Removing obsolete conffile /etc/cron.monthly/sreadahead

[COLOR="Red"]Setting up linux-headers-2.6.31-14 (2.6.31-14.48+ureadahead2) ...
Setting up linux-headers-2.6.31-14-generic (2.6.31-14.48+ureadahead2) ...[/COLOR]
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-libc-dev (2.6.31-14.48+ureadahead2) ...

```

---

### Post by MacUntu on 2009-10-29
Bootcharts:

[ATTACH]133586[/ATTACH]  [ATTACH]133587[/ATTACH]

Now somebody please buy me a SSD. :D

---

### Post by Vanishing on 2009-10-29
> **paul_in_london said:**
> Hmm. This is part of the ouput I got from aptitude when I updated/upgraded:

```
Setting up ureadahead (0.90.2-1) ...

Setting up sreadahead (1:0.90.2-1) ...
Removing obsolete conffile /etc/init/sreadahead.conf
Removing obsolete conffile /etc/cron.monthly/sreadahead

[COLOR="Red"]Setting up linux-headers-2.6.31-14 (2.6.31-14.48+ureadahead2) ...
Setting up linux-headers-2.6.31-14-generic (2.6.31-14.48+ureadahead2) ...[/COLOR]
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-libc-dev (2.6.31-14.48+ureadahead2) ...

```

wait..nvm..lol..i was a fool

---

### Post by zika on 2009-10-29
1. If I do upgrade from ppa mentioned above will I be able to use 2.6.32 and 2.6.31-rt kernel?
2. If I do upgrade from ppa mentioned above will I close my machine for official upgrades concerning sreadahad and boot ...?

---

### Post by keybuk on 2009-10-29
Glad that the PPA updates are working for you ;-)  It's just a shame we didn't get it into the release (ok, I only started writing ureadahead last Thursday, but still :p)

The GOOD NEWS is that if the PPA testing goes well, we'll put this into karmic as a Stable Release Update!

Right now though, you do need to be using the kernel in that PPA - if you're using a different kernel (e.g. rt) it won't work.  If you want to do a custom kernel, you can get the patch that you'll need to apply from "bzr branch lp:ureadahead"

(it adds a couple of trace events that ureadahead uses)

---

### Post by keybuk on 2009-10-29
Just had a thought...

You only need the kernel from the PPA *once*; if you're using a different flavour, or a custom build, boot from the PPA kernel on your first boot.

Check that you've got pack (and maybe *.pack) files in /var/lib/ureadahead, then you can reboot happily into any other kernel.

You won't get *quite* the same kick, as it'll be reading the wrong set of kernel modules, but it'll almost certainly be better than it was before.

(The kernel patches are used for tracing, they're not needed for running ureadahead once you have a pack)

---

### Post by paul_in_london on 2009-10-29
Unfortunately it doesn't work for me. I don't use "quiet" as a boot parameter and I saw a message about ureadahead failing. I wanted to post the message here, but it's nowhere to be found in the log files:

[https://answers.launchpad.net/ubuntu/+question/87272](https://answers.launchpad.net/ubuntu/+question/87272)

---

### Post by godhika on 2009-10-29
I must admit I doubted that the 10s for lucid were possible (even though I am still expecting that my system will take a little  bit longer)- but after this update I can only say, I think I was wrong. That was really amazing fast (compared with before) - congratulations to everyone in the ubuntu-boot team.

---

### Post by Vanishing on 2009-10-29
> **godhika said:**
> I must admit I doubted that the 10s for lucid were possible (even though I am still expecting that my system will take a little  bit longer)- but after this update I can only say, I think I was wrong. That was really amazing fast (compared with before) - congratulations to everyone in the ubuntu-boot team.

james deservers applause..
lets give it to him...

---

### Post by NCLI on 2009-10-29
Great work!=D>

---

### Post by flipper9 on 2009-10-29
WOW! :KS

My little netbook (Asus Eee 1000h, 2gb RAM, 1.6ghz Atom, 160gb SATA) just booted (after a couple times) in like half the time! Awesome! :D

---

### Post by zika on 2009-10-30
> **keybuk said:**
> Just had a thought...

You only need the kernel from the PPA *once*; if you're using a different flavour, or a custom build, boot from the PPA kernel on your first boot.

Check that you've got pack (and maybe *.pack) files in /var/lib/ureadahead, then you can reboot happily into any other kernel.

You won't get *quite* the same kick, as it'll be reading the wrong set of kernel modules, but it'll almost certainly be better than it was before.

(The kernel patches are used for tracing, they're not needed for running ureadahead once you have a pack)Does update-initramfs fix other kernel?

---

### Post by klim8 on 2009-10-30
> **zika said:**
> Does update-initramfs fix other kernel?

No, file usage statistics (used by ureadahead) can only be gathered using the new (patched) kernel.

---

### Post by celticbhoy on 2009-10-30
Is anyone else having probs with the keyserver?

---

### Post by klim8 on 2009-10-30
> **celticbhoy said:**
> Is anyone else having probs with the keyserver?

I had problems yesterday. I think it is caused by people upgrading to karmic. Servers are really busy

---

### Post by andrewabc on 2009-10-30
As far as I'm aware keyserver has not worked for me for several months. Others have had problems before, so I dunno if it is my ISP blocking it.

---

### Post by zika on 2009-10-30
> **andrewabc said:**
> As far as I'm aware keyserver has not worked for me for several months. Others have had problems before, so I dunno if it is my ISP blocking it.It worked for me yesterday, just new method of authentication stalled so I had to use old style and be patient.

---

### Post by ktp on 2009-10-30
> **celticbhoy said:**
> Is anyone else having probs with the keyserver?

It was really slow for me today...just let it keep working and finally got through.  I love the first few weeks of a release.

---

### Post by LittleKoy on 2009-10-31
I upgraded using the ppa, but when starting it says something about ureadahead(-others?) being killed by ABRT, and exiting with state 4.

So, it would appear that what I installed is not working, BUT the boot it is definitely faster. I timed it about 2 days ago, and the boot time was about 50s GRUB->Desktop/0% CPU, but now is something like 34s!

---

### Post by artir on 2009-10-31
[IMG]http://img510.imageshack.us/img510/8696/josepckarmic200910316.png[/IMG]

But xsplash is a bit choppy

---

### Post by NCLI on 2009-10-31
Unmodified kernel?

If so: WOW. I guess 10s really is within reach for Lucid.

---

### Post by MacUntu on 2009-10-31
> **artir said:**
> http://img510.imageshack.us/img510/8696/josepckarmic200910316.png

But xsplash is a bit choppy

Now post the full chart... :*)

---

### Post by artir on 2009-10-31
> **MacUntu said:**
> Now post the full chart... :*)
I disabled the extra 45 seconds of wait in bootchart, so that's why it isn't a minute.

The kernel is the one provided in the PPA

---

### Post by Vanishing on 2009-10-31
5  more days to go..:p

---

### Post by MacUntu on 2009-10-31
> **artir said:**
> I disabled the extra 45 seconds of wait in bootchart, so that's why it isn't a minute.

That's why your chart is incomplete, thus not representing the full boot process.

---

### Post by Starks on 2009-10-31
Was pybootchartgui updated to take into account all the Karmic changes made to bootchart and bootchart-java to better represent boot times?

---

### Post by andrewabc on 2009-10-31
> **MacUntu said:**
> That's why your chart is incomplete, thus not representing the full boot process.

And if you include the 45 second delay, you include lots of stuff that happens after you get to the desktop. Thus you can't use the 'time' in the bootchart as it is just 45 seconds added to what bootchart used before.

Default bootchart on my SSD shows 51 seconds. At 15 second mark my music player (audacious) is playing music. I wasn't even in a rush to start it either, I could probably shave another second or two off.

Non 45 second delay bootchart is 6 seconds.

I really prefer looking at 6 seconds, instead of 45 seconds which has 40 seconds of non boot stuff (web browsing/ music player etc).
Comparing bootcharts with the added 45 seconds will make comparisons much more difficult and impossible. Yes it misses a couple things after GDM such as gnome-clock-app or indicator-message, but those are apps that are starting.

See [here](http://ubuntuforums.org/showpost.php?p=8208190&postcount=624) for both my bootcharts. EDIT: png on forum is currently broken. So if bootcharts looks small and squished that's why.

They really should have made the extra time something like 5 or 10 seconds. 45 is a bit long and if your computer has not gotten to a fully working desktop 45 seconds after GDM then you have a >10 year old computer.

---

### Post by zekopeko on 2009-10-31
It takes me around 90 sec to boot to a fully working desktop :(

And that's on a platform that they use for benchmarking the boot improvements. I do have a spinning disk though.

---

### Post by MacUntu on 2009-10-31
> **Starks said:**
> Was pybootchartgui updated to take into account all the Karmic changes made to bootchart and bootchart-java to better represent boot times?
Working fine here (it's only parsing and drawing, so it just needs to care about bootchart's output format).

> **andrewabc said:**
> I really prefer looking at 6 seconds
Why not make it stop earlier, like after three seconds? :p

> **andrewabc said:**
> which has 40 seconds of non boot stuff (web browsing/ music player etc).
Do you want to measure your boot time or listen to music and browse the internet? ;)

> **andrewabc said:**
> will make comparisons much more difficult and impossible
You just need to take a closer look at your charts - there's more than the now useless 'time' value. The boot process is finished when your desktop becomes usable. That is, when there's no activity in the chart's graphs.

Your first chart starts idling after 12 seconds - that's your boot time. Now you can reduce those 45 seconds by the amount of idle time in the graphs - in your case around 35 seconds. If you remove the whole 45 seconds the chart will be cut off before your session is ready thus being useless.

In short: don't blindly change or remove those 45 seconds sleep.

---

### Post by Starks on 2009-10-31
Still a minute to a working desktop...

[http://img682.imageshack.us/img682/5813/kingfisherlucid20091031.png](http://img682.imageshack.us/img682/5813/kingfisherlucid20091031.png)

BTW, when did these new attachment resolution restrictions get put into place here?

---

### Post by Vanishing on 2009-10-31
> **MacUntu said:**
> 

Why not make it stop earlier, like after three seconds? :p



lol.that way you are looking for an electronic dictionary..:D

---

### Post by Ellipsis on 2009-11-01
I applied the same ppa patches:

There was a pretty big speed boost (almost 20 seconds off boot time). I wonder why some people are getting this boost and others are not hmm. 

I am done "booting" at about 18 seconds. 

btw For some reason Ubuntu doesn't detect my processor as Athlon II 245 @3.2 GHz

---

### Post by Bordi on 2009-11-01
> **zekopeko said:**
> It takes me around 90 sec to boot to a fully working desktop :(
..and 52 sec @ my system. Why does it take so long? :(

[-> bigger image]("http://media.ubuntuusers.de/forum/attachments/2208053/teebook-karmic-20091101-19.png")

---

### Post by plun on 2009-11-01
Ubuntu-Geek is up with a manual

[http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html)


--

---

### Post by artir on 2009-11-01
This is the full chart with bootchart-java:
[http://img215.imageshack.us/img215/1390/josepckarmic200911012.png](http://img215.imageshack.us/img215/1390/josepckarmic200911012.png)

---

### Post by MacUntu on 2009-11-01
> **artir said:**
> This is the full chart with bootchart-java:
[http://img215.imageshack.us/img215/1390/josepckarmic200911012.png](http://img215.imageshack.us/img215/1390/josepckarmic200911012.png)

Ok, andrewabc was right: with ubuntuone kicking in, it's hard to tell when your system gets usable (look at Bordi's chart - there it's pretty easy to tell that the boot did not take 52s).

Guess I'd take the last bigger CPU spike at 32s.

---

### Post by vishalrao on 2009-11-01
about 25 seconds from grub menu to login screen on ubuntu and about 20 seconds on kubuntu for me on my Q6600 CPU with 7200 rpm HDD (thanks to no xsplash i believe) - this before adding ubuntu-boot ppa. after adding my kubuntu boot went up by 2 seconds :) so waiting for further work by SJR... or maybe i should just go out and get an SSD :D

---

### Post by flipper9 on 2009-11-01
> **plun said:**
> Ubuntu-Geek is up with a manual

[http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html)


--

That's a manual? All it does is explain how to setup a repository.  It says very little about the updates being made, shows no statistics, shows no configuration.  It's just a news article and traffic generator.  Would be better to keep people here, commenting on any issues, problems so we don't fragment the "help"/manual.

Awesome work by the developers!  Definitely a boot speed improvement on every computer I've tried: old Dell GX260 P4 1GB, Gateway 64-bit AMD Processor Laptop 2GB, Asus Eee 1000h.  All running Karmic (64-bit on the Gateway), and all working beautifully with this PPA.

---

### Post by zekopeko on 2009-11-01
> **Bordi said:**
> ..and 52 sec @ my system. Why does it take so long? :(

[-> bigger image]("http://media.ubuntuusers.de/forum/attachments/2208053/teebook-karmic-20091101-19.png")

Because bootchart doesn't record only from grub to gdm but from grub to a fully usable desktop (your disk is idle, all the stuff that Gnome needs has loaded and you can work).

---

### Post by andrewabc on 2009-11-01
> **zekopeko said:**
> Because bootchart doesn't record only from grub to gdm but from grub to a fully usable desktop (your disk is idle, all the stuff that Gnome needs has loaded and you can work).

No, it records grub->GDM-> +45 seconds extra. Which most likely includes your desktop being fully loaded and browsing the internet.

I have SSD. My extended bootchart is 51 seconds, yet my music player is playing at 25 second mark. I'm not sure what gnome is loading that takes up to 51 seconds when everything is fully loaded and CPU is idle at 12 seconds. Obviously that is because of grub->GDM (6 seconds for me) +45 second delay.

It has absolutely NOTHING to do with idle CPU or desktop fully loaded. GRUB->GDM +45 seconds.
If it takes an hour to get from GDM to desktop bootchart will only record the extra 45 seconds.

---

### Post by MacUntu on 2009-11-01
Small correction: Bootchart doesn't wait for GDM, it waits for 'rc' being stopped ([FONT="Courier New"]'[ "$UPSTART_STOP_EVENTS" = "stopped" ]'[/FONT] and [FONT="Courier New"]'stop on stopped rc'[/FONT]).

---

### Post by keybuk on 2009-11-01
> **Starks said:**
> Still a minute to a working desktop...

[http://img682.imageshack.us/img682/5813/kingfisherlucid20091031.png](http://img682.imageshack.us/img682/5813/kingfisherlucid20091031.png)

BTW, when did these new attachment resolution restrictions get put into place here?

Your boot time is largely being taken up by the Ubuntu One client :-(  I guess it's syncing on login?

---

### Post by keybuk on 2009-11-01
> **zekopeko said:**
> It takes me around 90 sec to boot to a fully working desktop :(

And that's on a platform that they use for benchmarking the boot improvements. I do have a spinning disk though.

Your chart didn't show up - it got scaled down, please feel free to e-mail it to me and I'll take a look for you

---

### Post by Starks on 2009-11-01
> **keybuk said:**
> Your boot time is largely being taken up by the Ubuntu One client :-(  I guess it's syncing on login?
I forget, is ubuntuone installed by default?

---

### Post by andrewabc on 2009-11-01
> **Starks said:**
> I forget, is ubuntuone installed by default?

Yes it is.

---

### Post by afv on 2009-11-01
Here's mine&#8230; More than 100 seconds to desktop. :|

[http://img21.imageshack.us/img21/5675/laptop01lucid200911021.png](http://img21.imageshack.us/img21/5675/laptop01lucid200911021.png)


Another startup:

[http://img4.imageshack.us/img4/2181/laptop01lucid200911023.png](http://img4.imageshack.us/img4/2181/laptop01lucid200911023.png)


Now with Kernel 2.6.32-2:

[http://img4.imageshack.us/img4/225/laptop01lucid200911024.png](http://img4.imageshack.us/img4/225/laptop01lucid200911024.png)

---

### Post by davidY on 2009-11-02
my boot is now 32 seconds wohoo!!

too bad i didn't time it before

however, i notice a very dramatic reduction in processing after the login.

---

### Post by Jay_Bee on 2009-11-02
It's working when my USB hard disk is not connected and boot takes about 45 sec but ubuntu-one keeps the bootchart running until 1:08.

With my USB disk connected, ureadahead has only a tiny line in the bootchart and the boot takes more than a minute

I can see that ureadahead created a .pack file for my USB disk. Wonder what's that for.

---

### Post by cdEWoozy on 2009-11-03
```
With sreadahead:
Grub -> GDM    : 47s
GDM  -> Desktop: 30s (probably more, bootchart stops before the desktop is fully loaded)
Total          : 1m17s

With ureadahead:
Grub -> GDM    : 28s
GDM  -> Desktop: 16s
Total          : 44s
```

On a Dell Latitude E6400 with a Core2Duo P8600 (2.4GHz) and a Toshiba MK1652GSX hdd (5400rpm). Even the delay between usplash and xsplash is significantly shorter (<1s).

Yay :)

---

### Post by Bordi on 2009-11-03
Ah yes, now it work's. **6.77** sec to desktop. :D

edit /etc/init/bootchart.conf and  'sleep 45' removed, and ureadahead installed. :popcorn:

[-> my chart]("http://media.ubuntuusers.de/forum/attachments/2212758/teebook-karmic-20091103-6.png")

Thinkpad T400 2765-52G, 4G Ram & 250G OCZ Vertex SSD. ^^

---

### Post by andrewabc on 2009-11-03
> **Bordi said:**
> Ah yes, now it work's. **6.77** sec to desktop. :D

edit /etc/init/bootchart.conf and  'sleep 45' removed, and ureadahead installed. :popcorn:

[-> my chart]("http://media.ubuntuusers.de/forum/attachments/2212758/teebook-karmic-20091103-6.png")

Thinkpad T400 2765-52G, 4G Ram & 250G OCZ Vertex SSD. ^^

Nice SSD. :O
I only got 60gb vertex.
My bootcharts are 6 or 7 seconds (with a 1.8ghz core2duo and ICH8, 3 years old).
Very nice to see this improvement everyone is having, especially for the hard drive booters.

Your laptop support SATAII?
I think some laptops only had SATAI, not sure if newer ones have SATAII (and not have it disabled to save power).

---

### Post by Bordi on 2009-11-03
Thanks. :) Yes it is SATAII supported, but it seems that karmic can't use the speed of this SDD. This SSD should have a peak reading speed of 250, but i haven't seen that yet. Always less then 200, since karmic. :(

---

### Post by andrewabc on 2009-11-03
> **Bordi said:**
> Thanks. :) Yes it is SATAII supported, but it seems that karmic can't use the speed of this SDD. This SSD should have a peak reading speed of 250, but i haven't seen that yet. Always less then 200, since karmic. :(

That's probably normal. I'm only getting 110-150mb/s

---

### Post by NCLI on 2009-11-03
> **Bordi said:**
> Thanks. :) Yes it is SATAII supported, but it seems that karmic can't use the speed of this SDD. This SSD should have a peak reading speed of 250, but i haven't seen that yet. Always less then 200, since karmic. :(

Isn't that just because while 250MB/s may be the theoretical limit, in the real world, it only reaches 200MB/s?

---

### Post by andrewabc on 2009-11-03
> **NCLI said:**
> Isn't that just because while 250MB/s may be the theoretical limit, in the real world, it only reaches 200MB/s?

Nope, they reach 250 easily. SATA II actually limits the full potential.
[http://www.anandtech.com/storage/showdoc.aspx?i=3667&p=5](http://www.anandtech.com/storage/showdoc.aspx?i=3667&p=5)

Probably has to do with loading an OS and having to load so many small files and doing lots of CPU stuff. It's not reading a single sequential 2mb file like benchmarks show.

---

### Post by Bordi on 2009-11-04
I don't think so, because it was faster with Jaunty. In this last cahrt of Jaunty, the speed goes up to 221. However the fastest Speed what i ever in one of my charts have seen, was a small piece over 300.  :|

[->> Jaunty Boorchart]("http://ubuntu-pics.de/bild/29700/teebook_jaunty_20091022_4_mN3ei4.png")

Edit: Oh yes i forgot. Once in Virtalbox, the speed was going up to 317. ^^

[->> 317MB/s]("http://ubuntu-pics.de/bild/29702/ubuntu_karmic_20091020_3_AR8u7Q.png")

---

### Post by cow_racer on 2009-11-08
My Thinkpad X61 supports SATA II but it's speed is of SATA I.

---

