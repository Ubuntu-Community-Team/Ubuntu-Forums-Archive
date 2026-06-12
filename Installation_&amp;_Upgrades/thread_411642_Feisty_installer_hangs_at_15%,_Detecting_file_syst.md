---
title: "Feisty installer hangs at 15%, Detecting file systems on Sony Vaio SRX87"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by guy-in-corner on 2007-04-17
I'm attempting to install the latest beta of Feisty on my Sony Vaio SRX87. It keeps hanging at 15%, while detecting file systems. Initially, the DVD-ROM drive whirs periodically, but it's stopped and hasn't done this for a while now.

I've done some searching around this, and my problem appears to be different from other instances:

One person claims that manually formatting (i.e. using fdisk) the disk before installation solves the problem. I tried this, going through the "Manual partitioning" step in the installer to assign mount points and swap. This doesn't solve the problem.

Other people have said that they've seen this, but that they've still been able to move the mouse. I can't. The system appears completely frozen. Pressing Num Lock has no effect, for example.

I can't get the Ctrl+Alt+Fn key combinations to work either, so no luck there.

I know that this laptop is capable of running Ubuntu, because I've successfully run both Dapper Drake and Edgy Eft on it before.

I'm going to attempt the alternate installer, but does anyone have any other suggestions? I'd (obviously) like to see this fixed before the final release of Feisty.

---

### Post by chakkaradeep on 2007-04-17
Did u burn your CD at what speed? This happens sometimes when you burn your ISO file in a larger speed. I usually stick to 12x speed when writing ISO images.

Try once by burning the ISO image with a low burning rate.

---

### Post by MR Bacardi on 2007-04-23
I ran into the same problem when installing Feisty on a laptop.
I did burn the CD at full speed, but I have installed Feisty on two other machines with the same CD, both without the problem (and I had the CD checked for errors).

My solution was to run a text install (choose from boot menu).
However, this is not as easy as installing from gnome running the live CD and I would guess it is a bug of some kind.

---

### Post by adah on 2007-04-29
I have this problem too :( . The test system is a SiS-based desktop. I thought there might be a conflict with the existing system, so I wiped 6.04, and then Windows, and let the the installer manage the partitions completely (tried manual partitioning in vain). Still no go. This is very bad and saddening.

How to install in text mode? I cannot find the option in the boot menu.

---

### Post by mabersold on 2007-04-30
I've also run into the problem, but I was pretty sure that it's because my laptop just can't handle the GUI installer.

I'd also like to know how to install from text mode, I don't recall seeing that option from the CD menu while booting up.  I'm installing Xubuntu, FYI.

---

### Post by adah on 2007-05-08
Another shout for help. Anyone has any clues?

How to do a text-only installation? Should I go for the server installation (and install the GUI later)?

---

### Post by Topsiho on 2007-05-08
Seems many people have this problem. I have it on one of three computers. I read a suggestion somewhere that, trying to speed up the boot process for Feisty, processes are run in parallel, and that timing problems may be the cause that things go wrong on some but by no means all computers.

I used the alternative CD with success, and maybe the suggested text install will also work.

Feisty DOES boot very fast though :)

Topsiho

---

### Post by Topsiho on 2007-05-08
"How to do a text-only installation? Should I go for the server installation (and install the GUI later)?"

A text install is not easier or more difficult as a graphical install. It just looks less nice. So please do not let you be deterred from using a text install.

The graphical install is in one place even more counter intuitive then the text install, where it lets you select a partition to alter it's properties. To me  I always have to remember that I am not selecting the existing properties when I click on it ...

Topsiho

---

### Post by Kaptain Chaos on 2007-05-08
Hello,

The best thing to do is download the 'Alternate'.iso  version for your system and burn to a CD.
Boot up and select the text install option. **Don't** install the server version - this will only give you a very basic 'text mode' system. The installation process is very easy to follow and great for any system that hangs.

I installed both Ubuntu and Xubuntu Dapper on 2 machines with limited RAM this way. I increased the RAM on one and can now install from the live CD, the other has an old Cyrix2 processor with 128mb EDO ram. The alternate install works perfectly.
If you have any problems you could try looking at [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/"). Herman gives a blow-by-blow account of installing via the Alternate CD.

Hope this helps.

---

### Post by gtsears on 2007-06-02
I downloaded the 7x bootable ISO and burned the CD at 8X yesterday.  I tried it out in a locally built 1Ghz AMD clone.  I tried it 3 or 4 times befor it booted successfully.  I played with it a bit and decided to install it 'cause it was sooo ssslllllooowww running from the CD.  The PC had a working install of Win2Kpro on it, when the first attempt failed at step 7 15% I thought it might be due to the NT file system.  On the next Ubuntu boot I used the partitioner to manually clear all partitions and repartition.  Because it had succeeeded in booting after 3 or 4 tries without me doing anything to fix it I decide to use that method with the install.  After about 4 or 5 repeats and waiting 45 - 60 min. after the apparent hang, I switched to a trusty WinXP machine and came to the forum.

While getting registered and reviewing my profile etc. I noticed that the 15% dialog had faded and was unreadable, as I was walking over to get a closer look the dialog came back up, but then indicated 20% , and then the "ubuntu - File Browser" came up.  The slider on the Install Dialog continues to advance (now about 52%).  I don't think I did anything to fix anything, but the install seems to be OK for now. 

I'll post again when it finishes or croaks.

Gene  :D

First Edit at 21:27 GMT -5

It appeared to finish installing OK.  When I clicked the RESTART button it went into lala land for long enough that I did a hard reset.  On restart it hung at a black screen. After several tries at rebooting  I have set it to reinstalling.  On step 5 or 6 it did not find anything to import into the new install.  Currently it says it is "Detecting file systems" the slider is at 15%.

I'll update again when there is something to report.

---

### Post by GRbenji on 2007-06-03
I had faced this same problem and let me tell you the story and the cause and hopefully the Linus expert can solve it.

I've 8 identical systems as shown below except for the problematic one that is using the onboard graphics as the agp card is dead and I've no spare.

- GA-7VM400M with AMD2400+
- DDR333 256MB
- GF4 MX440
- CDrom and disk used to install Edubuntu all systems is the same one as all system do not have CDrom installed

When booting up with the CD, have to select "Start Edubuntu in Safe Graphics Mode". Otherwise it will hang hang way. After bootup with "Start Edubuntu in Safe Graphics Mode", can feel the lag in moving mouse or typing.  And when install into HD, will stop at the 15% "Detecting file systems".

After many tries, gave up and pull out a agp card from 1 of the other system.  Am still installing now but have passed that 15% stage.

Will be pulling out the graphics card after installation completed to see if can bootup or not.

---

### Post by girard on 2007-07-01
i'm having the same problem with my system. i formatted the disk using gparted and i'm doing the live cd install of 7.04 again. dunno if this is going to get stuck at 15% again. 

i'm not sure if i missed something above, but is there a solution to this already? is this due to a bad burn and should we try burning the cd at a lower speed?

---

### Post by bear105 on 2007-08-04
FYI...Had this same trouble but let the process run for awhile. Was starting to get worried but noticed the DVD was still spinning. Eventually everything caught up and installed correctly. No reboots...

---

### Post by adil_uk on 2007-08-09
I had the exact same problem. in my case this site helped me solve the problem

[https://answers.launchpad.net/ubuntu/+source/yelp/+question/3929](https://answers.launchpad.net/ubuntu/+source/yelp/+question/3929)


First off using gpart or fdisk make sure you create a /dev/hda1 = ext3  and /dev/hda2 = swap

Then during the installation process and when you get to the partitioning part  I chose the "Manual"  option and  there were both of the driver I created. Right click on  /dev/hda1 and press on `Edit` button make sure on the` mount point`  to choose "/" and the click on ok. the /dev/hda2 is the swap just make sure you have more than 256.MB on it and click on ok. and off you go from there.

This is how I solved my  problem I'm not suggesting it will work for everyone but if it did then, ...well  enjoy your Ubuntu.

P.S make sure you do this after creating /dev/hda1 

sudo mkfs.ext3 /dev/hda1

---

### Post by plasma16 on 2007-10-27
I'm seeing the same problem on my desktop with my AGP graphics card.
I have three partitions, one ntfs for my winxp, another ext3 and a swap partition.
Ran the Ubuntu 7.10 (not-alternate version) in normal mode, selected Manual mode for partitioning.
Assigned the ext3 partititon to mount / and select to be formatted.
Hangs at "Detecting file system : 15%"
I also tried using ext2, same problem.

I'm trying to download the alternate version and try text-mode install.

---

### Post by khundeen on 2007-11-27
I had this problem too with the Ubuntu 7.10 Live CD.  

I have Dell Inspiron 8600.  However, I was trying to install Ubuntu on my WD Passport hard drive.  I am not sure if this could be a reason. 

I did check the integrity of the CD and found error of 25 files.  I am not sure if this caused it.  I didn't try to write a new CD but decided to try the Alternative CD instead and it worked.

---

### Post by broggyr on 2007-12-03
I was having problems like this constantly installing Ubuntu 7.10 on my Gateway M675 laptop with 256MB RAM.  I put in another 256MB and the issue went away.

Try installing more RAM if possible.

---

### Post by kernst on 2008-02-29
> **plasma16 said:**
> I'm seeing the same problem on my desktop with my AGP graphics card.
I have three partitions, one ntfs for my winxp, another ext3 and a swap partition.
Ran the Ubuntu 7.10 (not-alternate version) in normal mode, selected Manual mode for partitioning.
Assigned the ext3 partititon to mount / and select to be formatted.
Hangs at "Detecting file system : 15%"
I also tried using ext2, same problem.

I'm trying to download the alternate version and try text-mode install.

There is a slight chance (if you have the same problem I did) that you *may* be able to short-circuit the problem at the 15% mark by looking for a process called '[FONT="monospace"]01unmount_busy[/FONT]' (using 'top' at the command line or *System -> Administration -> System Monitor*) and killing it. Please note that you will have to be root to kill this process (either using 'sudo' at the command line, or 'gksudo' to run the graphical "System Monitor" program [*Alt + F2 -> gksudo gnome-system-monitor -> ENTER*]).

The purpose of [FONT="monospace"]01unmount_busy[/FONT] seems to be to wait for busy filesystems to become free before continuing with the installer, so **please make sure that any mounted filesystems are *definitely* safely unmounted before performing the above action.**

If you see a process in 'top' or "System Monitor" called "01unmount_busy" that seems to be taking more than its fair share of CPU while the installer is stuck at 15%, you can follow the step-by-step I posted at [http://ubuntuforums.org/showthread.php?p=4429985]("http://ubuntuforums.org/showthread.php?p=4429985#post4429985"), which may allow you to progress past that point.

There are several launchpad bugs ([113237]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/113237"),  [112828]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/112828"), and [67723]("https://launchpad.net/ubuntu/+bug/67723"), for instance) tracking this issue, and I've tried to add as much detail to them as I could, so maybe this one will be fixed in the next release.

---

### Post by farrukh_najmi on 2008-03-25
I have the same exact issue. Install hangs at "Detecting file systems" 15%.
I have 192 MB of memory in my old laptop. It seems the problem is related to low memory.
Has any one gotten a workaround for such low memory installs?

---

### Post by Bomberman on 2008-04-21
> **farrukh_najmi said:**
> I have the same exact issue. Install hangs at "Detecting file systems" 15%.
I have 192 MB of memory in my old laptop. It seems the problem is related to low memory.
Has any one gotten a workaround for such low memory installs?
My laptop has 640MB in it and I'm having the same problem. It's not (exclusilvely) a RAM issue. 
Going to try the alt. when it downloads.

Ops, sorry for the old thread kick :)

Worked a treat :) Going well even on this aged thing :)

---

