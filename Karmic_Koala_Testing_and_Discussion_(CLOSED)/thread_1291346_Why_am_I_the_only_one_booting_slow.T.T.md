---
title: "Why am I the only one booting slow.T.T"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-10-14
I see everyone cheering for fast boots, but on my laptop, the boot process actually takes about 2 mins.(from grub2 to full desktop).
I have attached my bootchar, can anyone tell me what is wrong?
i used bum to take some useless boot procs off(useless to me).
more description: i am using ext4, been using alpha since alpha 1, no reinstalls, using grub2.

btw:the boot chart was not the most recent, but the "environment" is the same, and boot time is the same.

---

### Post by MadMan2k on 2009-10-14
its not only you - my boot time went up with karmic as well. I guess it is because they replaced readahead with sreadahead.

---

### Post by Vanishing on 2009-10-14
> **MadMan2k said:**
> its not only you - my boot time went up with karmic as well. I guess it is because they replaced readahead with sreadahead.

to be honest..my jaunty boot time isnt that slick either..
maybe its finally time for an reinstall?hope not..

---

### Post by xir_ on 2009-10-14
i've got the same. 65 seconds

---

### Post by thecow on 2009-10-14
I'm not sure how to make one of those bootcharts, however Karmic is noticeably slower on boot than Jaunty was for me

---

### Post by mad0master on 2009-10-14
Confirm -- same here! :confused:
After distro upgrade to karmic -- it is a disaster after 9.04 (was really happy about that)!

Have not measured the boot times on the 9.04, but it is like 2-3 times slower.

Please advice! With slow wlan karmic is rather disappointing for a returning ubuntu user...

---

### Post by Vanishing on 2009-10-14
5 ppl read this thread and 4 replies they have the same issue..
hmmm.guess im not the only one booting slow..
but what could be wrong?:confused:

---

### Post by john_navarro on 2009-10-14
Perhaps it's related to [open bug]("https://bugs.launchpad.net/ubuntu/karmic/+bugs?field.milestone=12698") "performs poorly on slow HDD"

---

### Post by buzzmandt on 2009-10-14
I'm there too, long time to grub, long time grub to login, long time long in to de loaded.  but once it's loaded it's very snappy and nice, so i use suspend to ram alot

---

### Post by kansasnoob on 2009-10-14
I've been playing around going back and forth from legacy grub and grub2, but by boot times from the time the grub menu shows and I hit enter to desktop aren't bad in either.

It's about 19.8 seconds using legacy grub and 25.2 seconds using grub2. I was able to shave off some time by going to Sys > Admin > Login Screen (I'd selected to "auto-login" during install) and unticking the "Allow xx seconds for others to login" thingy.

---

### Post by novafluxx on 2009-10-14
Seems a tad slower for me as well. I too might want to blame sreadahead, but I'm not sure.

If you can tell me HOW to create one of those charts, I'll do it and post it!

---

### Post by buzzmandt on 2009-10-14
i installed bootchart, then ran boot chart, it said making png but i dont know where it is.
> buzzmandt@buzzmandt-laptop:~$ bootchart
Parsing /var/log/bootchart
Oct 14, 2009 10:49:46 PM org.bootchart.Main render
WARNING: Unknown log file: buzzmandt-laptop-karmic-20091010-1.png
Oct 14, 2009 10:49:46 PM org.bootchart.Main render
WARNING: No process samples
Wrote image: ./bootchart.png

wrote image: ./bootchart.png, ok, where?

---

### Post by novafluxx on 2009-10-14
> **buzzmandt said:**
> i installed bootchart, then ran boot chart, it said making png but i dont know where it is.

wrote image: ./bootchart.png, ok, where?

I can't get it to run...got an error!

---

### Post by crjackson on 2009-10-14
I just wanted to chime in and join the club.  The alpha versions booted faster than Jaunty for me, the beta version boots slower.

It was disappointeding that this new faster booting version of Ubuntu is actually slower for me.

This doesn't seem to have anything to do with my slow Raptor 10,000 rpm drives...

I get the same result on multiple systems.

---

### Post by Nesaskewatch on 2009-10-14
> **buzzmandt said:**
> i installed bootchart, then ran boot chart, it said making png but i dont know where it is.

wrote image: ./bootchart.png, ok, where?



Behold!

buzzmandt@buzzmandt-laptop:~$ bootchart
Parsing "/var/log/bootchart"

Right there.

---

### Post by novafluxx on 2009-10-14
> **crjackson said:**
> I just wanted to chime in and join the club.  The alpha versions booted faster than Jaunty for me, the beta version boots slower.

It was disappointeding that this new faster booting version of Ubuntu is actually slower for me.

This doesn't seem to have anything to do with my slow Raptor 10,000 rpm drives...

I get the same result on multiple systems.

I believe the boot process for Karmic is supposed to be streamlined and not necessarily faster. I think the faster boot up is for 10.04.:confused::confused:

---

### Post by kansasnoob on 2009-10-15
Well, someone experiencing the problem needs to file a bug report.

It would do no good for me to do so because my boot times are great.

Now, I'm not sure what package to file it against so I'll try to draw some attention to the issue.

---

### Post by kestal on 2009-10-15
On my desktop, boot is in 10-15 seconds which is nice. However a brand new laptop (2.2ghz dualcore/3gb ddr3/nvidia 9400m-g/decent HDD/etc) takes over 50 seconds.

---

### Post by jocko on 2009-10-15
> **buzzmandt said:**
> i installed bootchart, then ran boot chart, it said making png but i dont know where it is.

wrote image: ./bootchart.png, ok, where?

> **novafluxx said:**
> I can't get it to run...got an error!

> **Nesaskewatch said:**
> Behold!

buzzmandt@buzzmandt-laptop:~$ bootchart
Parsing "/var/log/bootchart"

Right there.
There's no point trying to run bootchart on an already booted system. It's run automatically during boot. Once it's installed, just reboot and then find the chart in /var/log/bootchart.

---

### Post by cicoandcico on 2009-10-15
In my system (Dell D830), boot takes about 1:20m. With jaunty, it took about 1:00.

I remember people saying that the last improvements were supposed to come between beta and RC, but at this point I have some doubts it will happen...

However, that's not much we can do but waiting. :)

---

### Post by taavikko on 2009-10-15
> **Vanishing said:**
> I see everyone cheering for fast boots, but on my laptop, the boot process actually takes about 2 mins.(from grub2 to full desktop).
I have attached my bootchar, can anyone tell me what is wrong?
i used bum to take some useless boot procs off(useless to me).
more description: i am using ext4, been using alpha since alpha 1, no reinstalls, using grub2.

btw:the boot chart was not the most recent, but the "environment" is the same, and boot time is the same.

For what I see from the bootchart, preload is taking some time,
It's not installed by default. Have you tried without it?
Also a note to everyone: every excess process will increase the boottime, surprise :)

I'll attach pretty stock installations bootchart, notice that I'm on the desktop starting gnome-terminal at 0:49 while the bootchart is still running.
And this HDD is a piece of garbage (like most laptop HDD's are, regardless of manufacturer)

---

### Post by NRDNick on 2009-10-15
It currently takes me about 1:16 from the time I make my choice in grub, to when my cursor changes from the wait symbol to a normal pointer. Doesn't seem overly slow to me. However the same system loads XP in about 25 to 30 seconds. Hope things speed up to somewhere in that half a minute range, but I'm thinking I wont see those boot times till the next release.

---

### Post by xir_ on 2009-10-15
my laptop is pretty modern (only two months old) is there anyway of finding out the Hdd speed (i.e spin rate) from the command line?

---

### Post by buzzmandt on 2009-10-15
thanks for the help everyone with bootchart
1:28

---

### Post by xir_ on 2009-10-15
here is the bootchart without preload, still the same amount of time.

gdm session worker seems to be taking a while.

---

### Post by RalphP on 2009-10-15
I have installed Karmic on an old IDE drive and on an external USB drive. Time to boot on the IDE drive is about 35 seconds but on the USB drive it is about 1 minute and 35 seconds. For the first 60 seconds after hitting enter or after the countdown time reaches zero, the GRUB menu remains on the screen then the boot sequence starts. I have installed both Kubuntu and Ubuntu on this external drive with no difference in startup time. It must be something with USB hard drives and GRUB. Previous versions of Ubuntu did not have this problem.

---

### Post by miegiel on 2009-10-15
> **xir_ said:**
> my laptop is pretty modern (only two months old) is there anyway of finding out the Hdd speed (i.e spin rate) from the command line?
```
sudo apt-get install hdparm
```
If you want to know the RPMs
```
sudo hdparm -I /dev/sda1

/dev/sda1:

ATA device, with non-removable media
	Model Number:       WDC WD3200BJKT-00F4T0                   
	Serial Number:      WD-WX10A89H9277
	Firmware Revision:  11.01A11
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  625142448
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      305245 MBytes
	device size with M = 1000*1000:      320072 MBytes (320 GB)
	cache/buffer size  = 16384 KBytes
**[COLOR="Red"]	Nominal Media Rotation Rate: 7200[/COLOR]**
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 0
	Advanced power management level: 254
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Free-fall Control feature set
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
		enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	Security level high
	80min for SECURITY ERASE UNIT. 80min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee203451469
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 203451469
Checksum: correct
```
If you want to know read speeds and cached read speeds.
```
sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  252 MB in  3.01 seconds =  83.66 MB/sec
```
```
sudo hdparm -T /dev/sda1

/dev/sda1:
 Timing cached reads:   2986 MB in  2.00 seconds = 1495.73 MB/sec
```

---

### Post by novafluxx on 2009-10-15
Here's mine:
[ATTACH]132074[/ATTACH]

---

### Post by FormerSlacker on 2009-10-15
1:16 to boot. Not really impressed with that at all.

---

### Post by Vanishing on 2009-10-15
> **taavikko said:**
> For what I see from the bootchart, preload is taking some time,
It's not installed by default. Have you tried without it?
Also a note to everyone: every excess process will increase the boottime, surprise :)

I'll attach pretty stock installations bootchart, notice that I'm on the desktop starting gnome-terminal at 0:49 while the bootchart is still running.
And this HDD is a piece of garbage (like most laptop HDD's are, regardless of manufacturer)

thank you!
gonna start tweaking tomorrow..:guitar:

---

### Post by garvinrick4 on 2009-10-15
They tell me that it is only beta and not to judge while doing
daily upgrades. So I do my dailys and see if it is going to blow up
in my face or be a good day for testing Karmic. I believe by release date all will be as expected. I am sure there are those who will always do their best to kick up dust and that is expected also.

---

### Post by xir_ on 2009-10-16
> **garvinrick4 said:**
> They tell me that it is only beta and not to judge while doing
daily upgrades. So I do my dailys and see if it is going to blow up
in my face or be a good day for testing Karmic. I believe by release date all will be as expected. I am sure there are those who will always do their best to kick up dust and that is expected also.


no point testing a beta if you have the i'll just wait because they'll fix it approach. The point is to give any and all feedback possible.

---

### Post by FormerSlacker on 2009-10-16
Just out of curiosity, I installed Debian unstable to compare the boot times with Ubuntu, with comparable applications installed.

14 seconds from boot to GDM with Debian! Maybe another 5-10 seconds to log in. Quite a difference from 1:16 with Ubuntu.

---

### Post by KrazyPenguin on 2009-10-18
My boot still slow, i'm waiting for final release to reinstall and see if it makes a difference.

+1

;-)

---

