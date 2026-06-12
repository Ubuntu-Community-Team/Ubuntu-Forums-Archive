---
title: "Boot time with Jaunty"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-01-12
A faster boot time is one of the goals for Jaunty [[1]](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-September/000481.html), so I'm curious how fast your Jaunty boots compared to Intrepid are. In my case, Jaunty boots a lot faster on all my machines. 

Here are two bootcharts [[2]](http://www.bootchart.org/) for my notebook (T2400 1.83GHz Core Duo, 2GB RAM, 80GB 5400rpm hard disk):

[[img]http://img.xrmb2.net/images/281522.png[/img]](http://img.xrmb2.net/images/607408.png) (overlay) [[img]http://img.xrmb2.net/images/326075.png[/img]](http://img.xrmb2.net/images/670420.png) (side by side)

20 vs. 28 seconds - 28,6% faster - stunning! :)

---

### Post by Mazza558 on 2009-01-12
With Ext4, the boot time will be even shorter.

---

### Post by MacUntu on 2009-01-12
> **Mazza558 said:**
> With Ext4, the boot time will be even shorter.

Tested that yesterday, no difference.

---

### Post by andrewabc on 2009-01-12
Both boot times were on a fresh install?

---

### Post by MacUntu on 2009-01-12
In the EXT4 vs. EXT3 test, yes. Partitions were 50GB, maybe the speedup comes with higher capacities? Time to test on a different machine. :)

---

### Post by ShirishAg75 on 2009-01-12
MacUntu, 
 just a comment/addition to your signature. 

It would be right if you rewrote it to say 

"Software development and testing are extreme forms of masochism"

as much as software developers, testers also love pain (in some sense).

---

### Post by autocrosser on 2009-01-12
> **ShirishAg75 said:**
> MacUntu, 
 just a comment/addition to your signature. 

It would be right if you rewrote it to say 

"Software development and testing are extreme forms of masochism"

as much as software developers, testers also love pain (in some sense).

!!!!!!:lolflag:!!!!!!

Agreed!

---

### Post by plun on 2009-01-12
> **ShirishAg75 said:**
> 
[B]
"Software development and testing are extreme forms of masochism"[/B]

as much as software developers, testers also love pain (in some sense).

No...:lolflag:

Reflashed my totally broken PC and installed Intrepid.  
(Jauntys CDs are just a mess...)

But...  upgrade-manager -d directly...:guitar:


(maybe I have broken memory modules....)

---

### Post by MacUntu on 2009-01-12
Freaks! :lolflag:

> **MacUntu said:**
> Time to test on a different machine.
Done - no difference between EXT4 and EXT3 but I'm still impressed by the boot time decrease. :)

---

### Post by fut21 on 2009-01-18
Jaunty is a fast booter, but networkmaneger 0.7.0 are very slow in starting up after the desktop appears.

---

### Post by MacUntu on 2009-01-18
Yeah, I noticed that too. In the Intrepid bootchart you can see NM starting about 9.5 seconds after the WLAN init, in the Jaunty bootchart it's 4.5 seconds. Best guess: the device is not ready when you see the desktop - Windows, anyone? :twisted:

---

### Post by ShirishAg75 on 2009-01-18
This is my bootchart.

Just for people. If you want to use bootchart to find out. Its pretty simple, 

Just install bootchart using your favorite package-manager (synaptic, apt-get, aptitude, Add/Remove Programs) whatever and then reboot. 

You will find another the .png files at /var/log/bootchart/

One thing more though, I had optimized my boot process a bit during Intrepid. Couple of things were left through.

---

### Post by vishalrao on 2009-01-18
that should be /var/log/bootchart

see this thread for how to enable/disable it as well: [http://ubuntuforums.org/showthread.php?t=868189](http://ubuntuforums.org/showthread.php?t=868189)

---

### Post by cl333r on 2009-01-18
> **MacUntu said:**
> Tested that yesterday, no difference.

The difference comes up after a large period of time, since ext4 keeps the integrity of the files better than ext3. The less parts a file is composed of, the faster it is read.

---

### Post by salsafyren on 2009-01-18
So what has exactly happened from intrepid to jaunty to make it boot faster?

[https://blueprints.launchpad.net/ubuntu/+spec/jaunty-boot-performance](https://blueprints.launchpad.net/ubuntu/+spec/jaunty-boot-performance)

the above page states the spec has not been started so I guess the decrease in boot time has happened by coincidence.

---

### Post by Trevice on 2009-01-18
it will be interesting when developments include the version 0.5 of upstart (I wish they to it finally in this version). Then all the boot process will be control using "events" instead of the traditional scripts. 
Anyone knows if they update upstart soon? or an aprox date??

thanksss

---

### Post by UbuWu on 2009-01-19
> **salsafyren said:**
> so I guess the decrease in boot time has happened by coincidence.

No, quite some effort has already gone into reducing the boot time. Several kernel modules are now built into the kernel and some more changes have happened. Some information can be found here: [https://lists.launchpad.net/ubuntu-boot/](https://lists.launchpad.net/ubuntu-boot/)

---

### Post by inportb on 2009-01-19
Interesting read...

In any case, I'm liking the performance gains. I too have experienced at least a 25% reduction in boot time.

---

### Post by Podex on 2009-01-19
> **Trevice said:**
> it will be interesting when developments include the version 0.5 of upstart (I wish they to it finally in this version). Then all the boot process will be control using "events" instead of the traditional scripts. 
Anyone knows if they update upstart soon? or an aprox date??

thanksss

Yes, I'm quite curious about this too. They made a lot of fuss about Upstart when it first came to Ubuntu, but since then I haven't heard anything about it. Nothing about it in the Jaunty blueprints either...

---

### Post by MacUntu on 2009-01-20
When looking at bootcharts like this I'm wondering if there is enough potential for upstart to improve boot time. Mostly I/O-Wait:
[[img]http://img.xrmb2.net/images/833887.png[/img]](http://img.xrmb2.net/images/463580.png)

[Opteron 144, 640GB WD Caviar Blue, 2GB DDR-RAM, most modules built-in - saves only one second compared to the generic kernel!]

---

### Post by jmmL on 2009-01-20
MacUntu, how did you get such a fast boot?

Apart from building in modules, what else have you done?

13 seconds is so fast! I'm currently thinking of switching over to jaunty sometime in the next month - i used to have about 30 second boots, but i now have more like 34s with virtualbox installed.

Also, can anyone report any improvements on gnome log-in time? Currently (in intrepid) it takes about a minute once the system has actually booted, which I think is far too long. The process isn't particularly disk-intensive as the hard disk light only comes on and off occasionally when logging-in. Hopefully this improves in Jaunty - because to most users the time to "boot" will include log-in time as well.

---

### Post by MacUntu on 2009-01-20
The custom kernel only saved one second. With the generic kernel I get 14 seconds GRUB -> GDM without doing anything. :)

And I agree, the time GRUB -> usable desktop should be of main interest and not GRUB -> GDM. It's just easier to compare I guess.

---

### Post by damis648 on 2009-01-20
Compiz is typically what holds back GDM->Desktop. Try turning it off, see if you see a difference. But I think you are right, we need to decrease that time. Hopefully once they get GNOME 3 out we can have an OS X speed login.

---

### Post by ShirishAg75 on 2009-01-20
> **Trevice said:**
> it will be interesting when developments include the version 0.5 of upstart (I wish they to it finally in this version). Then all the boot process will be control using "events" instead of the traditional scripts. 
Anyone knows if they update upstart soon? or an aprox date??

thanksss

Trevice, 
       I know of a developer (I don't remember his name off-hand (most probably John Dong though) who tried to give momentum to upstart in ubuntu, you can find some of his posts in the archive talking about upstart but nothing much came of it. 

Now that Fedora is using upstart, its possible that sometime in the future ubuntu may make the changeover to upstart, when that happens is anybody's guess. 

The problem (as I read it) there are just too many variables and not enough testing or people who are comfortable with testing upstart as being part of the boot process. 

Also don't know if it would be something which would be done within a single release or something which would also take multiple releases (as the pulseaudio experience as shown) , 

I, for instance would love to try it but need all the info. beforehand and printed as breakage (as anything else in software development) is very much possible/probable and when and if breakage happens I need a way to get back. 

I guess its more or less a momentum issue (both of users and developers) rather than anything else. 

all, sorry for the long post. 

Update :- Also upstart seems to be slow in uptake and stuff. Its at 0.5 atm although in jaunty its held at 0.3.9.8 which I guess is obsolete. 

[https://launchpad.net/ubuntu/+source/upstart](https://launchpad.net/ubuntu/+source/upstart)

Comments, suggestions welcome .

---

### Post by fut21 on 2009-01-22
Boottimes are going the wrong way. After the latest updates jaunty are a very slow booter.

---

### Post by Tich666 on 2009-01-22
18 seconds with the 2.6.28-5 kernel and ext4, not too bad. :D
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100756&d=1232675311[/IMG]

---

### Post by scottmuz on 2009-03-07
I upgraded to jaunty and upgraded to ext4.

My boot times with bootchart have increased from 28 (under intrepid) to 31 with jaunty.

I've put concurrency=shell but it is still more than interpid.

I'm a bit disappointed. 

Once I'm logged in though gnome feels more responsive.

---

### Post by iaskedalice09 on 2009-03-07
How does one change from ext3 to ext4? Thx.

---

### Post by phpadik on 2009-03-07
> **vishalrao said:**
> that should be /var/log/bootchart

see this thread for how to enable/disable it as well: [http://ubuntuforums.org/showthread.php?t=868189](http://ubuntuforums.org/showthread.php?t=868189)

It's annoying. My bootchart doesn't generate charts on /var/log/bootchart. Do you still need to enable it after installing thru apt?

---

### Post by terry_gardener on 2009-03-07
here is mine 23 secs

---

### Post by iaskedalice09 on 2009-03-07
Here's mine, 34 seconds. I'd love to get it in the teens so if anyone knows how to build a custom kernel for idiots, any instruction would be helpful.

Thx!

---

### Post by Jay_Bee on 2009-03-07
My grub->gdm time is 30 seconds, I think it's ok.

---

### Post by t-mo_ on 2009-03-07
I am so jealous of your bootcharts.. Can somebody give me a hint why my machine boots so slow (compared to yours)?

thanks

---

### Post by gjoellee on 2009-03-07
My Ubuntu boot in 21 sec, but Arch boots in 15 (and it even connects to Internet on startup). Ubuntu can still improve!

TIP: Remove unnecessary modules to load on startup.

---

### Post by gjoellee on 2009-03-07
My Ubuntu boot in 21 sec, but Arch boots in 15 (and it even connects to Internet on startup).

The point is that Ubuntu can still improve it's boot time!

EDIT: Somehow my first edit became a second post :S

---

### Post by andrewabc on 2009-03-07
> **iaskedalice09 said:**
> How does one change from ext3 to ext4? Thx.

step 1: Go to google.com
step 2: type in: convert ext3 to ext4
step 3: profit

---

### Post by Darkshade on 2009-03-07
24 seconds here. It might not be that fast but I'm pretty happy with it, considering that I only restart my computer when a new update requires it and I never turn it off to have to turn it on again.

---

### Post by avb on 2009-03-09
just a few notes to speedup start. 

1. Jaunty has a lot of modules compiled in kernel. Mine intel laptop can boot with a stock jaunty kernel without initrd at all. Try if it works with yours. 

2. Avahi daemon. If u dont need your laptop being discoverable via network, feel free to remove avahi-daemon package. Avahi-daemon is in Recommends of ubuntu-desktop package so ubuntu-desktop metapackage will stay in place.

3. Cups. If u do not using printing on your laptop, disable startup of cups daemon. And system-config-printer fronted in gnome session.

4. Bluetooth. If u not using bluetooth, disable bluetooth daemon and its frontend. 

5. Examine 'Startup applications' list and disable onces that u never using. I disabled practically everything. 

I was not bootcharting mine system, but so far im getting gdm in around 8-10 secs + im getting usable gnome desktop with metacity in around 5-6 seconds.

---

### Post by Starks on 2009-03-09
Jeez. Why isn't there an upstart ppa...

I want the latest and greatest in boot procedure!

---

### Post by avb on 2009-03-09
ok. i reboot my lappy with a countdown timer and it showed me 22 secs to gdm and 8 to desktop :) Far from 10 secs, but still doesnt seems that long to wait.

---

### Post by IanW on 2009-03-09
Today I managed to reduce the bootup time of my Eee by a full 3 minutes!:D




How?




I removed the corrupt SD card which was causing a timeout.](*,)

---

### Post by Starks on 2009-03-09
3 minutes to boot?

That must've to sucked.

Glad that you fixed it and are now able to show off your eeepeen.

---

### Post by scottmuz on 2009-03-13
After I first upgraded from interpid my boottime increased but since the latest kernel update it has come down to 25 seconds (from 28 under interpid). Not bad.

---

### Post by taavikko on 2009-03-14
Quite fast in here...

---

### Post by MacUntu on 2009-03-14
> **taavikko said:**
> Quite fast in here...

Poor i7... got nothing to do. Time for a SSD? ;)

---

### Post by plun on 2009-03-14
Its fast.....:D

---------------

Phoronix wrote an article about X delays compared with Moblin and Jaunty

[http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw](http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw)

Ubuntu/Canonicals Scott James Remnant is trying to find out why...

---

### Post by taavikko on 2009-03-14
> **MacUntu said:**
> Poor i7... got nothing to do. Time for a SSD? ;)

Yeah, poorest of the poor, but the better one's had a price tag made of pure gold.

Pretty much like good SSD drives have... :(

Let's just wait that the world economy swirls more in the bottomless pit that it is in already :D

---

### Post by MacUntu on 2009-03-14
What I don't understand: Why does it take 0.7 seconds to probe an SATA port? I have four SATA ports, two in use and the other two connected to an e-SATA bracket:

```
[    0.929613] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 10
[    0.929665] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 10
[    1.652029] ata1: SATA link down (SStatus 0 SControl 300)
[    2.376026] ata2: SATA link down (SStatus 0 SControl 300)
...
[    2.376715] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 11
[    2.376766] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 11
[    3.256033] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
...
[    3.326899] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    4.204032] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
```

That's 0.72 + 0.72 + 0.88 + 0.88 = 3.2 seconds for those four ports.

---

### Post by adampope on 2009-03-21
Chance would be a fine thing! I did a reinstall to get ext4, but Janunty now takes over 3 minutes to boot - chart:

 [IMG]http://farm4.static.flickr.com/3443/3372429003_c1ab320b02_b.jpg[/IMG]

Likely culprits in there are:

modprobe
udevd
udevadm
s10udev
rc

All of which are gibberish to me. Any help to fix this much appreciated!

Running Acer Aspire 5510, ATI video card, Intel 1.73GHz processor, 495MB memory

---

### Post by IanW on 2009-03-21
> **adampope said:**
> Chance would be a fine thing! I did a reinstall to get ext4, but Janunty now takes over 3 minutes to boot - chart:

 [IMG]http://farm4.static.flickr.com/3443/3372429003_c1ab320b02_b.jpg[/IMG]

Likely culprits in there are:

modprobe
udevd
udevadm
s10udev
rc

All of which are gibberish to me. Any help to fix this much appreciated!

Running Acer Aspire 5510, ATI video card, Intel 1.73GHz processor, 495MB memory

This happened to me with an Asus EeePC 701 - It turned out to be a corrupted SD card in the reader slot, which meant the boot process was waiting for a timeout

---

### Post by adampope on 2009-03-21
Thanks Ian! I'd read your reply there. Unfortunately, without having anything in my SD card slot, this fix won't help me.

---

### Post by MacUntu on 2009-03-23
T2400 Core Duo, 2GB DDR2 RAM, 7200rpm SATA II HDD, EXT4: **GRUB -> desktop in 20 seconds***.

[http://img.xrmb2.net/images/600075.png](http://img.xrmb2.net/images/600075.png)

Jaunty's boot time mission successfully accomplished.

*) I optimized the readahead list by running "profile", copying all the files from the new readahead list to a tar file, rebooted with a live CD, extracted (overwrote) all the files from the tar, and finally sorted the file list by block numbers (this made the disk throughput go up). I did the same thing to the session readahead list (which I've created according to this how-to: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)). Some work but saved about seven seconds of boot time (27 seconds is still great). :)

---

### Post by shafin on 2009-03-23
Jaunty sure has some tricks down its sleeve, in Intrepid, my boot time was around the 29 sec mark, now its around 24 in Jaunty.

---

### Post by grantek on 2009-03-25
> **MacUntu said:**
> copying all the files from the new readahead list to a tar file, rebooted with a live CD, extracted (overwrote) all the files from the tar
What was your logic behind that? I'd have thought overwriting a file would put the new contents in exactly the same list of blocks as the original, especially if the entire operation happens before a sync to disk.

---

### Post by Hairy_Palms on 2009-03-25
just installed jaunty, id spent some time optimising my intrepids boot process too, yet still it went from 24s in intrepid to 17s in jaunty, nice,

---

### Post by n3had on 2009-03-25
My system is really slow after gdm infact around 25 secs lag

Here's the bootchart

---

### Post by MacUntu on 2009-03-25
> **grantek said:**
> What was your logic behind that? I'd have thought overwriting a file would put the new contents in exactly the same list of blocks as the original, especially if the entire operation happens before a sync to disk.

Do
```

sudo filefrag -v somefile
cp somefile somefile2
sudo filefrag -v somefile2
mv somefile2 somefile
sudo filefrag -v somefile

```
and compare the block information. I guess that's what happens while extracting the tar. The files extracted from the tar are definitely read faster than before.

---

### Post by happyhamster on 2009-03-29
Just did some tests, and was surprised how big the difference is in boottimes. On a clean and default install (32 bits, only a root-partition + swap): 

Intrepid (ext3): 25.0 sec.
Jaunty   (ext3): 17.5 sec.

And times were even shorter when using ext4:

Jaunty (ext4): 13.7 sec.
Jaunty (ext4, 64 bits): 14.0 sec.

And when using separate / and /home partitions:

Jaunty (/=ext3, /home=ext4): 14.5 sec.
Jaunty (/=ext4, /home=ext3): 13.8 sec.

Those results were from a regular sata drive (Hitachi deskstar 160GB). When using an ssd (OCZ Vertex) boottimes went down to:

Jaunty (ext3, ssd):  9.9 sec.
Jaunty (ext4, ssd): 10.1 sec.

(The picture that bootchart outputs gets too narrow to print all the text :))

---

### Post by philinux on 2009-03-29
On 64 bit clean beta install EXT3.

Grub to Login 24.5 seconds.
Login to Desktop 16 seconds.
Total 40.5 


On intrepid it used to be 29 and 29.
Total 58

---

### Post by ssdt on 2009-04-17
It's going to be faster in the next versions to come too if this is that fast.

---

### Post by xl_cheese on 2009-04-17
Who really cares how fast the boot time is???  I rarely reboot my computer.  Even then, who cares about 5 seconds?

To me it seems like there are bigger fish to fry than to worry about boot time.  How 'bout the audio mess?  

Why spend the resources trying to save someone 5 seconds of boot time when they could be working on bugs that cost the user hours to fix?

---

### Post by scaine on 2009-04-17
Anyone who uses a laptop will care.  If boot time can get down to suspend/resume times, everyone will care.  Hell, the environment will care.

---

### Post by MacUntu on 2009-04-17
> **xl_cheese said:**
> I rarely reboot my computer.

So?

---

### Post by ssdt on 2009-04-18
It's only you. For me, it takes less electricity and the "Go Green" will come out to be better. So why not keep it green by using less enery?

---

### Post by SeanBlader on 2009-04-19
My system out of the box with Jaunty comes up with 12 second boot time, and then after a few changed settings, dropped it another second according to the attached bootchart. Looking at processor and IO times, it looks like that could be decreased even more if you knew the best way to sequence things to get those gaps out of there.

Goes to show that a fast processor isn't the panacea that Intel and AMD would have us believe. I get decent performance with a 1.4 Ghz processor, but I would guess that the SSD is a bit more helpful.

My boot partition is Ext2 and then / and /home are both Ext4.

---

