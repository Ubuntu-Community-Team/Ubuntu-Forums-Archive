---
title: "Unable to boot/install"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by vitaminz on 2006-10-04
Hi, I've recently attempted to install Ubuntu again, after installing it on VirtualPC in college and realising how amazing it is. I burnt the desktop-i1386, seeing as I have a 32bit Intel Celeron 2.2ghz CPU. However, after the Ubuntu loading screen, an error message comes up (On a black screen with white text)

It says

[17179711.650000] Buffer I/O Error on device hdd, logical block 23711.

After 5 seconds, the same error appears below the existing one, with the numbers different (The first few numbers seem to randomly change, and the logical block number increments by 1)

I've tried the CD in both my CD-RW drive and DVD-ROM drive, but I get the same errors.


Also, I have 512mb so that shouldn't be an issue.

Any ideas? Thanks.

---

### Post by whizbaby on 2006-10-04
I guess: CD broken (hdd is the fourth ide drive, is this your cd drive?).
Re-burn it at slow speed or try the *alternate install cd*.

---

### Post by vitaminz on 2006-10-04
Hi, I think it is, yeah. Here's the drives on my system (If you can tell from the drive letters that is)

A:\ Floppy Drive

C:\ Local Disk (Windows partition)

D:\ Virtual drive made with Daemon Tools

E:\ (Partition of my HD. Same physical hard drive as C:\)

F:\ Ubuntu (The partition I want to install Ubuntu on)

G:\ DVD Drive

H:\ CD-RW Drive

I:\ Another virtual drive made with Daemon Tools

I've burnt at a very low speed, and I'm about to try it. I'll post with the result.

---

### Post by n3r0 on 2006-10-04
Sounds like your HDD is bad. Did you try running ' chkdsk DRIVELETTER: /f ' on those partitions in windows?

On the ubuntu cd you can "check media" or some such option as well, to eliminate the cd being bad.

---

### Post by dannyboy79 on 2006-10-04
dude, if you want to be safe, i would unhook all hdd's that you won't be using to install ubuntu. in other words, i would disable the virtual drive in windows first, then i would shut down. then unhook all hdd;s except the one that you're installed ubuntu on. then go from there. that's what I did as I didn't want to accidentally over write all my stuff on my windows drive.

---

### Post by whizbaby on 2006-10-04
> **dannyboy79 said:**
> then unhook all hdd;s except the one that you're installed ubuntu on. then go from there.
How would grub install correctly in the MBR of the first HD if it isn't connected?

---

### Post by dannyboy79 on 2006-10-04
the hard drive being called hdd is most likely your windows drive, it goes by ide channels. so you'd have to tell us what's hooked up to what for us to be able to tell you which drive is being called 'hdd'. so, ide0 channel, master drive would be hda and slave on ide0 would be hdb. then ide1 master is hdc, and ide1 slave is hdd. if it is your windows drive, the soonest you can, i would replace it. these errors a re a sure sign that it going dead. why don't you get a program to check it's integrity. i think i downloaded something from seagate and was able to run it by booting to a floppy that had the program on it. i found the drive to be dying.

---

### Post by whizbaby on 2006-10-04
> **dannyboy79 said:**
> the hard drive being called hdd is most likely your windows drive
Concluded from what? hdd is most likely to be one of the CD/DVD drives. (second IDE bus, second drive). Windows is most likely to be installed to the first IDE master (hda).

---

### Post by vitaminz on 2006-10-04
Thanks for the replies guys, I burnt it at a low speed and it works perfect now :)

---

### Post by whizbaby on 2006-10-04
> **vitaminz said:**
> I burnt it at a low speed and it works perfect now 
CDwriters don't seem to get any better these days...
:-\"

---

