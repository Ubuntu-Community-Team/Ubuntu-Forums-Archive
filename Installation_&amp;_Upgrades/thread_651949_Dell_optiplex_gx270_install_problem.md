---
title: "Dell optiplex gx270 install problem"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by devoncatt on 2007-12-28
This is a general install question . I have installed all versions of linux on many generic home brew computers in the past with a few minor problems. I can not get the live cd to work on this Dell optiplex gx270 . I have had the same problem with an older IBM computer at work as well. THe linuxes seem to fail at the hardware detect portion of boot. Any suggestions? Umbutu 7.10 just hangs after the choice of live/install or safe graphics mode. I got an old computer for a friend and tried to give them something other than windows.
devoncatt

---

### Post by Pumalite on 2007-12-28
Memory, graphics?

---

### Post by Pumalite on 2007-12-28
I think you have integrated graphics, so better go for the Alternate CD.

---

### Post by devoncatt on 2007-12-31
I am downloading the alternate cd I am just wondering why buit-lin graohics fouls up linux live cd's so much? Isn't it common enough that it is part of a live cd? If it is builtin doesn't that pretty much limit it to ATI, Nvidia or Intel graphics? Just curious at this point. 
devoncatt

---

### Post by Pumalite on 2007-12-31
They are the ones supporting Linux ( ATI only lately)

---

### Post by sirspiddy on 2007-12-31
I had this same issue with several gx270's at work trying to install 7.10 but no issues when I installed 6.06.  After much reading I learned that the stock gxw270's did not have enough ram to support the liveCD and that the alternate CD was recommended.  I was able to install using the curses based alternate CD, however after a successful install the desktop was rather slow to use even with compiz turned off.  Some machine I migrated back to 6.06 and others I  upgraded the ram.

---

### Post by Pumalite on 2007-12-31
256 MB of RAM or less> Xubuntu Alternate CD:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Or:
7.10 Xubuntu Alternate CD (consumes more memory)

---

### Post by devoncatt on 2007-12-31
I have tried the alternate cd no luck, nothing seems to install on this machine. I have tried ubuntu,fedora core 8 , linux mint, windows XP - they all fail. Any suggestions?
Devoncatt

---

### Post by Pumalite on 2007-12-31
Did you try Xubuntu Alternate CD?

---

### Post by bsmith1051 on 2008-01-01
it fails on ANY OS?  sounds like a hardware prob, e.g. bad CD drive.

---

### Post by K.Mandla on 2008-01-01
+1. If it's failing at every opportunity, then there's something else going on. See if you can change to a different CD drive.

---

### Post by devoncatt on 2008-01-02
It gets to the reboot in windows XP so it writes to the disk ( but then doesnot see the cdrom) 
It halts at trying to install any version of linux.

I am wondering is it something unususal on motherboard ( I.e jumper that needs to be reset?)
or is the in board graphics weird so that it is not recognized by linux
I had asimilar problem with linux and another old dell desktop- in graphics - it could never stablize the video.

On this one I set the video to 8 mb in the bios- it uses system memory to run the video.

Another possible thought could it be a non standardl  ide controller?

The first choice for boot disks seems to poll the sata controller not the ide.

Would irqpoll at the startup help? or something else?


Devoncatt:confused:

---

### Post by Pumalite on 2008-01-02
Hardware problem. Check everything. Change parts or the computer.

---

### Post by devoncatt on 2008-01-04
I installed a new agp video card , an older ATI. Windows XP was also freezing the install at devices. I know this model has a history  leaky  capicitors. Windows XP is now going further. Why won't umbuntu in the alternate install or the standard dvd install or even boot. It is a generic linux problem because Fedora 8 also ghangs after loading the kernel as well.In Umbuntu all I get is a blank screen with sometimes a cursor.
What does Dell install that Linux can't deal with???

Devoncatt:confused:

---

### Post by torgrot on 2008-01-04
I have a gx270 sitting on my desk now.  It has 1.5gb of ram though.  I have run ubuntu in the past on it and just now tried the live CD and it works just fine.  I know I have been through several CD-Rom drives on this box, for some reason they just don't last.  Replace the CDRom drive and try again.  Do you have more than one hard disk?  My box has two sata drives and  Ubuntu had some problems sorting out the drives.

torgrot

---

### Post by devoncatt on 2008-01-07
The GX270 I have has 512 MB of memory - which should be plenty of memory for Ubuntu or some other linux. I have set the video memory to 8MB in the BIOS. I have tried three different PATA drives. Including a cloned disk  of a GX290 which has consistently worked in most other dells in the past.
Exactally how much memory does Gutsy's Live require?
In the Past with Feisty betas I had to enter certain options on booting the live disk to actually make it boot on my generic machine ( Intel Core Duo, 2 GB memory with an ASUS motherboard).
Is that needed in Gutsy?
 Do I need options such as  irqpollor no apic or no lapic ? What do they actually do?

Or do I need to dump the gx270 ?
The Bios is AO4

Devoncatt

---

### Post by bsmith1051 on 2008-01-09
> **devoncatt said:**
> do I need to dump the gx270 ?  The Bios is AO4
The most recent (final?) BIOS rev is A07.

Have you tried a new CD *drive* ?  That's what sounds flaky, not the hard drive.

---

### Post by devoncatt on 2008-01-14
It turned out to be a hardware issue.  I got a replacement machine and the install proceeded with no problems. This model is known to have leaky capacitors and other hardware problems.
Not easy to diagnose because it doesn't install and thus no   log.

Devoncatt

---

### Post by bsmith1051 on 2008-01-15
of course!  How could I have failed to mention that??  Sorry... 

I've got dozens of these machines in my office (had, actually) and they *ALL* needed a new motherboard, even the ones that didn't outright blow their caps.

---

