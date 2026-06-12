---
title: "Ubuntu (and other distros, plus older versions) extremely slow on old laptop"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by clcarrow14 on 2012-07-06
Hello. I have an old laptop from 2004 running Windows XP. It's a Jetta Jetbook 9600. It's not a popular brand, but Jetta is a small company based in the east coast.

[ftp://ftp](ftp://ftp).**jetta**us.com/**Jetta**us/**specs**heets/**9600**Brochure.pdf

My Specs are:
Intel Pentium M 2.00 GHz
1 GB Memory
60 GB Hard Drive
Mobile Intel 915GM/GMS,910GML

I have been trying to get Linux to run well on this laptop but have had no luck. The problems I am experiencing are:
Extremely Slow (like 2-5 Mins) Boot Time

Sluggish response (Example: Firefox opens fast, but if I type a letter, the program fades to black and white, and stalls for a good minute)

Sometimes, distros like Fedora and Ubuntu later than 10.04 don't boot at all.

It's too the point that Linux is unusable. :(

Anyways, I would really like to get Linux working on this machine, and any advice would be appreciated. Anyone have any similar circumstance that they have solved? I have looked all over the net and nothing has been found. I'm stumped. :/

It may be worth noting that Puppy Linux works fine, but I can't bear the interface. I'd rather have XP. It is also worth noting that my laptop can also run Windows Vista at a reasonable speed. It's old, but it's still alive and kicking. Please note that I'm not a linux newb, but I'm a little wet behind the ears. haha.

Thanks,
Cameron.

Edit: I currently have 10.04 installed on this laptop, dual boot. I'm guessing that, with proper work, that's the closest I'll get to a modern distro on this laptop.

---

### Post by black veils on 2012-07-06
things shouldnt be slow with that ram, maybe some of it is bad? or maybe the hard drive is bad? psu?

---

### Post by clcarrow14 on 2012-07-07
I've done a memory test on it, everything is fine.. I have no problems with my hard drive under Windows XP, nor Vista. And as for PSU, I don't believe that would cause any problems with only Linux. I would notice if something was wrong with it in Windows, but Windows runs stable and smooth. It's just not my preference. :P

If you have any commands for me to post the output of, then let me know. I can get into Ubuntu 10.04, it just takes a while to do everything. :P

I have heard before, although I don't know the legitimacy of this, that Windows is better at working with buggy hardware/not fully functional hardware. So perhaps, this laptop of mine could be buggy or something.. idk. XD

Thanks,
Cameron.

Oh BTW, if you know any tests I can do to my hardware to help you help me solve this problem, please let me know! :)

---

### Post by clcarrow14 on 2012-07-07
*Bump*

If bumping is not allowed in this forum, I apologize. I'm just trying to get the laptop running Ubuntu. :D

---

### Post by Merrattic on 2012-07-08
If you can install htop (or just use Task Manager) to see what programs are running, using CPU/RAM?

Is your HDD thrashing away all the time (blinking light etc) ?

If you are not fussed about using ubuntu, try Slitaz on there and see how that runs (Openbox/LXDE)

---

### Post by plucky on 2012-07-08
> My Specs are:
Intel Pentium M 2.00 GHz
1 GB Memory
60 GB Hard Drive
Mobile Intel 915GM/GMS,910GML

The Intel Pentium M Cpu will not boot Ubuntu 12.04 as it will not support the PAE Kernel which is now being used it 12.04.

Try Xubuntu 12.04 as that uses the non-PAE kernel,or do what I did and install Ubuntu 11.10 and upgrade the 12.04 on my Intel Pentium M laptop.

My laptop has the Pentium M 1.7Ghz with 512 Mb of memory and is very usuable.

Good Luck

---

### Post by clcarrow14 on 2012-07-08
> **plucky said:**
> The Intel Pentium M Cpu will not boot Ubuntu 12.04 as it will not support the PAE Kernel which is now being used it 12.04.

Try Xubuntu 12.04 as that uses the non-PAE kernel,or do what I did and install Ubuntu 11.10 and upgrade the 12.04 on my Intel Pentium M laptop.

My laptop has the Pentium M 1.7Ghz with 512 Mb of memory and is very usuable.

Good Luck

I'm aware of this, so back when 12.04 came out, I installed using the net iso, and well, that's when I found out Unity is definitely not the answer, as it's worse on my laptop than Gnome is..

My hard drive is acting like normal, it's just when I run a program in linux, it shows usage until it finishes stalling. Could it possibly be my hard drive, even though it works with Windows? I mean, I guess that would make sense, as Puppy, which boots into RAM, runs perfect.

I'll check out Slitaz, and I'll let you know if any specific programs are using up my CPU/RAM.

Thanks guys. :)

Edit: I don't think SliTaz is quite what I'm looking for. I'm looking for something to replace Windows completely on this laptop. But thanks for the suggestion. :)

---

### Post by clcarrow14 on 2012-07-08
I would like to report that I believe my hard drive is the problem.. Not sure if it is because of the hard drive itself, or the way it was configured.

I am currently typing this from a Linux Mint 10 flash drive I had laying around, and it works perfectly..

I wish  could get it to work on my laptop, but I may be out of luck, because laptop IDE hard drives are a little hard to find these days.

Thank you,
Cameron.

---

### Post by cipherboy_loc on 2012-07-08
Might try using smartctl. 

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

It should detect most things. 


Cipherboy

---

### Post by oldos2er on 2012-07-08
> **clcarrow14 said:**
> *Bump*

If bumping is not allowed in this forum, I apologize.

It's allowed, we just ask that you do it not more than once every 24 hours.

---

### Post by clcarrow14 on 2012-07-08
> **oldos2er said:**
> It's allowed, we just ask that you do it not more than once every 24 hours.

Oh, thank you. :)

I'll check out that hard drive tool and report back.

---

### Post by clcarrow14 on 2012-07-08
Here is the output: 

```
mint@mint ~ $ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio EIDE
Device Model:     WDC WD600UE-00HCT0
Serial Number:    WD-WXEY04008151
Firmware Version: 09.07D09
User Capacity:    60,011,642,880 bytes [60.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Jul  8 23:01:33 2012 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 4800) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  63) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   189   170   021    Pre-fail  Always       -       1550
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3649
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10263
 10 Spin_Retry_Count        0x0012   100   098   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2468
192 Power-Off_Retract_Count 0x0032   001   001   000    Old_age   Always       -       6312280
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       6658611
194 Temperature_Celsius     0x0022   107   099   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```I'm not quite sure what these results mean. Could someone help me interpret them?

*Edit* Sorry for double posting. I wasn't sure how to make a CODE box, so I just made a new reply.

---

### Post by clcarrow14 on 2012-07-09
*Bump*

---

### Post by mastablasta on 2012-07-10
the problem is you graphics card. unity uses hadrware acceleration so it needs quite a bit of power to run well (new computer would run it with no issues).
 
you graphics card (actually a chip) is weak by itself and add a poor Intel linux driver support to that and you get this.
 
solutions? you can try Unity 2D or Gnome Fallback mode. See if they perform any better. If everything is still slow. it's time to think about alternative desktop environments. Xubuntu 12.04 (XFCE) is one of them. it is lighter on resources while at the same time it looks likeold Gnome (it can be easilly customized to look exactly like old gnome). you can install lubuntu desktop next to your current Gnome installation. Another even lighter option is Lubuntu (LXDE). It's still being developed but for some it performs well on these old intel chips and their old maschines. 
 
you can also try openbox (to me that is a bit too minimalistic) or ubuntu based Bodhi linux. both are very light options.

---

### Post by clcarrow14 on 2012-07-11
> **mastablasta said:**
> the problem is you graphics card. unity uses  hadrware acceleration so it needs quite a bit of power to run well (new  computer would run it with no issues).
 
you graphics card (actually a chip) is weak by itself and add a poor Intel linux driver support to that and you get this.
 
solutions? you can try Unity 2D or Gnome Fallback mode. See if they  perform any better. If everything is still slow. it's time to think  about alternative desktop environments. Xubuntu 12.04 (XFCE) is one of  them. it is lighter on resources while at the same time it looks likeold  Gnome (it can be easilly customized to look exactly like old gnome).  you can install lubuntu desktop next to your current Gnome installation.  Another even lighter option is Lubuntu (LXDE). It's still being  developed but for some it performs well on these old intel chips and  their old maschines. 
 
you can also try openbox (to me that is a bit too minimalistic) or  ubuntu based Bodhi linux. both are very light options.

Thank you for the reply. I know my graphics chip is old, but I honestly doubt that is the problem. As mentioned previously, Linux Mint 10 (Gnome 2) booted from a flash drive works perfectly. An installation of Ubuntu 10.04 (Gnome 2, also) on the hard drive is not usable. Boot time is horrendous, and the OS is sluggish. Both of these problems mentioned in my first post.

I have tried many DEs on this laptop, none of them are usable when installed on a hard drive. Whether it be Gnome, LXDE, or XFCE, it doesn't make a difference

I have also done some research, and it appears that certain models of Western Digital hard drives, including the one in my laptop, have difficulties with read/write speeds when using Linux. I haven't really looked into it too much, but that could explain why I can run XP/Vista, but not something lighter, such as LXDE.

Again, I thank you for the reply, but please read the thread prior to replying.

---

