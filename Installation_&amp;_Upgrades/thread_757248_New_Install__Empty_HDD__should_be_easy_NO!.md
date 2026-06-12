---
title: "New Install / Empty HDD / should be easy? NO!"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by heinz57g on 2008-04-16
after reading about all those issues people have with splitting between WIN and UBUNTU, i thought for
a trial system it would be easiest to forget WIN, and install 8.04 from a live CD onto an empty HDD.

i had a few used ones around, so a 10GB previoulsy used for WIN98 came in handy. FDISKed and
reformatted (under DOS) it should do fine, no?

all the advise here is how to run WIN and LINUX on the same HDD. hardly anbody talks about a plain 
and simple all-HDD installtion, i could not even find proper instructions on this anywhere - so easy it
is, i thought.

starting the live CD (which i had used before, it is fine) brought the first surprise: going into the live
sytem first i thought it would have nothing to do at all with the HDD. actually i had read somewhere
one could run a live-CD-linux on computers without HDD at all. not mine: long before even getting to
the desktop the HDD started grinding, first came black screen, later for 20+ minutes a text-only screen
with multiple notices on errors and whatever, lines counting upward to somewhere near 300,000,
whatever that was. never seen it before.

then finally the desktop. from there i tried the INSTALL SYSTEM, and USE ENTIRE HDD. it says after
a (again long HDD grinding) while it would format the disk, but the %-indicator stays at zero, again
for a long time. and then the error code "The ext3 file system creation in partition #1 of  SCSI1
(0.0.0) (sda) failed". 

and that was it, out of there only a CTRL-ALT-DEL or a power-off worked.

tried that three times in a row (8.04, 7.10, 8.04, each 2hrs+), it is no fun anymore. but it does not 
seem to be a hardy-specific thing.

why is a live CD accessing/checking/running the HDD for 20mins? and what went wrong thereafter?

took the HDD out and had it checked under WIN for all possible faults, nothing. so why does UBUNTU
not accept, or like, this one?

i am at loss now.

greetings      - heinz -

PS: this is a standard new desktop, not a special laptop or even an eeePC.

---

### Post by Pumalite on 2008-04-16
Did you do md5sum on the iso? Did you burn at 4x or less? Did you burn as an image? Did you set CD as first in boot order in BIOS?

---

### Post by heinz57g on 2008-04-16
>> Did you do md5sum on the iso? Did you burn at 4x or less? Did you burn as an image?

sure, i have used that live CD multiple times on other machines, a setup on my wifes laptop worked
beautifully. and to make sure, the third try was with a newly burned one.

 >> Did you set CD as first in boot order in BIOS?

sure, how else would it have started and done what i described before?

greetings    - heinz -

---

### Post by jflaker on 2008-04-16
Should be painless......I dual-booted Vista and Linux and that was painless...........on a fresh drive, you should have no issues getting the system cut in.

You MAY have some issues with miscellaneous hardware (rare, mine had issues prior to 7.10 which seem to be resolved in 7.10), but you can come back here and ask should you have any problems!

---

### Post by heinz57g on 2008-04-16
>> Should be painless ....

so i thought. see above.

just to make (triple) sure: just booted another computer with same CD into a live system, went within
1.5 mins, no problems.

by feeling: there is something that linux does not accept about the previous setup ( WIN98 ) or formatting
of the HDD, something hidden, maybe i the MBR (but also checked and twice re-written). it boots
fine (now into DOS), WIN sees it and has no issues with it (when used as a slave in the other system),
so this is just a guess, but the constant grinding and 'trying' the disk under linux tells me i am not far off.
 
 >> You MAY have some issues with miscellaneous hardware (rare, mine had issues prior to
 >> 7.10 which seem to be resolved in 7.10)

unlikely. the same computer boots perfectly into LIVE when the old 300GB HDD is in it that it originally
had (though no ubuntu INSTALLATION tried). the desktop is there within a bit over a minute, whereas
the 'new' 10GB HDD takes some 25+ mins, and lots of text-only mssgs on screen.

 >> but you can come back here and ask should you have any problems!

which i am doing herewith, at 2am pure pleasure, and a big thanks to all of you for your patience.

greetings      - heinz -

---

### Post by Pumalite on 2008-04-16
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by heinz57g on 2008-04-16
tried something else: removed the HHD completely, and tried to go LIVE cd. and it worked. took a bit
longer, about 2 mins because of a long pause at the very beginning, some 30+ secs where just the bar
goes left/right/left, but otherwise, the live system came up beautifully. the waiting time at the begnining
is NOT there (or not by far that long) when booting with a working HDD installed (but not used).

greetings     - heinz -

---

### Post by oilchangeguy on 2008-04-16
slave the hard drive in another xp system. then from my computer, right click on the drive, properties, tools, error checking, put a check in both boxes, then click start.

---

### Post by heinz57g on 2008-04-16
DBAN and GPARTED should be on my KNOPPIX emergency CD, let me check right now. KNOPPIX i had
tried before: it gives a similar constant-try-and-grind when trying to set up, but unlike UBUNTU, it tells
you when it is doing that: ''Starting udev hot-plug hardware detection...", which again to me means it is
trying to recognize that HDD, but cannot, or only slowly.

lets see if i get it into it working state. once DBANed, do i have to use GPARTED? does linux, UBUNTU
i this case, not have its own formatting utility specially when doing a USE ALL HDD install?

greetings      - heinz -

PS: KNOPPIX booted in a (long) 3 minutes, some HDD grinding, UBUNTU in 20++ minutes, constant
grinding and running command-line text.

---

### Post by heinz57g on 2008-04-16
>> slave the hard drive in another xp system. then from my computer, right click on the 
 >> drive, properties, tools, error checking, put a check in both boxes, then click start

see above, already done, nothing. that plus other incl DOS hdd checks. nothing.

greetings       - heinz -

---

### Post by Pumalite on 2008-04-16
I like Gparted Live CD because is a newer version, more flexible, more powerful and offers more control. And yes. You have to format your whole HDD after DBan.

---

### Post by oilchangeguy on 2008-04-16
> **heinz57g said:**
> >> slave the hard drive in another xp system. then from my computer, right click on the 
 >> drive, properties, tools, error checking, put a check in both boxes, then click start

see above, already done, nothing. that plus other incl DOS hdd checks. nothing.

greetings       - heinz -

ok, then perhaps it's time to give up on the dead, or dying hard drive.

---

### Post by heinz57g on 2008-04-16
guess what: DBAN also does not like that HDD, it finished within 1 second with 'non-fatal' errors.
since it did not even try to go into the disk, i come back to my theory above: something wrong
with the boot or MBR sector of that HDD.

TBC ...

greetings      - heinz -

---

### Post by heinz57g on 2008-04-16
>> ok, then perhaps it's time to give up on the dead, or dying hard drive

my NOTHING above meant that those test found out nothing, the disk turns out A1-OK everywhere. it
seems more a logical mistake rather than a mechanical.

GPARTED live cd is standing by already.

greetings      - heinz -

---

### Post by Pumalite on 2008-04-16
If you have any doubts, try: TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by heinz57g on 2008-04-17
well, at least i got three hours sleep. managed to get DBAN to run in the most simple
mode and without verify, but run it did.

and now GPARTED does not recognize the disk, at all. stops with an error 15 seconds
into trying to format.

i am close to sure LINUX (in whatever version) is just the messenger, not the cause for
the problem, and i am close to throwing that HDD out. but why it would format under
DOS and WIN without problem, and boot and run, is beyond me. something when removing
WIN and reformatiing into DOS must have screwed up some tables (FAT or MBR or or or),
and i thought i could find out and overcome it.

so, lets testdisk give it a try.

greetings    - heinz -

---

### Post by dstew on 2008-04-17
Could it be a problem with the cable, and not with the drive? When you put it into the Windows machine, and checked it, did you use the same cable, or a different one?

---

