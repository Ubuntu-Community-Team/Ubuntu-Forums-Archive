---
title: "Need help on RAID for high availability on SOHO network"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by lcason on 2008-03-23
**QUESTIONS**
1. Is it feasible to run everything on a single RAID1 disk, such that if either spindle fails, the machine is still bootable without loss of data?
2. If yes, is there a verified "recipe" for cooking this up somewhere that someone can point me to? I've found many recipe ideas from other distros, TLDP, old versions of Ubuntu, Debian docs, etc., but while gettting ideas and mixing them may work OK for cooking a meal, it isn't working very well for me on getting this RAID1 config done. 

I'm looking for some helpful suggestions on setting up NAS for family network that also supports work-at-home use. I looked fondly at FreeNAS and OpenFiler, but don't want to dedicate the box to just NAS, and figure that SAMBA on Ubuntu will meet my requirements. If I had the cash to lay out on a "turn key" solution, I'd probably buy the NETGEAR ReadyNAS appliance and be done with it--but I don't, so I'm looking to build my own solution.

BACKGROUND
I am the household "sysadmin", with one WinDoze workstation, and one Linux machine I've been using as a workstation and server. There are several other WinDoze machines and a Mac on the home network, that I'd eventually like to provide NAS to. I would like to run RAID5 with spares so that I can procrastinate for a while before fixing a failed drive, but without buying a new box it looks like I'll have to make do with two drives and RAID1. If RAID1 performance is really poor, I can add a third drive to stripe RAID5. 

CURRENT ODD "BUG"
I've been in a loop on software RAID configuration on my Linux box for many hours now. I got as far as having RAID1 between the two PATA disks synching, but here's an odd thing: I open up a terminal an run the following command: ```
 sudo mdadm --query --detail /dev/mdo 
``` 

The first few times I run this, all looks well. The HD LEDs are blinking happily in unison, and the synchronization percentage is gradually increasing as I run the query at later times. All is well until the sudo authorization has timed out and I get prompted for my password--then the system hangs and only a hard reset will recover it.  I've reproduced this behavior several times. Not so much because I'm a glutton for punishment, but because I changed other things and thought that finally everything would be working fine. But like the doctor says, "if it hurts when you do that, then don't do that" so I'm letting the synch run untouched until it finishes. Oops, it just finished (blinking lights stopped) but the console is hung--this time without my touching anything.  Sigh..  Must be a config problem, as this same hardware has been running Gutsy with no issues for the last several months.

MY SERVER HARDWARE
CPU: Intel 3 Ghz P4
Motherboard: Intel® Desktop Board D875PBZ  [http://www.intel.com/design/motherbd/bz/index.htm](http://www.intel.com/design/motherbd/bz/index.htm) 
RAM: 4 GB
PATA Controller 1: WD 120 GB  7.2K drive as master
PATA Controller 2: SONY 52X CD-ROM Drive as master; WD 120 GB  7.2K drive as slave



NEXT STEPS IN MIND
Option 1. If I can't get software RAID to work right, purchase a real hardware RAID controller (no FakeRaid), but I suspect it would make sense to go with SATA, rather than PATA (near end of life?), which would require that I change out the HDs and the removable HD caddies. I've seen some nice SATA backplanes that hold 4 drives that are supposed to fit in the space for three drive bay slots, but that sounds like a knuckle buster that I'd like to avoid if possible.

Option 2. Load OpenFiler and build another Linux workstation. Except I tried loading OpenFiler, which is a CentOS appliance, which uses RedHat (like?) tools that I also had issues with when trying to configure RAID1--so even if I was willing to dedicate the box to a NAS server, I may still have hardware config issues to resolve.

Thoughts?

---

