---
title: "Unable to set RAID or SAMBA on U 14.04 system"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by PatMcSwain on 2015-01-03
I'm upgrading a small file server for 2015.

Existing working system is 12.04 Desktop with SAMBA, no RAID.  One drive is OS, second drive is shared files.  System has worked flawlessly for 2 years.

So I removed the 2 120gb drives and replaced with 3 240gb drives, and am trying to install 14.04.

Goal is to have 1 drive as OS, not shared.  2 drives as RAID1, shared with 10 Windows machines.

I can install either 14.04 Server or 14.04 Desktop with no issues at all.

When I install 14.04 Desktop, SAMBA will not install, "waiting to install - freeze".  No ability to set the 2 data drives into software RAID1 either.  Can't find any useful disk management functions.

When I install 14.04 Server, I select the SAMBA install, can't find the RAID options, then I must put a desktop on it, since I'm terrible at CLI.  I use the sudo apt-get --no-install-recommends ubuntu-desktop command to put a desktop on it.

At that point I'm dead in the water.  Can't RAID, can't launch SAMBA, etc.

All the tutorials and threads I've read fail one way or another.  Mostly because they are aimed at setting RAID as the boot volume, or they assume SAMBA will actually install in 14.04 desktop.

Realistically, should I just give up and stick with 12.04?  Or am I just not finding the right tutorial?  Can I use 14.04 as a Windows fileserver without SAMBA?

(Cliff Notes:  Want to set up 14.04 with SAMBA and RAID1.  Hardware is proven.)

---

### Post by PatMcSwain on 2015-01-03
OK, gave up on RAID for now.
Did get SAMBA to install and work:

1)  Install 14.04 Desktop.
2) Don't try to install SAMBA directly.
3)  Right click the data area, and share.
4)  It will tell you that you must install software.  Answer yes and give password.
5)  It will lock up during this, and not allow you to hit install on a second window.  This is ok.
6)  Wait a few minutes and reboot.
7)  Now SAMBA will work.  There is nothing really wrong, it just doesn't handle install messages correctly.

Note:  If you don't have a dedicated video card, or fast on-board graphics, DO NOT install 14.04 desktop.  It redefines slow to a new level.  12.04 is slow, but 14.04 is completely unusable.  It takes 2 seconds to respond to each keystroke, or mouse action.  It is so slow that you cannot type or use the mouse for GUI activity.
In my case, I installed a small video card so I could work with the computer.

If I figure out how to RAID 1 the additional data drives, I will post it up.

---

### Post by MAFoElffen on 2015-01-03
My prefrence for that would be Server Edition-- but with either:

That should have been something you planned beforehand in the install...
- In the partitioner, select manual
- Partition the first disk with root partiton and a swap
- Partition all of the second and third disk... at this time, select mount as / "do not use"
- Once the partitioner sees unused partitions, two other option will appear/add to the partitioner's menu: LVM & mdadm
- Select mdadm > type > select sdb and sda as members (no spares)... finsh the options and write
- Back in the pariitioner, select the md0 logical disk and partition > use as /home
-- Finish and finish install

Otherwise, Linux Software RAID is mostly commandline, even if you have Desktop installed. I'm nowhere near releasing a working version of mdadm-GUI yet.

So install mdadm: 
```

sudo apt-get update && sudo apt-get install mdadm

```
use fdisk to partition both the disks with a type code of "fd", which is a linux_member.
```

sudo fdisk /dev/sdb
sudo fdisk /dev/sdc

```
To initialize to RAID (Set/Zero the superblocks on the drives):
```

sudo mdadm --zero-superblock /dev/sdc /dev/sdd

```
Create RAID1 using /dev/sdb1 and /dev/sddc
```

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```
It will take a while to create and assemble the first time. You can check progress via
```

sudo watch -n 2 cat /proc/mdstat
# OR
sudo tail -f /proc/mdstat

```
...When it finishes, at that point you can partition and add a filesystem... or just add a filesystem directly to the RAID container.
...then add the UUID of the filesytem to the fstab to mount the filesystem at boot.

Install Samba and when you configure the samba config file, add your directory to the end of that file. 

***It doesn't have to be mounted as /home. It could be /Export or any other name your predetermine.

---

### Post by PatMcSwain on 2015-01-04
Thanks!

I'll try that method.

My problem is that using a Ubuntu fileserver is so trouble-free, that I don't get a lot of seat time with Linux.  I learn just enough CLI to get the necessary task done, which happens rarely. 

What has always amazed me, is that Linux is better at talking to Windows machines than other Windows machines are.

---

### Post by MAFoElffen on 2015-01-04
LOL. Yes... just talking SMB. 

Currently, I feel old. I'm going back to school and collecting degrees and certs to document my skills. I have an advantage over new students in that I've done UNIX, then Linux since 1988... but I have to convert my understanding of Win OS'es from Linux to Win. Seems Win is still behind in some ways, trying to catch up on filesystems, LVM and software RAID. I know how it works from that translation. What gets me is the where things are located inside WIN OS and their specific terminology.

I noticed that in your planned server layout... Win OS'es need to boot from a primary, normal, active volume = cannot be RAID nor LVM, because their own system needs to be running to translate it, before it can use it. Linux can boot from inside a RAID and/or LVM Volume, because the Boot Manager (Grub2) knows how to figure that out... You can run your a Linux root from a software RAID volume... Win hasn't figured out how to do that yet. Meaning, your business plan could look into adding another disk, to run 2 RAID 1 volumes, one for root and one for your SMB share and be more secure. Server services priority is "uptime" and reliability. But remember that RAID is not a replacement for backups.

Since I'm spoiled by having experience with X since '88, I have my servers installed with a minimum install of XServer. I have them setup to boot to a TTY console, but X is available there to be able to start an X Session (GUI) instance for admin. After through with what I need to do, exit goes back to console. What M$ now teaches with their own WIN Server is that management is easier with a GUI, but that Core (console) is more secure... So falls into that same methodology. Free the resources for server, where the processes should be prioritized to server services, not to the GUI foreground processes.

EDIT-- (another note) Commercial (business), recommend that you put that on a UPS. With battery backed hardware raid, you get a little more safety with your write cache. Most software RAID failures occur with a power failure, when it doesn't have a chance to commit changes and sync the array... close gracefully, before shutdown. That will save you in the what-if.

---

### Post by PatMcSwain on 2015-01-04
The problem I've always had with Win as a fileserver has been Excel.

After 20+ years, Excel is still a poorly behaved application.  It still has memory leaks, still hates removable media, and still has issues with closing files correctly.

I used to have to unlock files, or rename files almost daily.  I had to reboot the fileserver about once a week. This is with only 6-8 workers using Excel.

Then 4 years ago, I set up a Ubuntu fileserver (10.04), and the problems nearly vanished overnight.  Maybe once a month I'd have to unlock a file or rename one, and NEVER had to reboot the fileserver, ever.

Ubuntu cuts my babysitting time to virtually nothing.  It's so nice not to even think of the fileserver.  But I still have monkey with the client Windows machines on a regular basis.  Sadly, they run machine controller cards and special software that won't run under WINE, or I'd switch in a heartbeat.

---

### Post by MAFoElffen on 2015-01-04
> **PatMcSwain said:**
> Sadly, they run machine controller cards and special software that won't run under WINE, or I'd switch in a heartbeat.
Now you've caught my attention. You have my curiosity! I like a challenge. Especially when it is getting WIN and Linux coexisting seamlessly... 

What controller cards and software are they using pray-tell?

---

### Post by PatMcSwain on 2015-01-04
They run Coordinate Measuring Machines, aka CMM's.  These are high accuracy measuring machines, with resolutions of up to 0.00025 mm.  Most are Direct Computer Control (DCC) which means they are robotic in nature, like a CNC milling machine, but more complex.

Some run Heidenheim? X,Y,Z controllers, some run GPIB controllers, and others run USB or COM communications with special drivers that relay X, Y, Z coordinates and movement information.

They also have Sentinel security dongles, and one has a Matrox? frame grabber for video inspection.

There is no interest at all from the CMM manufacturers to code for anything but DOS/Windows.  Yes, 2 of the machines still run MSDOS, and a lot of the code in the Windows versions is mearly DOS apps hidden by a GUI.

AFAIK, the CMM mfr's don't acknowledge Apple exists, nor 64-bit operating systems.  Some of my new machines must run 32-bit Win.  Their re-calibration software is still DOS and runs from a 3.5" floppy.  

It is unlikely there is any market for running CMM's on Linux.  Any changes to the computer or operating system (Windows OS updates included) voids the warranty, and can stop you from getting the machine serviced.

That being said, I'm willing to experiment.  It's just that I'm not your typical CMM owner.  I repair my own machines, and have done "the impossible" many times in the past.  The MFR will say something can't be done, and I prove them wrong.

---

### Post by MAFoElffen on 2015-01-04
Am familiar with CNC, CAD to CAM, G and M codes... I do woodworking and am a Moderator of a Woodworking Forum that includes a CNC section.

---

### Post by PatMcSwain on 2015-01-04
Unlike CNC machines, CMM's don't have an ASCII communication language (GCODE) that is transmitted between the machine and the PC.  It's all binary in a proprietary format for each CMM MFR, and often CMM model specific.
Attempts at making a universal language failed.  It's called DMIS, and never took off like GCODE, HPGL, Gerber, DXF, IGES, etc, did.  

This has always been a problem in the CMM industry.  While you can write a routine to edit the gcode so it can be transported to another CNC controller, it's tough with CMMs so far, since the data stream going into the machine is binary, and not publically documented.  Only CMM Manager software has made a serious attempt at talking to more than one brand of CMM.

---

