---
title: "I need to change Processors but keep programs/settings"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by uncr347ivenam3 on 2008-07-04
**To begin with here's my question:**

   I'm getting a new system soon (with a different proc).  I want to keep all my programs and settings from my current install of Hardy (my documents/media are on another drive so I have no worries for them).  When I installed the version of Hardy I'm running now, I didn't bother to put my home directory (~) on a different drive/partition.  I want to know if I just tar my home directory on my current computer and then untar it on my new one (overwrite the one from the fresh install) will that work?  will I end up with errors, etc?  How would I go about backing up and restoring my programs?  Will just moving the current hard drive to the new system work or will a new processor mess stuff up?

**Helpful info:**
[LIST]
[*]I'm comfortable with the command line.
[*]I fond [COLOR="Red"]_[this guide]("http://ubuntuforums.org/showthread.php?t=35087")_[/COLOR] that explained how to back up a system but I don't know if a new proc will mess this up
[*]I'm think I'll be switching to an AMD proc
[*]The upgrade will also include a switch from 256mb of rambus to 768mb ddr (more ddr if I'm lucky)
[/LIST]

**Hardware/Software info:**
```
theodore@trinity:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:02.0 Mass storage controller: Promise Technology, Inc. PDC20268 (Ultra100 TX2) (rev 02)
02:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:06.0 Mass storage controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 04)
theodore@trinity:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 13b1:0020 Linksys 
Bus 001 Device 003: ID 0409:005a NEC Corp. 
Bus 001 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000  
theodore@trinity:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        244          5          0          2         50
-/+ buffers/cache:        191         57
Swap:          666        296        370
theodore@trinity:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 0
model name	: Intel(R) Pentium(R) 4 CPU 1700MHz
stepping	: 10
cpu MHz		: 1693.858
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
bogomips	: 3391.46
clflush size	: 64

theodore@trinity:~$ uname -a
Linux trinity 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
theodore@trinity:~$ df -hiT
Filesystem    Type    Inodes   IUsed   IFree IUse% Mounted on
/dev/sdd6     ext3      885K    214K    672K   25% /
varrun       tmpfs       32K      67     32K    1% /var/run
varlock      tmpfs       32K       1     32K    1% /var/lock
udev         tmpfs       32K    3.0K     29K   10% /dev
devshm       tmpfs       32K       2     32K    1% /dev/shm
lrm          tmpfs       32K      18     32K    1% /lib/modules/2.6.24-16-generic/volatile
/dev/sdd1  fuseblk      558K     48K    510K    9% /media/WinXP
/dev/sde1  fuseblk       62K     13K     49K   21% /media/Media_1
/dev/sda1  fuseblk      1.2M     25K    1.1M    3% /media/Media_2
/dev/sdb1  fuseblk      221K      67    221K    1% /media/Movies_1
/dev/sdc1  fuseblk      405K    1.5K    404K    1% /media/Movies_2
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon      885K    214K    672K   25% /home/theodore/.gvfs
theodore@trinity:~$
```
Software: Ubuntu 8.04 Hardy Heron



Thanks for your help,
Theodore

---

### Post by Zack McCool on 2008-07-04
Chances are, if you just move the hard drive, everything will be fine.

This isn't like Windows.  Linux has no "registry" that maintains a list of drivers and hardware information.  It loads modules as it needs them.

Backing up your home directory to a compressed file is a fine idea, but I wouldn't expect any major issues.  I have performed the same procedure in the past, and never skipped a beat...

---

### Post by Archmage on 2008-07-04
I think the easiest way would be to install the linux-386-kernel for troubleshooting and than insert the old hard-drive into the new PC and boot from it, If this is possible.

Second best solution would be to install Ubuntu on the new PC and than add the old harddrive and than copy the ~-Partition (keep care of the hidden files, too.)

---

### Post by uncr347ivenam3 on 2008-07-04
So the "linux-386-kernel for troubleshooting" would be installable via apt-get?  and I imagine it is a cli tool for getting any problems working I may have with a new proc?

---

### Post by shivam.seth on 2008-07-04
I think that things can get totally messed up for you, no matter what method you try to backup! The reason being that you are moving from Intel to AMD.

Intel basically uses "Little Endian" representation for writing and reading data on a system whereas AMD uses "Big Endian". SO basically a byte which Intel Pentium would read as "12345678" would be read by an AMD proc as "87654321". See, this can totally screw up everything!

This was a question asked to me in one of my interviews, which i couldn't answer n then the interviewer answered it for me, so I know it well. But still i suggest you to check this point. If its true, then you know your answer straight away ---> NO, otherwise ....damn that idiot interviewer!

---

### Post by Archmage on 2008-07-04
> **uncr347ivenam3 said:**
> So the "linux-386-kernel for troubleshooting" would be installable via apt-get? 

This is a kernel that you can install additional that should work on any pc of the latest 15 years. You still might have problems with your grafic-card, but in general you should have a system that would only need adjustment till it is okay.

Since you know the terminal I assume that you can work this small things out.

In case this wont work - do my second option and copy the whole home-partition after you did a new install.

---

### Post by uncr347ivenam3 on 2008-07-05
> **shivam.seth said:**
> I think that things can get totally messed up for you, no matter what method you try to backup! The reason being that you are moving from Intel to AMD.

Intel basically uses "Little Endian" representation for writing and reading data on a system whereas AMD uses "Big Endian". SO basically a byte which Intel Pentium would read as "12345678" would be read by an AMD proc as "87654321". See, this can totally screw up everything!

I just realized I've had similar experience to what I asked about.  I work at _[Free Geek]("http://freegeek.org/")_ where we referb older computers and load them up with Hardy.  The way we do it is we have a system with several removable hdd slots and it performs a network install (we never reboot them on the 'imager' machine).  Then we take the hdds and put them into the systems we build.  On every system I've built, (AMD or Intel) I haven't had any problem with this.  How does this make sense?

Also, would it hurt my install to just put it in the new system and boot up?  Will ubuntu try to fix itself or will it just give an error until it put it back into the old system?

---

### Post by misterbk on 2008-07-05
> **shivam.seth said:**
> I think that things can get totally messed up for you, no matter what method you try to backup! The reason being that you are moving from Intel to AMD.

Intel basically uses "Little Endian" representation for writing and reading data on a system whereas AMD uses "Big Endian". SO basically a byte which Intel Pentium would read as "12345678" would be read by an AMD proc as "87654321". See, this can totally screw up everything!

This was a question asked to me in one of my interviews, which i couldn't answer n then the interviewer answered it for me, so I know it well. But still i suggest you to check this point. If its true, then you know your answer straight away ---> NO, otherwise ....damn that idiot interviewer!

I think you are confused...  I believe I've heard that Apple computers were Big Endian, but AMD and Intel are binary instruction set compatible -with some caveats:-

The kernel installed on the original poster's machine is the generic kernel.  I forget what technology exactly that uses but it's basically the one that's designed to work on anything you could reasonably throw at it without going back to the pre-P3 days.  That means P4 and later, and AMD past either K6-2 or Athlon.

The difference between PC compatible processors is not endian, it is **instruction sets.**  As Intel and AMD develop newer processors, they add new instruction sets for new features they've added.  This has been going on pretty much forever.  At one point you could have a processor with or without an actual floating point unit.  The floating point operations were added on as another set of instructions you could ask the processor to do.

Later on, Intel started adding processor instructions classified as "SIMD" or "Single Instruction Multiple Data".  They called it "SSE" and it was for integer operations, which helped image processing.  AMD was competing at this point and added their own SIMD instructions, instead going for floating point, which was attractive to everybody doing anything in 3D.

Now we have all kinds of instruction sets on all kinds of different processors, going all the way up to SSE4 and honestly getting kind of hard to keep track of.  **The generic kernel ignores all of them** so that it can support almost any chip.  (That's why some people get different kernels and recompile their apps - to make use of those extensions.)

So, if you move your drive AND all of the hardware in the new system is supported by linux, you should be ok but you might have to change some config files if device names changed.  (I had this happen once - my hard drive became 'sda' to linux when it had been 'hda' before, after moving a drive, so I had to boot a liveCD and change some stuff to make linux figure that out.  GRUB especially is susceptible, that's one thing that was broken for me.)

---

### Post by grss1982 on 2008-10-11
Sorry to be bumping this thread, but I was wondering if you change just the processor would there be problems encountered?

My rig currently:

Intel Pentium 4 506, 2.66 Ghz Processor
SL7N73VM Mobo Link: [http://www.inno3d.com/products/motherboard/SL7N73VM.html](http://www.inno3d.com/products/motherboard/SL7N73VM.html)
1GB DDR2-533Mhz
128MB GeForce 6600
80GB Seagate IDE HDD
Ubuntu 8.04.1

I wanted to change my current processor to a spare Intel Pentium 4 HT 630, 3.0 Ghz Processor that I had lying around.

Question: Would this require me to re-install Ubuntu 8.04 or do I just drop in the new processor without any reinstalling done?

---

### Post by gali98 on 2008-10-12
I can't see how there would be that many problems on the software side.
the kernels are pretty generic.
I mean you can't put a 32bit only processor on 64bit OS machine, but besides that it should work.
The only thing I can say is to try it.
Kory

---

### Post by grss1982 on 2008-10-15
> **gali98 said:**
> I can't see how there would be that many problems on the software side.
the kernels are pretty generic.
I mean you can't put a 32bit only processor on 64bit OS machine, but besides that it should work.
The only thing I can say is to try it.
Kory


Oh I see. Thanks, **gali98**. :) Might try this over the weekend. :KS

---

### Post by Frak on 2008-10-15
> **misterbk said:**
> I think you are confused...  I believe I've heard that Apple computers were Big Endian, but AMD and Intel are binary instruction set compatible -with some caveats:-

The kernel installed on the original poster's machine is the generic kernel.  I forget what technology exactly that uses but it's basically the one that's designed to work on anything you could reasonably throw at it without going back to the pre-P3 days.  That means P4 and later, and AMD past either K6-2 or Athlon.

The difference between PC compatible processors is not endian, it is **instruction sets.**  As Intel and AMD develop newer processors, they add new instruction sets for new features they've added.  This has been going on pretty much forever.  At one point you could have a processor with or without an actual floating point unit.  The floating point operations were added on as another set of instructions you could ask the processor to do.

Later on, Intel started adding processor instructions classified as "SIMD" or "Single Instruction Multiple Data".  They called it "SSE" and it was for integer operations, which helped image processing.  AMD was competing at this point and added their own SIMD instructions, instead going for floating point, which was attractive to everybody doing anything in 3D.

Now we have all kinds of instruction sets on all kinds of different processors, going all the way up to SSE4 and honestly getting kind of hard to keep track of.  **The generic kernel ignores all of them** so that it can support almost any chip.  (That's why some people get different kernels and recompile their apps - to make use of those extensions.)

So, if you move your drive AND all of the hardware in the new system is supported by linux, you should be ok but you might have to change some config files if device names changed.  (I had this happen once - my hard drive became 'sda' to linux when it had been 'hda' before, after moving a drive, so I had to boot a liveCD and change some stuff to make linux figure that out.  GRUB especially is susceptible, that's one thing that was broken for me.)
You are correct. IBM/Motorola/Freescale/Apple processors are Big Endian, while all x86 and x86-64 is Little Endian.

Just be aware that an AMD will not fit into an Intel board. (AM2 vs. LGA 775).

---

### Post by sandy8925 on 2008-11-07
> **grss1982 said:**
> Sorry to be bumping this thread, but I was wondering if you change just the processor would there be problems encountered?




Yeah sure you can change the processor. That won't cause any problems in either Ubuntu or Windows.

---

### Post by petermck on 2008-11-07
I've done this several times swapping out Intel for AMD Celeron to Semperon, K7 to Pentium dual core etc always with a new motherboard and had no problems, but here's the things to consider.
[LIST=1]
[*]These have all been headless servers. That is, no keyboard, mouse or monitor.
[*]No graphics are used on these systems.
[*]The generic kernel that comes with the distribution was used, no custom kernels.
[/LIST]
Typical kernels in Debian and Ubuntu are built to handle either AMD or Intel variants and have all the necessary options compiled in to work with either. I think you are very unlikely to have problems if you just change the CPU, but if you change the MB as well and the graphics processor is on board the chance of having problems will be a lot greater, but most likely only with running the desktop. If this happens running dpkg-reconfigure xorg will most likely fix it.
I would backup your data, uninstall any packages you don't want, backup your /etc/X11/xorg.conf file, and just do it! You may be pleasantly suprised at just how robust Ubuntu is.

---

### Post by gali98 on 2008-11-07
Just to clarify... You CANNOT put an AMD processor on an intel motherboard (or vise versa.) They are different slots and the computer would probably not even turn on if you managed to make it fit.
You CAN take a hard drive out of a computer that used an AMD cpu and put it into an intel machine (and vise versa) without problems, as the kernels Ubuntu uses are generic and compiled with generic instruction sets.
Changing Ram would also not affect anything, but you have to have the right kind of ram for your motherboard. Not only is there ddr ddr2 and sdram (as well as others, but they are the most common) but there are classes within those categories as well.
If, like the user above says, you change graphics cards, it would be a smart move to backup your xorg.... In Intrepid it would probably start up in low graphics mode and give you the option of autoconfigureing your xorg (which should work)
Kory

---

