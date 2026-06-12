---
title: "[SOLVED] Can't get server through base install (corrupt file message)"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by chrisofarabia on 2008-10-28
Hi all,

I'm very much a linux newbie, but trying to get there, albeit slowly.

I'm trying to create a standard LAMP server using a 'Hardy Heron' 8.04.1 LTS distro I got from Linuxsales in the UK. This is being installed on an older PC that has recently been given a new mobo (MSI P35 Platinum), a Core 2 Duo 2.4GHz, 2Gb RAM and 2x 320Gb HDDs. The only things retained from the old PC are the case, an LG CD-ROM drive, an LG DVD-ROM drive and a 1.44Mb floppy drive.

On each occasion I've tried to install the system, it's got as far as the base install, but almost immediately, I get "Debootstrap Warning" and a series of corrupt file messages, following which I have to abandon the install.

Since then, I've tried creating a new install CD from the Linuxsales one using InfraRecorder at 8x record speed (MD5 hash checked out OK), with the same result. I've downloaded the ISO from Canonical UK (MD5 hash checked OK), reburnt the CD at 8x with the same result. Now I'm not too sure where to head next.

The CD's I have all check out OK on the pre-install check - none will boot on the CD-ROM, but they all boot without an issue from the DVD-ROM.

I've managed to set up the HDDs as RAID1 with two partitions without too much difficulty, but the base install goes no where.

My only immediate thought is to find a different optical drive to try. Does anyone have any other suggestions?


EDIT: This is a clean build, no dual-boot capability on it.

---

### Post by chrisofarabia on 2008-10-28
A few more things tried, but not exactly what you'd call progress. Seems both optical drives had been jumpered on their 'cable select' pins on one IDE ribbon cable. Switched those back across to Master/Slave, with the DVD drive as the Master. Still nothing changed, as soon as it reaches install base system, it heads off into the 'Debootstrap Warning'. Tried switching the boot sequence onto the CD-R/RW drive, but that continues to ignore the install disk altogether.

Have now disconnected the CD-R/RW drive completely and will try with just the DVD connected.

---

### Post by chrisofarabia on 2008-10-28
No joy...

Apropos of nothing, the first file that fails comes up with the following:

**Warning: file:///cdrom/pool/main/c/coreutils/coreutiles_6.10-3ubuntu2_i386.deb was corrupt**

Any suggestions?

---

### Post by chrisofarabia on 2008-10-28
For my next trick, I tried running the desktop 'live' demo, which came up a treat on first time of asking. After a few runs round the demo to see what's what, I hit the install option. This went through so far until it got to the partitioner, at which point I'm being told that the '/' partition is too small - now I know when I was messing with the server version, I'd set that at 10Gb and left the rest of the disk space (about 298Gb) set as the 'swap area'. Anyway to cut a long one short, I then used on of the guided options to sort out the partitions and everything installed, though I think on only one of the HDDs, not the full RAID1 set. Got to the re-start, but it didn't come back up. Seems that the BIOS is still detecting the RAID, and probably not the single disk install it probably now has. But at least I've now actually seen ubuntu running...

More tomorrow I think, it's now late here. Night all...

---

### Post by chrisofarabia on 2008-10-29
I keep hoping someone might be able to chip in and suggest something - any takers?

---

### Post by superboss on 2008-10-30
I dont have a solution but I do have the same problem... I've tried multiple different locations for the iso, checked the MD5 on all of them and they check out OK, used two different burners, used 2 different CD-R discs and 2 different CD-RW discs... still no joy! I have the same problem with 8.04.1 Server and 8.10 Server. I have no idea what is happening but its quite discouraging to see these errors when I'm sure potentional newcomers will stay well away if they experience the same problems.

---

### Post by chrisofarabia on 2008-11-02
I can understand the discouragement and share your frustration. I think I can add a little more to the picture now though that may be of some assistance. Today I got hold of a new new SATA DVD Writer (Samsung Super-Writemaster BG69-00687A) and have just installed the same. In the process of trying to get it set up as the boot device, I noticed that none of the SATA devices were showing up in BIOS and as a result couldn't select the new DVDW to boot from. 

I eventually discovered that the BIOS has a RAID setting built in and this was enabled. After resetting to IDE and re-booting, all SATA devices now show in the BIOS and can be selected as boot devices, including the HDDs which hadn't been apparent in the selection options before, only a RAID option.

I think I'm concluding that using the BIOS based RAID conflicts with the software RAID that Ubuntu is trying to set up. I'm now going to try setting up the software RAID again to see if the install will run through, though I still think I need more information on an appropriate partition order for a LAMP server.

I will be back... [-o<

---

### Post by chrisofarabia on 2008-11-06
Well I'm pretty sure the analysis in post #7 describes what was causing the problem.

Sorted the partitioning question as per this thread --> [Partitioning Schema for LAMP Server]("http://ubuntuforums.org/showthread.php?t=967875")

The basic install eventually went on very easily and I'm now adding a few bits I want before finishing off the configuration I want.

---

