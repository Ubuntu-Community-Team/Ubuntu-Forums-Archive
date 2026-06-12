---
title: "Install makes disks unuseable"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by TiberiusT on 2011-01-23
Gd day all,

Been trying for 1 day to install Edubuntu 10.10 on my kids Core2 which has run Win7 wout problems for abt 6 months. I am getting nowhere...tried everything - diff install methods, reburnt DVDs. In desperation I stripped the PC down to nothing - took out RAID disks and left only one SATA 80GB only. Tried to install using that setup but it trashed the disk - even BIOS does not recognise it. Seemed to install OK but at the end reported multiple i/o errors and wouldn't reboot.

Thinking disk was coincidentally knackered I replaced it with an old ATA 500GB and tried again (think 10th attempt). Install took abt 45 mins and now I have the same result - the 500GB is also trashed. I cannot reinstall Win7 on it because even BIOS does not recognise the disk.

PC: P5N-E-SLI, (Nvidia 680 chipset), Core2Duo at 2.0, BIOS defaults. Mobo checks out as Linux OK.

I have now loaded from CD. Disk utility reports no disks. How do I recover the disks and find a way for Ubuntu to install on a disk? 

I originally started this because Ubuntu said dual boot system was safe. I have now wiped out the Win7 installation, and seem to have 2 x dead disks. Safe? What is 'unsafe' then? 

Doan wanna give up! Any assistance hugely appreciated. N00b on Linux, stacks of PC experience though..
tks in advance
T

---

### Post by oldfred on 2011-01-23
RAID used to require the server install or the command line installer, not the liveCD. They may have updated installed to see RAID, but the special drivers were not in the standard desktop as that is uncommon. 

Some have had issues with DVDs. CDs seem to work better or use flash drive. Always burn CD at slowest speed drive will allow and run the verify CD on first boot of CD. Also check that CD works as liveCD and that your systems works from the liveCD.

Some systems require BIOS settings to be changed.

If hard drive still has RAID metadata on it, that will often prevent install.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

[https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to laod the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by TiberiusT on 2011-01-23
@oldfred

Tks very much for the detailed response. Lots of stuff to work thru there. 
Even though I never tried to insall to the SATAs (they are just used to backup the network I have at home) maybe their settings interfered somehow. I'll run thru those BIOS settings yu suggest and give it another go. I did try 4 separate versions: Edubuntu 10.10 32 and x64, Ubuntu 10.10 x64 (same install disk which has worked on my machine all this week) and a new 11.04 trial of Edubuntu....in that order. 
After calming down a bit now :p , it seems it must be a BIOS setting issue. BUT the problem is that the consequences of getting it wrong seem dire! It's 'Goodbye HardDrive'!
Never ever experienced that with a harddrive b4 - I'll do some serious googling on what to do with them.

tks again. I'll report back soon

T

---

### Post by Quackers on 2011-01-23
Be aware! If you are using raid0 (a striped array) and you reset bios to non-raid you will lose Windows! It would need to be re-installed.
If you are using raid1, you may be ok.

---

### Post by dino99 on 2011-01-23
The best solution is to boot whith a third app like partedmagic, then make partitioning as needed. Small howto below:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note: as previously you had raid installed, you need first (before formatting) to remove dmraid as explained by oldfred in the post above.

---

### Post by TiberiusT on 2011-01-23
Tks Quackers and Dino99. 

I'll give PartedMagic a go and see if i can recover the 2 disks.

I never tried to install to the Raid0 system. The PC had 3 disks originally. 1 x SATA 80GB which had Win7 and all data on it, and 2x1.5TBs in RAID0 which were just used as backup for other PCs on the network. I tried first to install to a partition on the 80GB, but that didn't work, so I sacrificed Win7 and tried an entire disk install, again on the 80GB. The install completed but didn't boot. On 2nd attempt I ended up with a unuseable disk. I assumed it was somehow on it's way out anyway (it's very old) since I've never comes across an OS install trashing a disk.

I then put in another disk from another machine I had - an IDE ATA 500GB and tried Ubuntu 10.10 x64 from the install DVD as I had used on my PC this week which worked fine. Sorted...I thought.... It installed and it kind of ran, very unhappily, but after abt 10 mins use crashed and wouldn't boot again. I then tried other versions (Edubuntu 10.10 x64, 11.04) and ended up with a trashed 500GB ATA as well. Every single install has shown some sort of problem dealing with the hard drives - it's never been happy.

I am a bit reticent to try again (just found a very old Maxtor 40B in my parts bin  though which is def expendable :p) since it seems this is dangerous procedure.

T

---

### Post by TiberiusT on 2011-01-23
just an update...

I thought PartedMagic might bypass the BIOS somehow but it also denies existence of either the 500GB ATA or the 80GB SATA when I put them in individually. BIOS sees them, but reports them as 0 data bytes available. And yes...they are def connected correctly - been building my own PCs for 20 years!
Seems they're both bricked.

The more I use my addled nonce, the more it appears that this must be a BIOS problem with the machine, which evidently never affected Windows (which I think doesn't use the BIOS to interface to the disks...does Ubuntu?). No one else has ever reported this problem (I've searched a lot) and I simply can't believe that Ubuntu goes around trashing disks without a very good reason. Also, that Nvidia
NForce 680i chipset has always been a bit dodgy (used it for 4 years now).

Tomo I'll get a USB edition running to keep the kids happy. Been the whole weekend at this - can't even look at the damn thing anymore ;) When i get some enthusiasm back I'll flash the BIOS and try again with that Maxtor. Computers must never be allowed to win.

T

---

### Post by TiberiusT on 2011-01-30
Ubuntu on Asus P5N-E SLI Nforce 680i Chipset. Just to finish the thread for other suffering NForce users... 

One week later... given up. Upgraded BIOS to 1406. Tried again with 10.04 LTS x64. It installed on a USB drive but ran very very slowly. Tried another HD install and it did install this time, but still ran very slowly. At one point, when booting up (takes abt 5 mins) I saw a message flash up which said something like :

"NForce - smbus1 problem probing SMB1" or something similar to that. 

That is enough to convince me that the NForce chipset is causing all these problems. Not least because I used same install disk on my Foxconn BloodRage GTI without any probs.

I'm going Linux and nothing's gonna stop me. Will buy a new mobo this week.

T

---

### Post by dino99 on 2011-01-30
you are not alone with this issue, but a patch exist:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296)

if you still want a new board, forget about foxconn (not the best, even asrock is better, by far)

---

### Post by TiberiusT on 2011-01-30
Thanks a lot Dino99. Quickly reading thru those bug reports it's not clear whether it has been fixed or not. I'll give it some more time tomo.

OT My personal experience with Foxconn is different. My i7 920 has been running at 3.80 GHz for one year on air in a cheap steel case wout any problem. I encode videos, often it's at 95pct CPU use for 72hrs. Took 30 mins to OC and it's been abs faultless. Anyway, they've stopped making them:( and my cheap mobo days are finished...

T

---

### Post by TiberiusT on 2011-02-21
Well, I solved it in the end. Not very pro though. I spent another week trying to get Ubuntu to work on the Asus P5N-E SLI Nforce 680i. It wouldn't. So, I bought a cheap Gigabyte G31 mobo, swapped ALL the components from the Asus and...perfect installs followed. I've now tried 4 different flavours (same CDs as b4) and not one time did I have one single problem. The SATA 80GB is working again, the 500GB ATA appears to be dead. 

Whatever the problem was, the time spent trying to figure it out was worth much more than the 40 Euros that the new mobo cost. Goodbye Nforce....other Owners say they have no problems...whatever...

As an aside on the new machine with a Core2Duo E4400 at 2.0Ghz, single SATA 80GB, Win 7 Pro x32 boot time is 1m 10secs. Ubuntu Maverick x32 is 45 secs, seriously beautiful to use, and the abundance of free educational software for kids is fantastic. 

It's been worth it :D

T

---

### Post by Quackers on 2011-02-21
Glad to hear you got things running :-)

---

