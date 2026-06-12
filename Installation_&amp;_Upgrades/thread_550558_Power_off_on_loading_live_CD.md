---
title: "Power off on loading live CD"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by Namakemono456 on 2007-09-14
I had Unbuntu installed on my old computer for about three months because I became tired of XP, but I bought a new computer about 2 weeks ago and now I'm having trouble installing. When the CD boots I get the option screen and when I hit install the screen goes to "loading linux kernel" then the computer powers off. my specs are

AMD x2 6000+
2gig ram DDR2 6800
nvidia 7300 GT OC
SATA HD
And using my 32 inch hdtv as a monitor ATM. (1360x768 max)

Any idea what my problem is? I've tried Unbuntu x86, Unbuntu ultimate gamers edition x86, and unbuntu ultimate x86 (trying to get away from x64 for awhile after the fun installs last time) sorry bout grammer but i cant type well sitting on the floor.

---

### Post by mxg01 on 2007-09-14
Are you using the alternate CD? If so, can you get into Ubuntu using a normal live CD?

You might try running the memory test from the alternate CD.

Sorry I can't be of more help.

---

### Post by Namakemono456 on 2007-09-14
Still the same problem with the alternate CD (x86) Any ideas?

---

### Post by Pumalite on 2007-09-14
I think it might be your 32 inch tv. If not; hardware failure. Check your Power Supply.

---

### Post by Namakemono456 on 2007-09-14
Same problem with my normal monitor, my power supply shouldn't be a problem because when i rebuilt my computer i removed a lot of unneeded pci cards and hard drives. I forgot to mention that i can boot xp x64 on the computer fine (thats what im using now) so its not that there are hardware issues. I'm trying to install unbuntu on one HD and have XP on the other.

---

### Post by Pumalite on 2007-09-14
Do you have two SATA or one SATA and one IDE? Is XP in sda1?

---

### Post by Namakemono456 on 2007-09-14
2 sata, XP is on sata1

---

### Post by Pumalite on 2007-09-14
Try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by Namakemono456 on 2007-09-14
Tried it, same error :/ I have about 4 different unbuntu distro cds/dvds sitting next to me.

---

### Post by Pumalite on 2007-09-14
When you say: 'same error'; you mean you power off every time? Weird. Did you do md5sum on your iso, burn at 4x, check CD for corruption after burn, before install, etc, etc. Have you tried these CD's in another computer?

---

### Post by Namakemono456 on 2007-09-14
CD's boot fine on my little brother's computer, and his is slow compared to mine.
AMD 2100+
1g ram
ATI Radeon X1350 Pro

Yeah and i mean the power off error on all of them

---

### Post by Pumalite on 2007-09-14
Well, the only problem I see with your computer is your ATI Radeon. That should have been solved with the Alternate CD. I don't know what else to tell you.

---

### Post by Namakemono456 on 2007-09-14
The radeon is on my little brothers computer that unbuntu boots on, my comps specs are in the first post and uses a geforce 7300

---

### Post by jacob01 on 2007-09-14
so they computer just shuts down?

if it doesn't and the display just doesnt appear then the linux drivers on the disk might not support the resolution you are using.   can you try a different monitor

---

### Post by Pumalite on 2007-09-14
On second thoughts; I would change burner. (Funny that your power supply is OK and that CD's are fine in other computer)

---

### Post by Namakemono456 on 2007-09-14
The cd managed to get to the loading screen this time amd make a few passes, and then it just powered off. I thought maybe it was temperatures but the computer is at 40degrees c after 3 days straight running wondow. Could there be a voltage thing that unbuuntu sees and is therefore shutting it down?

---

### Post by Pumalite on 2007-09-14
I have to say that I'm inclined to think that this is purely hardware problem: wires, connections, etc.

---

### Post by Namakemono456 on 2007-09-14
Yeah but the problem i have with that is that i boot windows no problem... maybe ill take a look around my box.

---

### Post by Pumalite on 2007-09-14
Remember that Windows is already installed. What if something went wrong with your burner in the interval?

---

### Post by Namakemono456 on 2007-09-14
The disks were burned on 2 other Computers (i have 6 in my household)
New evidence though, the alternate install disk gets to different points before the power off occurs, the farthest was just after network install, earliest when loading the kernel

---

### Post by Pumalite on 2007-09-14
Sounds like your burner is short-circuiting.

---

### Post by Namakemono456 on 2007-09-14
I see what your saying lol, the burner is shorting while it reads...that might be it, sorry i thought you meant it was shorting while burning.

---

### Post by Pumalite on 2007-09-14
Short-circuit
Short-circuit Short"-cir`cuit, v. t. [imp. & p. p.
 Short-circuited; p. pr. & vb. n. Short-circuiting.]
 (Elec.)
 To join, as the electrodes of a battery or dynamo or any two
 points of a circuit, by a conductor of low resistance.
 [1913 Webster]

---

### Post by Namakemono456 on 2007-09-14
Went out and bought a new dvd drive, same problem.

---

### Post by Pumalite on 2007-09-14
Next suspect would be your video card, but have you run a memtest?. Otherwise you would have to take it apart and back together again, but I suspect you would rather be a prisoner of Micro$%&

---

### Post by Namakemono456 on 2007-09-14
Yeah i would...i ran the memtest through 2 passes when i first got the problem :/ Looks like i should just look through my wires at this point.

---

### Post by Pumalite on 2007-09-14
How about trying this:CPUCooL - [2007-09-01 | Shareware $17.95 | 1.67 Mb | Win All | 515712 | 4.69 ]
Cool, optimize and monitor your system.
From here:[http://www.majorgeeks.com/downloads7.html](http://www.majorgeeks.com/downloads7.html)

---

### Post by jesscroft on 2007-10-03
Hello --

I am having the same problem.  The install gets as far as detecting hardware and then the computer powers off.  I've tried both version of xubuntu 7.04 -- same thing for both of them.  I used the 7.04 alternative version disk to successfully install on another computer.  Did you ever figure out what was going on?  I am running a memtest now.

---

### Post by Phill Kenoyer on 2007-10-19
Hello,

I had an old version of Ubuntu installed on my laptop and I was having problems with the video where the graphics were messed up when I moved windows around.

So today I started installing 7.10.  I got all the way to where it started installing the software and the computer would shut off.  I had thought the power fell out and the battery was dead because the charging light came on.

Nope, Windows runs fine on it.

So I booted Ubuntu again and it would not even boot.  It would just turn the computer off.

After about 10 times of trying to get things going I found out that it's when Ubuntu is "detecting hardware".  I'm not sure if it's the hard drive or the power management, but when it gets there everything goes dark.

I finally got booted up on the live CD, and from the terminal I use cfdisk to make the partitions.  I mkswap and mkfs.ext3, and all that ran fine.  So I'm thinking that it might be another issue.

I'm currently downloading the alternate CD, but from reading the comments in this topic I'm not sure if that is going to help... Unless there is a way to turn off hardware detection.

I'm going to go into the CMOS and see what options I can set there for power management... I don't think Linux even uses the CMOS settings though. :confused:

---

### Post by Phill Kenoyer on 2007-10-20
Hello again,

I downloaded the alternate disc and installed Ubuntu with it.  The text based install worked good.  Not as fancy, but probably faster than the GUI install.

The only problem, and I'm not sure if this is different from the normal install, is that when booting I don't get the fancy Grub boot loader (the graphic version) and I don't get the nice boot up screen with the Ubuntu and progress indicator.  When I boot it's just a black screen until the login screen comes up.  That's kinda lame.

But, now that it's up and running I'm able to drag windows around again without the screen getting all messed up.  I'm able to scroll window contents without corruption too.

Nice!

---

### Post by Phill Kenoyer on 2007-10-21
I guess I was wrong.  I rebooted the system and now it starts to boot and turns off just like before.

I rebooted in daig mode and that worked.  Check the syslog files, but I could not find anything for when it shutdown.  fsck says everything is fine with the hard drive.

Strange problem.

---

### Post by justinhj on 2007-10-21
I've been seeing issues identical to this one. The install process kept powering off while it was running. I was able to install using the alternate disk, but now my pc just powers off every 10 minutes or so. It looks very deliberate, the screen fades out and it closes down. 

I can run xp on the same system and it never shuts down.


System info:

Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
Language: English (Regional Setting: English)
System Manufacturer: ASUS
System Model: A7V400-MX
BIOS: Phoenix - Award BIOS v6.00PG
Processor: AMD Athlon(tm) XP 2400+, MMX, 3DNow, ~2.0GHz
Memory: 512MB RAM
Page File: 506MB used, 743MB available
---------------
Card name: MSI NX 6600 (NVIDIA GeForce 6600)
Manufacturer: NVIDIA
Chip type: GeForce 6600

Name: VIA Rhine II Fast Ethernet Adapter
Name: Sound Blaster Live! 24-bit

---

### Post by leopards on 2007-10-22
Way back I think you said you were using the i386 install disk on a AMD 64 bit machine? Might want to try the AMD64 bit version of the install disk! I am also new at this, so I am not sure if the i386 version will run on a 64 bit machine!!

---

### Post by Phill Kenoyer on 2007-10-23
I tried booting using the repair option.  It goes real quick so I had to do it a few times.  Looks like the last log entry is something about PC Speaker.

* Loading Hardware Drivers
 ...
 Something about PC Speaker maybe

I tried booting off CD and checking the log files, but I guess it shuts down before syslog starts.  Nothing in the logs for today.  I'll check the startup files and see if there is something I can comment out.

---

### Post by Phill Kenoyer on 2007-10-23
AHH!

I was trying to see if the Pause key would keep it from rebooting, and when it came up to the point where it was rebooting I hit the key.

Well, it didn't reboot this time and I am able to see what the problem is.

"Intel TCO WatchDog Timer Driver"!

I'll bet that's what the problem is.  I'm going to disable it somehow and see if that fixes my issues.

---

### Post by Phill Kenoyer on 2007-10-23
I added "disable iTCO_wdt" to /etc/modprobe.d/blacklist.
But that didn't work.  Still turning off on me.

The only way I can boot up is to press the "Pause" while it's booting.

---

### Post by Phill Kenoyer on 2007-10-23
I reset the CMOS, and it was booting just fine.  I tried the regular install CD and it turned off on boot.  So I took the CD out and tried booting normally from the alt install and it boots fine.

I don't get the fancy boot up, just a black screen, but at least it's working.

---

### Post by FXEF on 2007-10-23
> **Namakemono456 said:**
> Tried it, same error :/ I have about 4 different unbuntu distro cds/dvds sitting next to me.

This is just a wild guess. I think the kernel is booting OK, however X does not load. Most likely video card and/or monitor does not play well with X. I have found that X does not like high and/or non-standard resolutions. Not sure why PC shuts off, could be a BIOS setting shutting PC off when X fail to load.

FXEF

---

### Post by DagonSphere on 2007-10-23
I seem to remember having a similar problem with my system at home - Not sure if it ever powered itself off or not.  I had to change the USB settings in the BIOS.  If you can, try turning down the USB port speed in your BIOS and try booting again

---

### Post by daddz on 2007-10-23
I am having a similar problem.

I´m installing from alternate cd. That´s running fine!
When I boot then it turns the pc off at about 3/4 of the loading bar.
Sometimes I can login but after some seconds it turns off.

The strange this is that I can use windows without any problems. :confused:

---

### Post by DagonSphere on 2007-10-25
Did you try to change the USB settings in your BIOS, if possible?

I had to do that in order to get the 6.06LTS CD to boot on my system.  One the GUI booted, I installed and everything went well.

---

### Post by Phill Kenoyer on 2007-11-07
Well, Ubuntu has been running for about a Week without problems, then yesterday it started doing the power off thing again.

One thing I noticed this time is that it told me the power cable was unplugged from the laptop in Gnome.  But it wasn't and I checked.  But when I rebooted, it would not boot anymore.

I also noticed that when it does power off, the charge light comes on.  I'm thinking it has something to do with the power features.

PS, I turned off USB legacy support in BIOS.  It booted up, but I can't be sure if that fixed it or if it decided to work today.

---

### Post by Phill Kenoyer on 2007-11-15
Welp, I managed to blow up the Windows partition on the laptop.  So I put the XP disc in and did the Repair option, which just reinstalls everything back to default, and then got stuck trying to upgrade to IE7.  The License Key is no longer valid and I don't want to mess with calling them for another key.  Today I nuked the drive and tried to install Ubuntu again.

Same thing.  It starts to install then turns the laptop off.  Then on reboot, it won't boot up.  Just turns off.

I'm done messing with Ubuntu.  I'm off to download something else.

---

### Post by helicase on 2007-11-15
> **Phill Kenoyer said:**
> I'm done messing with Ubuntu.  I'm off to download something else.
I hope trying something else works for you, but I'm not sure it will. I just tried to run a live cd on my friends laptop and experienced the exact same problem: the kernel loads and then the computer powers off. The thing is though, I tried feisty and then knoppix with the same result, so it doesn't seem to be a distro related problem.

---

### Post by torgrot on 2007-11-15
When the menu comes up from the LiveCD.  Highlight the install/run Ubuntu and press F6 I believe.  Move the cursor to the end of the kernel line and add acpi=off pci=biosirq I had a similiar problem on my Dell.  It would start to load and then reboot at random and not all the time.  It drove me crazy.  

torgrot

---

### Post by harryfiderchi on 2007-11-16
Hi all, new to ubuntu but already love it, however I have a very similar problem,

I have been looking around for days to find answers,

I origanaly installed Edgy from a cd, no worries.  

I upgraded via update manager to Fiesty, no worries.

I tried to upgrade to Gutsy via update manager halfway through install the pc powered off,

tried rebooting all I get is black screen with flashing curser, It took windows out with it,

Managed to get windows going but everytime I try booting to ubuntu (I can bring up a  

comand prompt), It takes out windows again.

I'm not sure what to type at the prompt to check what has gone wrong or even if it can
 
be recovered. It's getting to the stage where I am to scared to try because it takes out

windows every time and I am left with no working pc.

---

### Post by Pumalite on 2007-11-16
On top of all in this thread; I think you guys should check your screensaver, go to Advanced>Power Management>And make sure that 'Poweroff' is all the way to the right where it says 'Never'

---

