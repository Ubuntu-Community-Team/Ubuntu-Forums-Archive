---
title: "Lowest Spec PC Running Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by guimaster on 2009-10-26
Hey all,

 I am hoping that people who read this thread and have tested Ubuntu Karmic on older PCs can post their computer specs.

 The reason I ask is because I am wondering if Ubuntu Karmic is going to be too resource demanding for my laptop. I have a 1Ghz P3 cpu with 1GB of ram and a 16MB video card.

 I found Jaunty to be sluggish at times, especially running Open Office. That may have just been Jaunty though or Open Office and not a reflection of how Karmic will run.

 Thanks for your assistance!

---

### Post by psyke83 on 2009-10-26
I've got a Pentium M 1.5Ghz, 768MB RAM, Intel 855GM graphics. Karmic performance is excellent.

Your processor is getting old, but it should be sufficiently fast for most everyday applications and tasks. You have plenty of RAM, so that should be fine. What video card have you got? If it's Intel, your graphics performance will be much better in Karmic.

Putting aside graphics performance, Karmic should be no more resource-intensive than Jaunty. However, I recommend that you perform a fresh install, especially if your current installation is using the older EXT3 filesystem.

---

### Post by autocrosser on 2009-10-26
It's real snappy on my T42--1.8 CPU, 2G DDR 333 ram & a ATI FireGL 128 card--so going down specs a bit should be just fine.....

---

### Post by 23meg on 2009-10-26
Working fine on a low-power 900Mhz Celeron-M ULV 353 with 1GB RAM and GMA950, barring the expectable speed bottlenecks with such a configuration.

---

### Post by mrsurb on 2009-10-26
I'm running on a 700MHz Athlon with 384MB RAM. Though I'm running server so no GUI :) I guess that's cheating.

The great new karmic feature for me is how well byobu works over ssh.

---

### Post by cariboo on 2009-10-26
I had LXDE running on a 75O Mhz Duron with 512Mb ram upgraded from Jaunty, it ran quite well. Unfortunately I'm still looking for the holy grail, I'm trying other distributions to find what runs the best for me on that particular system.

---

### Post by todak on 2009-10-26
I am running a hand-me-down (got it free from my former workplace) Dell Precision 350 Workstation with a Pentium 4 @ 2.26 gHz and 1.5 GB Rambus RAM and have no ill effects, though I want to put a newer board that I have, that takes standard memory, into the tower. The Rambus memory is stupid expensive! I could buy a good used newer tower for less expense than it would be to replace the Rambus memory. :P

---

### Post by prshah on 2009-10-26
> **23meg said:**
> Working fine on a low-power 900Mhz Celeron-M ULV 353 with 1GB RAM and GMA950, barring the expectable speed bottlenecks with such a configuration.

Yet another positive vote for 900Mhz Intel Centrino, 1GB RAM, Intel 855GM. Works great, compiz also enabled. The difference in firefox startup between Jaunty and Karmic is DRAMATIC!

---

### Post by k3lt01 on 2009-10-26
My laptop, check my signature for its specs. No problems what so ever so far and have been running it for 3 days now. Internet, Pidgin IM chat (Empathy is pathetic but thats another story), Evolution, OpenOffice all work brilliantly well. Haven't tried much else yet.

---

### Post by GeorgeVita on 2009-10-26
Hi, I have a one year newer PC than this on thread title and works fine **except softmodem** and **3G modem** (with the standard kernel to be released). System info:

_Working fine with 9.10_:
Motherboard: MS-7005 MICRO-STAR INTERNATIONAL CO., LTD
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz
DIMM SDRAM Synchronous 2x256MiB (width: 64 bits)
VGA: RV350 AS [Radeon 9550] ATI Technologies Inc
ATA Disk: ST340014A Seagate 37GiB (40GB)
cdrom: DVDRW LDW-451S LITE-ON
cdrom: CD-R/RW SW-252F SAMSUNG
[U]
Not Working with 9.10:[/U]
soft modem: [V.92 56k WinModem Agere Systems]("http://www.linmodems.org/")
[Huawei E169 3G modem]("http://ubuntuforums.org/showthread.php?t=1285294")
[ZTE MF636 3G modem]("https://bugs.launchpad.net/ubuntu/+bug/408555")
   
Regards,
George

---

### Post by Onesimus on 2009-10-26
I'm running Karmic on a Dell Dimension 4500.  It has 1.7GHz processor, and 512Mb of RAM.  It runs fast, though I haven't got Visual effects enabled.

you should have no problems at all.

---

### Post by knarf on 2009-10-26
I'm running Karmic (testing) on a Thinkpad T23 with a 1.2 GHz Pentium III-m and 768 MB of SDRAM. This is sufficient to run just about anything I need. It is also a good way to make sure the software I develop runs on moderate spec hardware. The only drawback of this system is the graphics processor, a wheezy and anemic 'SuperSavage'. The OpenGL support for this chip is sub-optimal and somewhat buggy, not to mention slow. This is no fault of Karmic or Ubuntu or Xorg or Linux though, the hardware is just not up to it...

---

### Post by 00b00nt00 on 2009-10-26
To the OP, I had a Compaq E500 laptop with an 800Mhz PIII and 512 MB RAM. Intrepid worked fine, but without compiz (as to be expected).

If your computer is a desktop with a socket 370 CPU, you may be able to drop in a 1.4 Ghz Tualatin PIII with 512KB cache. At least then it will certainly be faster than a netbook!

---

### Post by ikisham on 2009-10-26
I guess the bottleneck will be the desktop environment. Maybe disabling the graphical effects will help and also mind you that if you hit that blue question mark on the top panel you'll have the cpu running at 100% for a couple of minutes.

---

### Post by r4lly on 2009-10-26
PC spec 

1,6 AMD Athlon XP 
512 MB DDR 
AGP NVidia 6600xt

All of them secondhand 

:)

---

### Post by PaulInBHC on 2009-10-26
AMD Duron 1.2
512 SDRAM
Radeon 7000 64mb
7200 rpm hdd

Runs great with half the drain of XP Home. I play a flash game that I couldn't full screen in Windows but I can now.

---

### Post by emarkay on 2009-10-26
Has a P3 with 384  Mb of RAM (old Dell I was scrapping), and while it took near forever to load, the Live CD was doing just fine.

---

### Post by edujose on 2009-10-26
Hi guimaster, I think Karmic will run well, like many people have said before.

Karmic runs smooth here using a second-hand machine: 1 GHz PIII, 512 MB RAM, 10 GB HD and a cheap ATI Radeon 9600 AGP graphics card with 256 MB RAM on it I think (Compiz works great with open-source driver).

Using the original 8 MB graphics card (maybe a Trident or an S3, don't remember) the GUI worked, though slower and with some jerkiness when moving windows (and no Compiz).

Anyway your card has 16 MB so it should be good enough to run Karmic (might run the GUI more or less smoothly, but will run it).

---

### Post by jso2897 on 2009-10-27
I have a failure to report - an old Dell, with a 700mhz PIII. It will install, but on boot, it won't recognize or load the kernel.

---

### Post by cascade9 on 2009-10-27
It runs, OK-ish on a Intel P3-866, 376MB usable RAM (384MB with 8MB shared video), ultra-crappy intel 810 video. If it had a touch more RAM or a decent video card it would run a fair bit better. 

> **00b00nt00 said:**
> To the OP, I had a Compaq E500 laptop with an 800Mhz PIII and 512 MB RAM. Intrepid worked fine, but without compiz (as to be expected).

If your computer is a desktop with a socket 370 CPU, you may be able to drop in a 1.4 Ghz Tualatin PIII with 512KB cache. At least then it will certainly be faster than a netbook!

I'd be careful of this. It might be possible, depending on what motherboard you have, but most of the coppermine pentuim 3 boards wont take a tualatin in my experience. Worth if it it does, the 1400/512K P3s are fast.

---

### Post by andrewabc on 2009-10-27
Works great on pentium4 1.8ghz, 768mb SDRAM, 80gb hard drive. 32mb tnt2 video card that doesn't even have proprietary drivers (because ubuntu/drivers stopped supporting it a year or two ago). Trendnet TEW-424UB wireless g usb stick works better than previous ubuntu. HP Printer/scanner detected and works.

Best working ubuntu on this computer yet.

> **guimaster said:**
> 
 The reason I ask is because I am wondering if Ubuntu Karmic is going to be too resource demanding for my laptop. I have a 1Ghz P3 cpu with 1GB of ram and a 16MB video card.


You may want to update to a newer laptop :)
The cheap $300 netbooks are much faster (even though slow by todays standards). 1.6ghz atom, 1gb ddr2 ram, intel GMA950

---

### Post by cascade9 on 2009-10-27
@ andrewabc- you should be able to get the drivers for a TNT/TNT2. No idea on why ubuntu stopped supporting it, but the drivers are on the nVidia site (under 'legacy')-

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I dont know how much more you would get from an atom over the faster of the p3s, even with them having ddr2 etc, but I doubt it would rank as 'much faster'. 

[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)

---

### Post by humphreybc on 2009-10-27
Back home I've got Jaunty running on an 800mhz processor with 512MB SD RAM. It's pretty good. Hooked up to a 19" LCD with 1080P Resolution, so it's a bit sluggish in that regard :P

---

### Post by francsal on 2009-10-27
> **cascade9 said:**
> @ andrewabc- you should be able to get the drivers for a TNT/TNT2. No idea on why ubuntu stopped supporting it, but the drivers are on the nVidia site (under 'legacy')-

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I dont know how much more you would get from an atom over the faster of the p3s, even with them having ddr2 etc, but I doubt it would rank as 'much faster'. 

[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)

I can tell you form personal experience that an Atom 1.6 really does outperform a PIII 933 running Kubuntu. My sister has one old PIII computer on her house, and out of kicks, decided to try Kubuntu on it. It has 1 GB of ram, too, and an ATi card, if I´m not mistaken. Therefor, the setup was very similar to my Atom with 1GB of ram and Intel graphics. Short story, it booted a lot faster on my netbook (probably has to do with the HD, right?), and it felt much more responsive thatn on the PIII. Maybe the Atom per se it´s not faster that the PIII, but the sum of the components make it, IMHO, faster overall.

Back on topic, that machine was running it acceptably. It was not a speed demon, obviously, but for everyday chores it was adequate.

Cheers.

Frank.

---

### Post by cantab on 2009-10-27
Dual Pentium III 866 MHz, 512 MB Ram here. Karmic runs fine in most respects. The exception being the sound is a total f-up.

---

### Post by HotShotDJ on 2009-10-27
I'm running Karmic RC on an eeePC 900 which has a Celeron-M 900 Mhz processor and 1G RAM.  Runs just fine.

---

### Post by andrewabc on 2009-10-27
> **cascade9 said:**
> @ andrewabc- you should be able to get the drivers for a TNT/TNT2. No idea on why ubuntu stopped supporting it, but the drivers are on the nVidia site (under 'legacy')-

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I dont know how much more you would get from an atom over the faster of the p3s, even with them having ddr2 etc, but I doubt it would rank as 'much faster'. 

[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)

As for drivers, ubuntu stopped support because X or something stopped support, so I'd end up having to hack a bunch of stuff to get it to work.

I'm pretty sure netbook/atom would run much faster than pentium 3.
You also have to take into consideration the mainboard, with pentium 3 probably only having ICH 4 or 5. Atom has ICH 7 or 8.

Atom front side bus is much larger than P3. DDR2 would be much faster than SDRAM. Going from pentium 3 to atom is skipping a generation (pentium 4 era). So you should definitely notice an improvement. Yes atom and P4 have similar mhz, but everything else is upgraded, and less power consumption/heat.

---

### Post by Sylslay on 2009-10-27
I sugest to open topic and ask for more low - spec hardware?
 (not upgrate to max) 

Lets start?

CPU, p3/p4 , AMD Athlon/Duron. Frequancy range 600-1000MHZ
ram 128-256MB ram
video S3,ATI,Nvidia with VRAM 16-32MB
HDD 10GB , 5400RPM, slowest one
HDD 20GB   7200RPM  fastest one

Has anyone tried run system with hardwere from 2000-2001 ???
Send it to scrapyard?

I know that windows 2000 still working fine on that machines,but win xp very slow, 
but modern linux? How it perform?

Minimum:cpu 800Mhz/256cash, ram/sdram/ddr1 256MB, video 32MB,lxde,gnome,for web/office PC?

thx  psyke83

---

### Post by psyke83 on 2009-10-27
> **Sylslay said:**
> I sugest to open topic and ask for more low - spec hardware?
 (not upgrate to max) 

Lets start?

CPU, p3/p4 , AMD Athlon/Duron. Frequancy range 600-1000MHZ
ram 128-256MB ram
video S3,ATI,Nvidia with VRAM 16-32MB
HDD 10GB , 5400RPM, slowest one
HDD 20GB   7200RPM  fastest one

Has anyone tried run system with hardwere from 2000-2001 ???
Send it to scrapyard?

I know that windows 2000 still working fineon that machines,bu win xp very slow, 
but modern linux? How it perform?

Ubuntu's memory requirements are higher than Windows XP. 128MB will be unusable with the default GNOME release. 256MB will be adequate, but you will begin hitting swap quite soon, and large applications such as OpenOffice will seem a little slow to load.

If you insist on testing Linux a 128MB system, try the Xubuntu release, and download the alternate installer CD (as the text installer needs less resources to install).

I highly recommend that you get some extra memory, even for such an ancient machine (and it'll be a lot cheaper if you buy second-hand).

---

### Post by snkiz on 2009-10-27
Running karmic on a 855 Mhz p3 Coppermine & 384 MB ram Video is Nvidia fx5200 audio is Ensoniq 5880B. Its tight on ram but runs. Have a stupid VIA apollo chipset that doesn't wanna let my video card run at full speed (2x instead of 4x), but I don't know if that would matter with my low fsb.

---

### Post by bodycoach2 on 2009-10-28
I'm running 9.10 on a Acer TravelMate 260 laptop. 1GHz P3 (throttles between 733 and 1GHz), 768 MB ram, 5400rpm 80gb hard drive. It boots and runs faster than hardy did, and youtube and hulu videos work fine -they did not work on hardy. Voicerecorder and Rhythmbox will not start at all. Audio files play on VLC. 

I keep this laptop because of the 4 hour batter life. So far, with 9.10 it's actually done a bit better than Hardy, in that area. I'm hoping updates fixes some general issues soon.

---

### Post by Sylslay on 2009-10-28
to snkiz,

freind of mine, have gf6200
use only agp4 instead agp8, but see no diffrence ,

but on wiki [http://en.wikipedia.org/wiki/Agp](http://en.wikipedia.org/wiki/Agp) 
Version
AGP 1x
    A 32-bit channel operating at 66 MHz resulting in a maximum data rate of 266 megabytes per second (MB/s), doubled from the 133 MB/s transfer rate of PCI bus 33 MHz / 32-bit; 3.3 V signaling.
AGP 2x
    A 32-bit channel operating at 66 MHz double pumped to an effective 133 MHz resulting in a maximum data rate of 533 MB/s; signaling voltages the same as AGP 1x;
AGP 4x
    A 32-bit channel operating at 66 MHz quad pumped to an effective 266 MHz resulting in a maximum data rate of 1066 MB/s (1 GB/s); 1.5 V signaling;
AGP 8x
    A 32-bit channel operating at 66 MHz, strobing eight times per clock, delivering an effective 533 MHz resulting in a maximum data rate of 2133 MB/s (2 GB/s); 0.8 V signaling. 

Any one know how those can be explene with diffrent set of mobo?
And can you really see diffrence betwin agp 2,4,8 in any app or games???:o

---

