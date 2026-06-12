---
title: "is this a software issue or a hardware issue? - random freezes and crashes"
date: 2022-08-23
forum: Installation &amp; Upgrades
---

### Post by tilcica on 2022-08-23
just installed ubuntu 22.04 LTS because my PC was a having a ton of problems on windows 10(random bluescreens every 30 mins) and provided no actual errors or logs that would point to a single thing. after trying to get it to work for almost a week, I decided to throw in the towel and just install ubuntu as I've been planning for almost a year now. made a bootable USB, the install stalled or crashed 3-4 times before finishing. almost instantly after install, it started crashing and freezing with no apparent reason. swapped out the GPU for a different one, still froze. swapped out RAM for different ones - still froze. measured voltages and power output of PSU, all normal (4.81V and 12.11V, 363W out of possible 550W) so the problem is now either software related, though highly unlikely due to it persisting over 4 formats and 3 different OS (win10pro, win11pro and ubuntu 22.04) or a hardware issue (most likely CPU or MOBO).

I found the crash logs on ubuntu but don't know how to find any useful info in them, if there is any at all. do they point in the direction of a software issue or a hardware issue, if it's a hardware one, is it possible to see which component it could be?

PC specs:
AMD Ryzen 5 3600
tomahawk b450
kingston 4x4GB DDR4 2100MHz RAM
AMD Radeon RX580 nitro
1x128GB SATA SSD
2x7200rpm SATA HDD
CoolerMaster G550D power supply

Ubuntu crash logs are added as attachments

Windows blue screens of death errors were:
- kernel auto boost invalid lock release
- apc index mismatch
- pfn list corrupt
- irql not less or equal
- kernel security check issue
- kmode exception not handeled
- kernel auto boost lock acqusition with raised irql

---

### Post by TheFu on 2022-08-23
Dying  or misconfigured hardware cannot be fixed by software. Sorry.

I won't be looking through thousands of lines of logs. That feels too much like "work."  If you'll hone that down to the relevant lines with the actual issues, say fewer than 25 lines, someone might look.  Please don't make it hard for others to help and remember that everyone here is volunteering their time.

---

### Post by oldfred on 2022-08-23
This still gives me a couple of pages. Some are just repeating commands that have error in description like the mount of /.
Several days ago I had at least two pages. Just reran it and got three lines.?
I do not think I changed that many settings, do some update must have improved things.

sudo grep -E -i "error|warning" /var/log/dmesg

---

### Post by tilcica on 2022-08-23
I know it can't be, that's why I'm asking - to find out if someone who knows more than me, could point me in the right direction, as to: is this a hardware or software issue.

also I know not everyone has the time to sift through the whole logs but I don't know what I should even be looking for since I'm not familiar with ubuntu so I gave the whole log files if maybe at least 1 person has the time and knowledge to do so. if anything will even show there

---

### Post by Impavidus on 2022-08-23
If the issue exists on multiple OSs, it's probably hardware. Does the issue appear when just running the live disk, without installing or accessing the hard drive in any other way? If not, then my guess is a bad hard drive or SATA cable.

---

### Post by TheFu on 2022-08-23
oldfred provided a command to search log files.

The fact that the system is unstable with 2 different OSes, means it is likely hardware and I'd guess RAM speed related due to Ryzen.  I've had to slow my RAM down to 2666Mhz even though it is rated for 3200Mhz on my Ryzen 5 2xxxx box.  But the problem could be with the storage starting to fail too. 

```
$ sudo inxi -m
Memory:    Used/Total: 17511.1/32096.8MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-2: DIMM_A2 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-3: DIMM_B1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-4: DIMM_B2 size: 8 GB speed: 2666 MT/s type: DDR4
```

Hence, why I said hardware or misconfigured.

---

### Post by tilcica on 2022-08-23
> **Impavidus said:**
> If the issue exists on multiple OSs, it's probably hardware. Does the issue appear when just running the life disk, without installing or accessing the hard drive in any other way? If not, then my guess is a bad hard drive or SATA cable.

most of the time it happens when doing stuff (browser, games, work, etc) but I think it did crash 1 or 2 times while not doing anything

---

### Post by tilcica on 2022-08-23
> **TheFu said:**
> oldfred provided a command to search log files.

The fact that the system is unstable with 2 different OSes, means it is likely hardware and I'd guess RAM speed related due to Ryzen.  I've had to slow my RAM down to 2666Mhz even though it is rated for 3200Mhz on my Ryzen 5 2xxxx box.  But the problem could be with the storage starting to fail too. 

```
$ sudo inxi -m
Memory:    Used/Total: 17511.1/32096.8MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-2: DIMM_A2 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-3: DIMM_B1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-4: DIMM_B2 size: 8 GB speed: 2666 MT/s type: DDR4
```

Hence, why I said hardware or misconfigured.

I have 2 different sets of 2x4GB sticks but both are capped at 2100MHz so it looks like it's not the issue. storage could maybe be the issue, will try disconnecting the disk and installing on a different one, but in that case, why would the ubuntu USB crash before even starting install?

---

### Post by tilcica on 2022-08-23
did [COLOR=#000000]sudo grep -E -i "error|warning" /var/log/dmesg*[/COLOR]

/var/log/dmesg:[    0.915524] kernel: mce: [Hardware Error]: Machine check events logged
/var/log/dmesg:[    0.915526] kernel: mce: [Hardware Error]: CPU 1: Machine Check: 0 Bank 0: baa0000000010145
/var/log/dmesg:[    0.915533] kernel: mce: [Hardware Error]: TSC 0 MISC d012000100000000 SYND 4d000003 IPID b000000000 
/var/log/dmesg:[    0.915536] kernel: mce: [Hardware Error]: PROCESSOR 2:870f10 TIME 1661271670 SOCKET 0 APIC 2 microcode 8701021
/var/log/dmesg:[    1.098771] kernel: RAS: Correctable Errors collector initialized.
/var/log/dmesg:[    4.566868] kernel: EXT4-fs (sdc2): re-mounted. Opts: errors=remount-ro. Quota mode: none.
/var/log/dmesg.0:[    1.094687] kernel: RAS: Correctable Errors collector initialized.
/var/log/dmesg.0:[    3.784908] kernel: EXT4-fs (sdc2): re-mounted. Opts: errors=remount-ro. Quota mode: none.

so my guess would be that this points at a CPU problem

---

### Post by TheFu on 2022-08-23
> **tilcica said:**
> did [COLOR=#000000] 
so my guess would be that this points at a CPU problem

CPUs don't really fail, so that would be extremely unlikely if the CPU came from a normal retail seller.  They throttle before overheating, unless the thermal paste on the CPU wasn't correct.  The last 10 yrs, CPUs have come with thermal paste pre-installed, IME.  Are you watching the temperatures - assuming it makes it passed the boot?

To check the storage, look at SMART data.  smartctl is the command - two steps.  Request a test, wait for the test to finish (2m to 5 hrs), run a report for the test results.
You've also overloaded the MB being bad or having bad components.  That would suck.  You've done all the testing in the order that I would - likely better than I would have done it.

---

### Post by QIII on 2022-08-23
Memory and/or CPU faults would be noticed immediately.

Periodic faults as you describe strongly indicate a thermal cause.

Most likely issues there are the motherboard and/or the PSU.

A somewhat less likely cause might be a leaky application that eventually uses up all of your RAM.

---

### Post by TheFu on 2022-08-23
> **QIII said:**
> Memory and/or CPU faults would be noticed immediately. 

I had a RAM speed issue that would show up about every 4 days until I slowed the RAM down.  No other changes, just RAM.  Ryzen is very picky about RAM and having matched RAM for the entire system, not just matched pairs.  But that's just my experience.  The same RAM, in the same system, set to run slower, has no stability issues the last 2 yrs.
```
$ uptime
 15:24:33 up 9 days,  4:37,  5 users,  
```
Stable enough.  Also have a Ryzen 5600G with 2 sticks running happily at 3200Mhz.  Same exact RAM vendor SKU in both systems for all 6 sticks (4 in 1, 2 in the other).

---

### Post by tilcica on 2022-08-23
> **TheFu said:**
> CPUs don't really fail, so that would be extremely unlikely if the CPU came from a normal retail seller.  They throttle before overheating, unless the thermal paste on the CPU wasn't correct.  The last 10 yrs, CPUs have come with thermal paste pre-installed, IME.  Are you watching the temperatures - assuming it makes it passed the boot?

To check the storage, look at SMART data.  smartctl is the command - two steps.  Request a test, wait for the test to finish (2m to 5 hrs), run a report for the test results.
You've also overloaded the MB being bad or having bad components.  That would suck.  You've done all the testing in the order that I would - likely better than I would have done it.

it's not thermal throttling since I also took apart the whole PC, cleaned the thermal paste (was still "fresh" and covered the whole cpu) and the cooler was clean. applied new paste and it was still happening even with the case open and plenty of cool air around. 

I'm on another fresh install (mint this time since it was faster to install) but on another disk and it seems to be working beside the 1 crash during install. will try an ubuntu install tomorrow and turn on a few stress tests to see if it's gonna work or not and update the forum if it works or not

---

### Post by bingodingo on 2022-08-23
> **tilcica said:**
> I have 2 different sets of 2x4GB sticks but both are capped at 2100MHz so it looks like it's not the issue. storage could maybe be the issue, will try disconnecting the disk and installing on a different one, but in that case, why would the ubuntu USB crash before even starting install?

Mixing different sets of ram is risky - not guaranteed to work. (Even if it's the exact same ram, same manufacturer - sticks are only guaranteed to run as a set if sold as a kit.)
I would try running the system with just one of the sets of ram on out-of-the box settings (don't turn xmp/docp on) and see what happens.
(Follow your manual to properly remove / install the ram, making sure to disconnect power etc first.  
Use the B2 and A2 slots (*right*-most and second from *right*), see your manual, and Select [FONT=sans-serif]F6[/FONT][FONT=sans-serif]:[/FONT][FONT=sans-serif]Load optimized defaults, which will also make sure you haven't accidentally changed a bios setting in a way that is causing problems.[/FONT])
Until proven otherwise, running incompatible sticks of ram is what is causing your problem (each set by themselves may run fine).

Good luck

Edit: you can also try [https://www.memtest86.com/](https://www.memtest86.com/) (follow the directions). Also, you may need to reset CMOS after changing your ram configuration (see your manual).

---

### Post by TheFu on 2022-08-23
Ryzen is **very** picky about RAM.

---

### Post by tilcica on 2022-08-24
> **TheFu said:**
> Ryzen is **very** picky about RAM.

i know it is but i've had this setup for almost a year now without any problems. i've also tried both ways to have 4 sticks (1212 and 1122) and both work, even tho by b450 specs, i now have it at 1122. for some reason, correct ram placement for this board is: 
x1xx
x1x1
1122

also have tried with completely different ram that came in a set (2x4gb) and it was still crashing so ram itself is not the problem

also disconected the SSD and one HDD, installed ubuntu on the last HDD that was plugged in (format and clean install) and it crashed so my guess is, storage is also okay

---

### Post by TheFu on 2022-08-24
I had a Ryzen system that worked perfect for a year, added 2 sticks with the same vendor SKU, ran it at 2900Mhz for 14 months fine, then it started crashing.  The kernel crash logs showed that it was always why swapping.  I checked the SMART data on the storage (I do SMART tests and reports weekly), and saw the storage was fine.  Started watching the temperature and saw that it never exceeded the max thermal allowed, then started backing off the RAM speed after seeing a random post somewhere that Ryzen was very picky about matched sets.  As I slowed the RAM down, the uptime increased.  I was seeing 4-6 days up, with 2800Mhz, but really wanted to never worry about RAM being the issue again, so kept slowing and testing. Nothing else has been changed in the system. Just RAM and just the speed it is run.

This little script helps me get a count of kernel events in the logs for the last 10 boots:
```
$ more ~/bin/crashing 
#!/bin/bash

for i in {0..9} ; do
   RC=$(journalctl -b -$i |egrep 'dump_stack' |wc -l)
   echo "Boot -$i : $RC"
done;
```

When it was crashing, I'd see hundreds of stack traces in the logs, before a crash.  In the system, as it runs today, I'm seeing 1 stack dump due to Firefox oom-killer.   The kernel killed it for violating asking for memory that it could provide.  I run firefox inside a RAM limited firejail sandbox, so it isn't allowed to allocate 60GB of RAM, just around 8GB. Allocations beyond that aren't possible and it gets killed.  The system logged, there was a page fault, and it keeps going.  In 22.04, there  have been many complaints about the oom-killer being overly aggressive.  The Ryzen system I'm on still uses 18.04.

Anyway, that's my best guess.  I know we sound like broken records.

---

### Post by bingodingo on 2022-08-24
> **tilcica said:**
> i know it is but i've had this setup for almost a year now without any problems. i've also tried both ways to have 4 sticks (1212 and 1122) and both work, even tho by b450 specs, i now have it at 1122. for some reason, correct ram placement for this board is: 
x1xx
x1x1
1122

also have tried with completely different ram that came in a set (2x4gb) and it was still crashing so ram itself is not the problem

also disconected the SSD and one HDD, installed ubuntu on the last HDD that was plugged in (format and clean install) and it crashed so my guess is, storage is also okay

Can I suggest your reasoning is a little off?: 
1. "but i've had this setup for almost a year now without any problems" - so by this argument the CPU, the motherboard and  everything else are all good as well? Smells like wish fulfillment to me. Have a look at TheFu's comments.
2. "also have tried with completely different ram that came in a set (2x4gb) and it was still crashing" So it's not possible that there was also a problem with that kit (or the timings you set for it)? Surely it's better at least to run memtest86 on your current set up? Are any of these kits on the QVL for your board? I don't see any Kingston 2100MHz kits - do you mean 2133MHz?
3. "for some reason, correct ram placement for this board is: ..." how can you tell correct placement when your system isn't working as specified? 1st two  rows are the same as the quick start page 4, 3rd row assumes you can mix kits - this assumption may be wrong / causing your problems.

You can say / prove whatever you like on the forum (happy to listen) but your system isn't paying any attention, the pathology will just continue until you dig it out. A systematic approach will get you there faster.

---

### Post by tilcica on 2022-08-26
> **bingodingo said:**
> Can I suggest your reasoning is a little off?: 
1. "but i've had this setup for almost a year now without any problems" - so by this argument the CPU, the motherboard and  everything else are all good as well? Smells like wish fulfillment to me. Have a look at TheFu's comments.
2. "also have tried with completely different ram that came in a set (2x4gb) and it was still crashing" So it's not possible that there was also a problem with that kit (or the timings you set for it)? Surely it's better at least to run memtest86 on your current set up? Are any of these kits on the QVL for your board? I don't see any Kingston 2100MHz kits - do you mean 2133MHz?
3. "for some reason, correct ram placement for this board is: ..." how can you tell correct placement when your system isn't working as specified? 1st two  rows are the same as the quick start page 4, 3rd row assumes you can mix kits - this assumption may be wrong / causing your problems.

You can say / prove whatever you like on the forum (happy to listen) but your system isn't paying any attention, the pathology will just continue until you dig it out. A systematic approach will get you there faster.

1) could be, yeah. i swapped the RAM and GPU for another known working one (used by my brother daily with no problems) and it was crashing on my rig, checked my 2 parts on his rig and it was running without bigger problems

2) the other ram set is in working condition and my brother uses it daily with no problems whatsoever. i ran memtest86 on both my set and his, both passed with 0 errors in my and his rigs (4 tests in total). ye, i meant 2133MHz 

3) the way i said that ram had to be placed was directly from the mobo manufacturer (MSI). i've also trid running with only 1 kit (2x4) and it was crashing so non matched or non working ram is not the problem or at least not the only one. 

i tried swapping all of the components that i could (PSU, RAM, GPU, SSD and the sata cable) and confirmed that all of them work but the ssd is a bit iffy. installed on a new one and it still wasnt working so the only thing that could be broken now is the CPU or mobo. went to ask 4 pc servis/repair shops if they could test one of them individually and only one could....for 40€ (minimum, could be higher) and a 2 week wait period. at least they confirmed that from the limited info they have, it is most likely a board problem. i ordered a new one and it should arrive today i think

---

### Post by TheFu on 2022-08-26
I'd think the Mobo is it too.  Sucks when this happens, but it is better than having to pay 3x more for a Mobo replacement from a branded computer build. Computers built from common, components are so much better for replacements.  Did you pick a different Mobo?  I've been happy with Asus recently.   I have an MSI from 2010 that is sorta working, but something is wrong with the PCIe slot for the GPU. It only resets on full power off. A computer restart doesn't work.

---

### Post by davidjmhansen on 2022-08-27
Windows is stable on good hardware.  Linux is also stable on good hardware.  It sounds like you have problems with your hardware.  I had the same type of issues when I used a bad hardware vendor that sold "refurbished" parts as new.

If you bought your hardware used or refurbished, it is possible that it was abused or had problems before.  I recommend that you change your hardware vendor after you return whatever you can.

---

### Post by tilcica on 2022-08-29
ok, so I ended up testing EVERYTHING twice and found out either the mobo (MSI b450 tomahawk) or the cpu (ryzen 5 3600) died. bought new parts, swapped them out and not a SINGLE issue from then on out. bought a ryzen 5 5600x and an ASUS prime x570-p, so it was also a bit of an upgrade from the previous parts. sadly can't test the old components myself since that would require way more work than I'm willing to put in. gonna most likely send them to the seller I bought the new stuff from since I know they buy used stuff, test it and then sell it as refurbished (they at least mark the stuff correctly - new, refurbished or dead, for parts). thanks so much for the help to everyone in here :D

sadly gonna have to switch from the newest ubuntu since some of the more important stuff I need for school isn't updated yet and I start in a couple days </3 hope I'll have more luck the next time I'll have time to switch to linux lol 

o7

---

### Post by TheFu on 2022-08-30
> **tilcica said:**
>  sadly gonna have to switch from the newest ubuntu since some of the more important stuff I need for school isn't updated yet and I start in a couple days </3 hope I'll have more luck the next time I'll have time to switch to linux lol 

Switching to a Linux-only desktop isn't quick, but none of this thread was caused by Linux. It was bad hardware.  Because I have time, I would have switched just the motherboard, since a bad CPU is extremely unlikely. Plus, they have warranties, so getting a replacement shouldn't be much more than writing a short letter, if that. [https://www.amd.com/en/support/kb/warranty-information/rma-form](https://www.amd.com/en/support/kb/warranty-information/rma-form)  The Ryzen 3xxx series is still an awesome CPU compared to what many people have.  I have both a 2600 and 5600G - both are extremely capable and run lots of VMs, video transcoding (CPU, not GPU) and are very stable with good RAM. Of course the 5600G is much newer, so it is faster and the onboard GPU is better than the nvidia GT 1030 that the other box uses.

I'd strongly suggest that you run a hypervisor and install a Linux of your choice inside a virtual machine, so you can learn and do nearly everything with Linux while still having the MSFT safety net.

I still have MS-Windows running inside a virtual machine here for the 2 things I need it for.  That list of Windows-only needs was 50, then 20, then 5 and sat at 5 for nearly a decade.  In just the last 2 yrs, it has gotten down to 2 programs - tax and financial - that remain.  Everything else is done on Linux and my Windows VM is powered off except for about 2 hrs every other week and for a few days a year for tax prep work.

Using MS-Windows is extremely frustrating for me and has been for 15 yrs.  Around 2009, I tried a Mac and found it even more frustrating.  All that power, but no real control.  But getting to the point where Linux could be my main desktop literally took decades.  If my job used MS-Windows, I'd probably still be using it more ... at least on their equipment.  When MSFT changed the EULA as Win10 beta was released, I stopped updating all MSFT software. I couldn't accept the new terms. Not everyone has that luxury.

---

