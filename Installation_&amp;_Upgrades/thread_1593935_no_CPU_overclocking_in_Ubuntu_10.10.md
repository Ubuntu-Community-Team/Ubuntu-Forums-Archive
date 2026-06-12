---
title: "no CPU overclocking in Ubuntu 10.10???"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by CTAPbIi on 2010-10-11
Yesterday it took me some time to find out the reason why I can not install Ubuntu 10.10. I downloaded amd64 iso from cdimage.ubuntu.com w/o any errors, checked it's intergrity using flush 0.9.8 and Transmittion 2.0.4 and on top of that I checked any & each letter in md5sum. Trust me, the image is OK. I did this "procedure" twice saving on different HDDs.

I thought smth wrong with DVD-writer. I can not make Ubuntu 10.10 been installed on my rig nor via live-DVD mode, nor just install. And on top of that I can not even check disk integrity (that's weird). I wrote down 3 different disks (DVD -R & +R by different brands and on one my 100% trustful DVD -RW disk. Just no. But in the same time I can install Ubuntu 10.04 flawlessly. I downloaded Ubuntu 10.04 and still NP to install. So my DVD-drive's "writing ability" is OK also.

The only way to install Ubuntu 10.10 is to take away my CPU overclocking in BIOS. After that - NP at all. But when I bringing back my OCing, I can not load Ubuntu 10.10 with the same [http://savepic.org/779842.jpg]("http://[URL")]error message [/url] as I got when I tried to install from DVD-disk. When I'm disabling Hyper-Threading, i'm getting [http://savepic.org/728665.jpg]("http://[URL")this message[/url]. 

From one hand, I might live happily w/o CPU OCing, but my rig is in distributed calculations (BOINC platform), so I really need that. I tried to google but looks no1 else facing this except me.

My hardware:
CPU: i7-920 OCed @4011 (191*21 @1.325V)
mobo: Asus P6T6 WS Revolution
RAM: Mushkin DD3-1600 (basically stock clocks)

Do not get me wrong: I'm **NOT** trying throlling and I'm **NOT** "holy war" maker. In fact, Ubuntu is my main (and on 99% - the only) operating system since 7.04 release. All I need to know is - "What should I do now?"

P.S. Sorry for pretty tough message :)

---

### Post by CTAPbIi on 2010-10-12
any ideas? or I'm really the only one facing this problem?

---

### Post by paulisdead on 2010-10-12
Looks like your overclock is not stable and you need to do more tweaking if you want to keep it.  I didn't clean install, but my core2 9550 runs fine with a 1ghz overclock on it in 10.10.

You might want to try adjusting voltages one at a time, just a bit, and try testing again after the change.  Typically you can adjust the CPU, memory, and northbridge voltages, some boards give you other options such as the front side bus, pci-e bus, etc, that you can try.

If you're using that turbo boost stuff the i7s have on them, it might be that one core can't handle being ramped up even higher when the other cores are idle.  You might try bumping the CPU speed down just a bit, as well.  You could just be running a little too fast for 100% stability, although it's stable during most operations.

Also none of your image links work.

---

### Post by CTAPbIi on 2010-10-12
My OC is solid rock stable over a year from now - both on Ububntu 9.10 & 10.04 as well as on [offtopic]. Even now it works just fine on ubuntu 10.04, so I believe the problem is in Ubuntu 10.10 itself. I'll try to play with BIOS around today. 
 
That's weird, pics were on there a day ago. I'll reupload it somewhere else. Thanks :-)

---

### Post by mbgaski on 2010-10-12
> **CTAPbIi said:**
> My OC is solid rock stable over a year from now - both on Ububntu 9.10 & 10.04 as well as on [offtopic]. Even now it works just fine on ubuntu 10.04, so I believe the problem is in Ubuntu 10.10 itself. I'll try to play with BIOS around today. 
 
That's weird, pics were on there a day ago. I'll reupload it somewhere else. Thanks :-)

Hate to sound a little harsh, but no, your OC isn't stable.  A lot of times errors produced by an overclock might not be immediately obvious.  If a specific instruction tends to goof up on OC for example, and the software you've been using doesn't call that, then you'd never notice it.  However, when you eventually switch to a software program that DOES use that feature, you'll get crashes, as you are now experiencing.

It's like claiming everything in your car works fine when in reality you never use the air conditioner because you live in Alaska.  Moving to Arizona didn't break your AC - you just didn't notice it before.

Reduce the OC or just run stock speeds - which is my suggestion anyways.  In my late teens overclocking was an interesting and fun way to "squeeze out more performance".  As I've gotten older (and admittedly have more money to spend on upgrades when needed), it's just more of a headache than it could ever be worth.

---

### Post by CTAPbIi on 2010-10-12
> **mbgaski said:**
> Hate to sound a little harsh, but no, your OC isn't stable. A lot of times errors produced by an overclock might not be immediately obvious. If a specific instruction tends to goof up on OC for example, and the software you've been using doesn't call that, then you'd never notice it. However, when you eventually switch to a software program that DOES use that feature, you'll get crashes, as you are now experiencing.
 
It's like claiming everything in your car works fine when in reality you never use the air conditioner because you live in Alaska. Moving to Arizona didn't break your AC - you just didn't notice it before.
 
Reduce the OC or just run stock speeds - which is my suggestion anyways. In my late teens overclocking was an interesting and fun way to "squeeze out more performance". As I've gotten older (and admittedly have more money to spend on upgrades when needed), it's just more of a headache than it could ever be worth.
 
That's good example with AC in Alaska :-) I'll play today with BIOS and OCing. In fact, I tried Yday 3780 (180*21) clock - same result, but again - I'll try.
 
I'm pretty sure that my OC is stable. It been checked tens times by various software like prime95, Lynx, SM, OCCT and over a year in distributed calculations (which is the most tough for hardware). It just works. But again - I'll play around 2day. And - I really need OCing :-)

---

### Post by paulisdead on 2010-10-12
You could also look into a bios update.  Though with overclocking, I've found it best to clear the cmos after a bios update, and redo all the settings in the bios after the update.

Have you tinkered with the voltages at all?

---

### Post by 98cwitr on 2010-10-12
i just tried to put my e6750 back @ 3.6 and it crapped out on me...wtf

EDIT: crapped out @ 3.5, stable @ 3.4 and w/ the memory @ 1022MHz...what gives? I've pulled 3.73 out of it before on 9.10

---

### Post by CTAPbIi on 2010-10-13
[FONT=Verdana][**mbgaski**]("http://ubuntuforums.org/member.php?u=759132") [/FONT]
 
[FONT=Verdana]You know what? I&#8217;m really shocked&#8230; [/FONT][SIZE=2]Last night I tried to play with OC. There is nothing to do with RAM, very low clocks (DDR3-10xx), high timings (10-10-10-31) and voltage (even 1.76V) did not help. The only way to install 10.10 was to reduce BCLK from 191 to 185. But even after that were some instability, so I came to 183 and lost over 4% in speed. That&#8217;s not good at all&#8230;[/SIZE]
 
[SIZE=2]That&#8217;s really weird&#8230; Yday I checked my rig stability on windows7 using prime95 and LynX. Trust me, solid rock stable on BCLK 191 for over two hours. And on top of that I can install 10.04 w/o any problem. In my understanding the guys messed up (or f.cked-up &#8211; depends on what u r thinking about this :-) ) smth in 35th kernel. I forgot to check OC on 32th kernel in 10.10, may it&#8217;s OK there.[/SIZE]
 
[SIZE=2]I was really battling with nvidia proprietary driver installation. I do need specific combination of the driver (195.30) and cudatoolkit (2.3) for maximum speed. Even after blacklisting of 5 free drivers I still got desktop after reboot. I tried to find what else I have to blacklist, but vesa & mesa did not help. I even deleted in synaptic all nv, nvidia, nouveau, xserver and other stuff &#8211; no luck.[/SIZE]
 
[SIZE=2]Me personally do not like new menus: items are very close to each other. I&#8217;ve got 24&#8221; screen so I do not need this &#8220;space saving&#8221;, ha-ha. And also I do not like orange menu&#8217;s highlighting &#8211; it&#8217;s way too bright in my mind. [/SIZE]
 
[SIZE=2]And in general &#8211; 10.10 is less stable (or more buggy) then 10.04. For example, why I have to start update-manager as root in console rather then do this from menu? Why update-manager crushed twice during update? lm-sensors are not working well for me, temperature readings are wrong. I do believe that I can fix it somehow, but why I should do this if it works just fine in 10.04?[/SIZE]
 
[SIZE=2]So, for the first time since 7.04 I&#8217;m staying on older release. Hopefully 11.04 will be better in terms of stability and OC.[/SIZE]
 
[FONT=Verdana][**paulisdead**]("http://ubuntuforums.org/member.php?u=234498")[/FONT]
[FONT=Verdana]the very latest BIOS for Asus P6T6 WS Revolution rev. 1.x is 0507 and it&#8217;s already there. All newer are for 2.x revision. I&#8217;m not sure what&#8217;s the difference between revisions, but I do not think that it&#8217;s a good idea to flash smth newer I&#8217;ve got right now :-)[/FONT]
 
[FONT=Verdana][**98cwitr**]("http://ubuntuforums.org/member.php?u=863250")[/FONT]
[FONT=Verdana]I&#8217;m not alone any more? Welcome to the club bro :-)[/FONT]

---

### Post by paulisdead on 2010-10-14
Ya, that's likely hardware rev2 of the motherboard, so you don't want to flash that to an older board.

It could be something in the newer kernels writes in some specific memory pattern that's different than previous versions that worked OK.  Or maybe some specific instruction getting run on a core when it's ramped up.  I'm not at all sure these are what the problem is, just offering possible explanations as to why this would be a problem after the update.

Linux has always been less kind to overclockers than windows.  It just tends to utilize the resources more, but give them back up when they're needed.  I do all my testing of my overclocks in Linux for this reason, since it should expose instabilities I might not see in windows, or find them faster.

As for lm_sensors being off, the modules for your motherboard might've changed in the newer kernel, and there maybe different ones you need to load for your board in the newer release.  This happened at one point with my asus p5q-e after an upgrade.  Try backing up your sensors.conf file and re-run sensors-detect.

If you need that specific of an nvidia driver set, I'd probably just do it by hand with the driver downloaded from their site archives.  You just have to pay attention to kernel upgrades, since you'll need to reinstall the driver after each upgrade.

I upgraded my 3 ubuntu machines, all with really different hardware to 10.10.  It's been solid on each of them.  Only my desktop is overclocked, but they've all been running smoothely with 10.10.  It's been one of the smoothest upgrades for me.  

I did have a couple sticks of Crucial DDR2 1066, that over time stopped being able to run stable at 1066 but ran fine at 800.  For some reason they started getting extremely hot at that speed, whereas they had run great when I first got them.  Perhaps something similar is going on.

---

### Post by CTAPbIi on 2010-10-15
what u r using for stability testing in linux? i saw smth like cputest in synaptic and also I heard about linux version of prime95.
 
I remember that story. especially on my older p5q pro :-) I recomplied 3.1.2 version and it was just fine.
 
nvidia driver. Well, in fact I can use 185ish driver for repos together with cuda 2.2, but iprefer 195ish driver with cuda 2.3, it just faster. I could not install 195.30 on 10.10 ...
 
RAM is not an isuue, I'm pretty sure. I tried even extremely ly clock and high timings and voltage - just FO. 
 
Anyway, thanks guys for you help, it was really usefull for me :-)

---

### Post by paulisdead on 2010-10-15
4 instances of Prime95 is a good test, one instance for each core.  The phoronix test suite is in the ubuntu repos, and stresscpu2 from it has been a pretty good test.  There are some other disk based tests I've used from it as well when I've tested RAID cards.  They've got unigine benchmarks built in too.  The sheer number of tests in the suite is just crazy.

Handbrake has also been a great real world stress test, since it's one of the few things I do in normal usage that can keep all 4 cores fully loaded for any amount of time.

Back in the day, I used to run a few huge compiles, like build the kernel and xorg source code.  Those aren't as good tests anymore, since they generally can't keep a quad core chip fully loaded for long.

---

