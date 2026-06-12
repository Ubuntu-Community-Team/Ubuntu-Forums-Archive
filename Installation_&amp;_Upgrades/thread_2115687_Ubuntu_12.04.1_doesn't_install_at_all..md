---
title: "Ubuntu 12.04.1 doesn't install at all."
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by viriatovigo on 2013-02-13
I’ve been for 5 days installing and uninstalling Ubuntu 12.04.1 and I going crazy. I am close to get another stroke. I had before Ubuntu 11.10 without problems but is uninstalled because, again, Ubuntu 12.04.1 used to get frozen half way of the upgrade.

Because I can not install it 100% ever.

I do install it from the CD: Not problem.

I reboot the PC with the CD on the drive: Not problem.

Ubuntu opens and do start to install: Not problem.

But then, when starts to copy the files… End of the road. 

Every time, any time it stops half way and I can do nothing because nothing responds.  T-h-e   i-n-s-t-a-l-l-a-t-i-o-n  g-e-t-s   f-r-o-z-e-n.

I would appreciate if someone can advise me about how to resolve this issue.

With thanks in advance for your kindness.

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by goldshirt9 on 2013-02-13
try burning the cd at a slower speed or install from usb stick ?

---

### Post by viriatovigo on 2013-02-13
Ta ahallubuntu

Nop! The RAM is OK and the drive is also OK.

Sorry, I am not too clever, my IT background is on IBM 3060 30 Mainframe (in 1975) and I've got lost for awhile on this new "toasters", but I don't get if it is working perfectly until do starts to copy the files **already** installed without problems, What has to do with the RAM? Mind that image has been loaded in the external HD from the Ubuntu CD -that I've got downloaded from Ubuntu- and it is a 1Tb HD.

---

### Post by viriatovigo on 2013-02-13
Ta Goldshirt9.

The CD it is already burned with the image able to reboot since I did install 12.04.1 the first time from it.

I don't know if I did explain me right, but the problem is when  Ubuntu starts to copy the files **already** installed.

---

### Post by Bashing-om on 2013-02-13
viriatovigo; Hi !

Regretful that you are experiencing such difficulties. Let's clean the slate a bit and establish a working foundation:
1. msdos (MBR) partitioning ? -> Max of four partitions per disk. ( a Biggy)
or are we looking at GPT partitioning 
2. Is ubuntu the sole system or are you dual booting ?
3. How old is the box -> is UEFI or smart response a factor ?
4. Does your cpu support pae


I understand that the liveCD boots up with no problems. This leads me to consider there is a disk format issue ?

Then I suggest -once conditions are known- to use GParted (if msdos partitioning) to delete current partitions, make a new partition table for the disk and then (re)install.
[INDENT]willing to help

[/INDENT]

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by viriatovigo on 2013-02-14
Good morning folks.

Sorry, but all your advise didn’t work (or more precise “I didn’t apply it properly”). For instance ctrl+alt+t doesn’t open the “terminal” at all.

Finally, in the 47th time of uninstalling and installing, Ubuntu 12.04.1 went fully through without me doing anything different to the other times.

It took to install it… **8 hours!!!** After that it notified me that where 331 updates to install. I did click on “install” and… **Took another 4 hours!!!**

But… (there is always a “but”) it is not working properly. **It takes about 15 minutes to open anything** and the menu bar is empty. In Ubuntu 11.10 in the left of the menu bar was a commands to open “file, etc.”, and in the right the icons for the keyboard, mail, bluethooth,…”. In Ubuntu 12.04.1 there is **nothing**. And in the tools bar also there are a lot less icons, for instance, all the HD connected into the PC, that were shown on Ubuntu 11.10, doesn’t show up on 12.04.1

So… ***12 hours to get in the end nothing????***

I am  too tired now and I need some sleep (have been near 24 hours fighting with Ubuntu 12.04.1), but when I do wake up I will uninstall the da*n bl**dy 12.04.1 and I will reinstall the brilliant 11.10

Ubuntu 12.04.1:Go to H*ll!!!

I take this opportunity to thank all of you for concern and help.

All the best to all of you.

---

### Post by howefield on 2013-02-14
> **viriatovigo said:**
> It took to install it… **8 hours!!!** After that it notified me that where 331 updates to install. I did click on “install” and…

For information, 12.04.2 is out today at some stage, which is basically 12.04.1 and all the updates since.

The are some nice new features in this update including new kernel, graphics system and a few other goodies.

If you are feeling up to it and still have problems, might be worth trying it instead of starting with 12.04.1 and updating.

---

### Post by oldfred on 2013-02-14
Three or four years ago I installed Ubuntu on an old laptop. Of course I had not read instructions on minimum hardware. Back then I think the minimum was 256K and I was installing on a system with 128K. I think it only worked when I had swap already created, but even then it took on the order of your 8 hours and likewise the updates took for ever. Once booted system was impossibly slow. Installed lightweight version and it worked well.

So how much RAM does you system have?

---

### Post by MAFoElffen on 2013-02-14
Okay... You can run a LiveCD on that right? You say your experience level on "toasters" is minimal, so, lets query your toaster to get info for these people trying to help you out.

Once you start a LiveCD, start a browser and get back to this thread. Then press <cntrl><alt><T> to start a terminal session. 

You can cut and paste the commands below, one at a time, to query your hardware. Then cut and paste the returned info here into a post.
```

cat /proc/cpuinfo
cat /proc/meminfo
free -m
lspci -vnn | grep Ethernet
route
traceroute us.archive.ubuntu.com

```
So I figure your box taking 8-12 hours to download updates and 4+ to install... could mean a number of things:
- CPU/Processor speed and capabilities.
- Low memory
- Tight disk space
- Low network speed/bottleneck

Notes on above commands... So you are not just doing this blind and understand the what and why. It will also tell other's about the info you are posting for them, to look at the info and to hopefully ID the problem:
1. Displays the CPU information as Linux see's it. Will show others your CPU speed, how many cores, if it is 32bit or 64bit, If it is PAE capable, etc.
2. Displays the info on the memory available to Linux. Not enough and it will either freeze or swap excessively to disk.
3. Displays how memory and swap is used. Add's to the info from (2).
4. Displays info on your Ethernet Network adapters. Could be a slow adapter causing a slow connection to the repo's. Too slow and it may timeout the connection.
5. Internal routing table of your PC showing your path to the outside world.
6. Timings of your PC's travel over the internet to a known point. In this example, it would display your route and how long it takes to get to Ubuntu's Main US server that contains their updates. This is where you said it's taking what seems like an eternity...

Sound do-able or do you need more detailed instructions to do that?

EDIT-- Additional to this, but not touched on yet, is the apt logs. Sometimes on old hardware, if not fully supported, then apt sometimes doesn't configure right and then has apt errors on connect and/or on install. If not revealed in the above, then that would be the next place where I would check.

---

### Post by viriatovigo on 2013-02-14
Ta olfred.

My RAM is 1Gb. I am not using the PC HD with Ubuntu but an external HD of 1Tb. The partition where is Ubuntu is 70Gb. 

In that external HD I have a partition for back up (I have an image of the PC's HD and a copy of all My Documents. I do back up every Friday); in other partition is Ubuntu; in other partition is Apple Snow Leopard and the rest of it is empty (about 520Gb.

The OS on the PC's HD is WindowsXP Professional (that I do not use at all). 

In the laptop still is Ubuntu 11.10 whit which I had and I have not problems at all. Only when I did fall foul on the Ubuntu 12.04.1 update my problems began. If this do not get resolve tonight, I will uninstall 12.04.1 and install again 11.10. Maybe 11.10 has not the wonders, marvelous, "divine" things of 12.04.21 but it is working like a dream meanwhile 12.04.1 it is not.

Kind regards.

---

### Post by viriatovigo on 2013-02-14
Ta MAFoELffen.

Here it goes:

1.-
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips    : 5985.56
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

2.-
Shmem:            301284 kB
Slab:              36488 kB
SReclaimable:      21096 kB
SUnreclaim:        15392 kB
KernelStack:        3384 kB
PageTables:         7480 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      507120 kB
Committed_AS:    2779252 kB
VmallocTotal:     122880 kB
VmallocUsed:       11192 kB
VmallocChunk:      89864 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       26616 kB
DirectMap2M:      886784 kB

3.-
MemTotal:        1014244 kB
MemFree:          110716 kB
Buffers:           60032 kB
Cached:           505620 kB
SwapCached:            0 kB
Active:           455388 kB
Inactive:         388344 kB
Active(anon):     329776 kB
Inactive(anon):   249680 kB
Active(file):     125612 kB
Inactive(file):   138664 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        124040 kB
HighFree:           4144 kB
LowTotal:         890204 kB
LowFree:          106572 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        278168 kB
Mapped:            88760 kB
Shmem:            301284 kB
Slab:              36488 kB
SReclaimable:      21096 kB
SUnreclaim:        15392 kB
KernelStack:        3384 kB
PageTables:         7480 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      507120 kB
Committed_AS:    2779252 kB
VmallocTotal:     122880 kB
VmallocUsed:       11192 kB
VmallocChunk:      89864 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       26616 kB
DirectMap2M:      886784 kB
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        888        101          0         59        497
-/+ buffers/cache:        332        658
Swap:            0          0          0

4.-
MemTotal:        1014244 kB
MemFree:          110716 kB
Buffers:           60032 kB
Cached:           505620 kB
SwapCached:            0 kB
Active:           455388 kB
Inactive:         388344 kB
Active(anon):     329776 kB
Inactive(anon):   249680 kB
Active(file):     125612 kB
Inactive(file):   138664 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        124040 kB
HighFree:           4144 kB
LowTotal:         890204 kB
LowFree:          106572 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        278168 kB
Mapped:            88760 kB
Shmem:            301284 kB
Slab:              36488 kB
SReclaimable:      21096 kB
SUnreclaim:        15392 kB
KernelStack:        3384 kB
PageTables:         7480 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      507120 kB
Committed_AS:    2779252 kB
VmallocTotal:     122880 kB
VmallocUsed:       11192 kB
VmallocChunk:      89864 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       26616 kB
DirectMap2M:      886784 kB
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        888        101          0         59        497
-/+ buffers/cache:        332        658
Swap:            0          0          0
ubuntu@ubuntu:~$ lspci -vnn | grep Ethernet
02:00.0 Ethernet controller [0200]: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) [8086:108c] (rev 03)

5.-
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         dsldevice.lan   0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

6.-
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute (You will have to enable component called 'universe')
 * traceroute (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>

---

### Post by viriatovigo on 2013-02-14
Thank you for this, MAFoElffen, I hate doing things without knowing why and what it means, like an idiot. I am not too clever but not to that extent.

Quote:
"Notes on above commands... So you are not just doing this blind and understand the what and why. It will also tell other's about the info you are posting for them, to look at the info and to hopefully ID the problem:
1. Displays the CPU information as Linux see's it. Will show others your CPU speed, how many cores, if it is 32bit or 64bit, If it is PAE capable, etc.
2. Displays the info on the memory available to Linux. Not enough and it will either freeze or swap excessively to disk.
3. Displays how memory and swap is used. Add's to the info from (2).
4. Displays info on your Ethernet Network adapters. Could be a slow adapter causing a slow connection to the repo's. Too slow and it may timeout the connection.
5. Internal routing table of your PC showing your path to the outside world.
6. Timings of your PC's travel over the internet to a known point. In this example, it would display your route and how long it takes to get to Ubuntu's Main US server that contains their updates. This is where you said it's taking what seems like an eternity..."

Thank you very much indeed. I try my best to recover all those lost years.

---

### Post by viriatovigo on 2013-02-14
By the way MAFoElffen.

**There is** something wrong with my evil "toaster" because running Ubuntu 12.04.1 directly from the CD it did work like a dream.

So the 12 hours installation were wrong somewhere. Aaaaaag!!!!

---

### Post by MAFoElffen on 2013-02-14
> **viriatovigo said:**
> By the way MAFoElffen.

**There is** something wrong with my evil "toaster" because running Ubuntu 12.04.1 directly from the CD it did work like a dream.

So the 12 hours installation were wrong somewhere. Aaaaaag!!!!

I forgot to explain "lspci"... That means list pci devices. Grep is a utility that would filters out the results looking for the string "Ethernet", which will filter out the info on your network cards/devices...
```

lspci -vnn | grep Ethernet

```
It works with LiveCD... You don't have traceroute installed, but the following would give an overall picture of your route timings:
```

ping -c 5 us.archive.ubuntu.com

```
Which means ping the Ubuntu update server 5 times and quite. For example:
```

PING us.archive.ubuntu.com (91.189.91.13) 56(84) bytes of data.
64 bytes from ragana.canonical.com (91.189.91.13): icmp_req=1 ttl=47 time=103 ms
64 bytes from ragana.canonical.com (91.189.91.13): icmp_req=2 ttl=47 time=101 ms
64 bytes from ragana.canonical.com (91.189.91.13): icmp_req=3 ttl=47 time=101 ms
64 bytes from ragana.canonical.com (91.189.91.13): icmp_req=4 ttl=47 time=102 ms
64 bytes from ragana.canonical.com (91.189.91.13): icmp_req=5 ttl=47 time=102 ms

--- us.archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 101.124/101.998/103.071/0.662 ms

```

One strange note is that /proc/cpuinfo isn't ID'ing your CPU specifically, nor how fast it is... Example on mine:
```

processor	: 0
[COLOR="Red"]vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 FX-60 Dual Core Processor
[/COLOR]stepping	: 2
microcode	: 0x4d
[COLOR="Red"]cpu MHz		: 1200.000
[/COLOR]cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr [COLOR="red"]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cmp_legacy
bogomips	: 2410.98
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 1
[COLOR="red"]vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 FX-60 Dual Core Processor
[/COLOR]stepping	: 2
microcode	: 0x4d
[COLOR="red"]cpu MHz		: 1200.000
[/COLOR]cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr [COLOR="Red"]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cmp_legacy
bogomips	: 2410.98
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```
So is there a sticker somewhere on the case that says what CPU is there?

But it does say that your CPU does support PAE:
```

flags : fpu vme de pse tsc msr [COLOR="red"]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm

```

---

### Post by viriatovigo on 2013-02-15
Ta MAF

I did get this from  Berlac Advisor:

Processor a	 	
3.00 gigahertz Intel Pentium 4
16 kilobyte primary memory cache
2048 kilobyte secondary memory cache
64-bit ready
Hyper-threaded (2 total)

---

### Post by viriatovigo on 2013-02-15
I can copy and paste the full Berlac Adviser report if you want.It says all I have inside my PC (Computer Profile it calls it) but is a bit long.

---

### Post by schragge on 2013-02-15
Besides */proc/cpuinfo*, there's also *lscpu* command that prints nearly the same info, but in more human-friendly form.

---

### Post by viriatovigo on 2013-02-15
OK MAF, let's go with your last advise:

ubuntu@ubuntu:~$ lspci -vnn | grep Ethernet
02:00.0 Ethernet controller [0200]: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) [8086:108c] (rev 03)

ubuntu@ubuntu:~$ ping -c 5 us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.15) 56(84) bytes of data.
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=1 ttl=53 time=115 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=2 ttl=53 time=116 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=3 ttl=53 time=116 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=4 ttl=53 time=116 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=5 ttl=53 time=117 ms

--- us.archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 115.641/116.738/117.186/0.704 ms
ubuntu@ubuntu:~$

---

### Post by dino99 on 2013-02-15
i suspect that ubiquity (the installer) is to blame here again.

Try the mini iso installation instead

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by viriatovigo on 2013-02-15
G'afternoon MAF.

Perhaps this info from Windows Help is better, I don't know...

 Processor  
Intel(R) Pentium(R) 4 CPU 3.00GHz  
Version: x86 Family 15 Model 4 Stepping 10  
Speed: 2992 MHz

---

### Post by MAFoElffen on 2013-02-15
Your network card is 10/100/1000. Your route timings are good. You have 1GB of memory.

Pentium 4... Which is supposed to be PAE compatible. I don't know if you are going to want to hear this...

I have some Pentium and Xeon multi-processor servers. They work great on current Ubuntu. Then I have this one Pentium 4 server... I have an open bug on this server for about a year... Since they went to PAE enabled 32bit kernels. Even though this checks the processor to ensure the CPU is PAE enablable, what was oncovered later was that some onboard memory controllers could not handle that ability.

"My" Pentium 4 HP server board will run Server Edition or Desktop Edition (initially). It will Install fine. But from the time you do the first "update," it corrupts the apt tree and fails. Since I have 9 other (home) servers and 7 Desktops, I set this one aside. 

I have another dev. project. I just put it back in a case and turned it on again yesterday morning... I'm thinking of going non-PAE with that and trying it all over again.

That might be a test for you. The method of install is to install the Ubuntu 12.04 non-PAE netboot CD image "[mini.iso]("http://www.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso")" and upgrade from that. Remember (for you, xubuntu-desktop) to select a desktop package...

---

### Post by viriatovigo on 2013-02-16
Ta MAF.

Nop... It is not pleasant to hear but is a good think to know. 

Thank you for the teaching. 

Normally I build my own PCs but since a health problem (a stroke while driving)I went lazy (well... My hands are not what used to be)and bought this one on eBay. Next week I'll go to London to the PC's open  markets to buy the stuff and will start to build a new one. 

I will no bother with this any longer; **[COLOR="Red"]there is[/COLOR]** something wrong with it; for instance gets affected heavily by any RF so the wireless network adapter gets wild and it is driving me mad. Ubuntu works good directly from the CD so I will keep working from it so far until I do manage to assemble the new one. Just be practical... 

Thank you MAF. All the best.

---

### Post by viriatovigo on 2013-02-24
Hi MAF and all that did try to help me.

The problem is resolved.

Instead to install Ubuntu in  an external HD I did installed replacing Windows in the PC HD and it took only 1h 45min to install including the updates.

I did backup first all my documents, pictures, videos, music and so on in the external HD and later put them in Documents within Ubuntu.

As I said, I have been in London in the PC markets and I got everything but is going toi take time since, as I said before, myb hands are not what they use to be after the stroke, but now I wouldn't care less. Ubunntu is working like a dream.

I've been 23 hours to get to know the OS and how to use it and I will not look back again. I am not 100% fluent but I am not missing Windows at all I can do everything that I was doing in Windows, absolutely everything: I set  my email on Thunderbird, put all my bookmarks in Firefox... Was worth the fight indeed.

Once more, thank you to every one.

All the best.

Tino

---

