---
title: "Post your Karmic bootcharts or boot times!"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-01
(What's the difference between bootchart-java and pybootchart?)

Not quite 10 seconds, but I'm satisfied with this...
[http://ubuntuforums.org/attachment.php?attachmentid=123233&d=1249163710](http://ubuntuforums.org/attachment.php?attachmentid=123233&d=1249163710)

---

### Post by caryb on 2009-08-01
32.64 Secs for me!

---

### Post by Yofel on 2009-08-01
Thinkpad: 28s
EeePC: 16s (SSD)
:D

---

### Post by ronacc on 2009-08-01
18 sec here .

---

### Post by autocrosser on 2009-08-01
Well--I'm less than impressed---I hadn't compared my times in quite a while...I dug back thru my records & here is a typical Jaunty Alpha from the development period & a typical Karmic from same time-period...no hardware changes during this time....I'm booting 10 sec slower than I was in Jaunty.....go figure...

---

### Post by MacUntu on 2009-08-01
A bit slower than Jaunty. What still hasn't changed over the years is the slooooooow session start. Better change to automatic login, add "bootchart=nostop" to your kernel boot line, and run "sudo /etc/init.d/stop-bootchart start" once everything is loaded. I'm sure you won't care about GRUB -> GDM times any longer. :D

---

### Post by xebian on 2009-08-02
16.03 secs here

---

### Post by xebian on 2009-08-02
> **caryb said:**
> 32.64 Secs for me!

I noticed on your signature that you have T7500?  But your bootchart says it's T7300.  Have you been shortchanged?

---

### Post by ktechkio on 2009-08-02
13 seconds here. 

Desktop PC
Pentium D 2.8 ghz Prestler, 2 Gb RAM @ 800 mhz, 7800 rpm hard drive, NVIDIA Geforce 8500 1Gb

---

### Post by Nburnes on 2009-08-02
Not much faster than Jaunty.

---

### Post by rudenko_ruslan on 2009-08-02
Mine.

---

### Post by plun on 2009-08-02
My laptop is rather sleepy....:-k

---

### Post by BUGabundo on 2009-08-02
> **Starks said:**
> (What's the difference between bootchart-java and pybootchart?)

well one uses JAVA and the other python.
Not everyone enjoys java.
also python bindings came latter, and was a bit more buggier (like it left bad margins in the png, etc)
AFAIK right now, both should produce similar results

Take into consideration that jaunty version suffered several modifications to the one on ibex, and that the one on Karmic is a totally re-written script.

For those that *really* want to measure their boot *and* login time, you can hack the /etc/rc5.d/S99stop-bootchart and add a line with a sleep X time on line 41.

I have mine with sleep 30 right now, on a karmic clean install. but on my old system that would boot to gdm in 30 secs, and only be usable after another 40 secs, i need a sleep of 60 secs.
Now i get to GDM in 19 secs, and usable on an extra 20 secs.
```
case "$1" in
    start)
	if [ -d $JAIL ]; then
	    LOGS=$JAIL/log
	elif [ ! -d $LOGS ]; then
	    exit 0
	fi

	sleep 30;
	# Kill the collector process, wait for it to end
	pkill -f /lib/bootchart/collector
	sleep 2

```

I have most of my bootcharts since hardy to karmic here:
[http://fileland.bugabundo.net/fotos/Linux/bootchart/](http://fileland.bugabundo.net/fotos/Linux/bootchart/)

---

### Post by MadsRH on 2009-08-02
> **Starks said:**
> Not quite _10 seconds_, but I'm satisfied with this...]

It is a common misunderstanding that Karmic will boot in 10 seconds. The 10 seconds boot is target for Karmic+1 

[http://people.ubuntu.com/~scott/boot-performance/Fast%20Boot.odp](http://people.ubuntu.com/~scott/boot-performance/Fast%20Boot.odp)

---

### Post by caryb on 2009-08-02
> **xebian said:**
> I noticed on your signature that you have T7500?  But your bootchart says it's T7300.  Have you been shortchanged?

A bug I believe...

cary@stinkpad:~$ cat /proc/cpuinfo 
processor       : 0                
vendor_id       : GenuineIntel     
cpu family      : 6                
model           : 15               
model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping        : 10                                             
cpu MHz         : 800.000                                        
cache size      : 4096 KB                                        
physical id     : 0                                              
siblings        : 2                                              
core id         : 0                                              
cpu cores       : 2                                              
apicid          : 0                                              
initial apicid  : 0                                              
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority              
bogomips        : 4393.66                                                                              
clflush size    : 64                                                                                   
cache_alignment : 64                                                                                   
address sizes   : 36 bits physical, 48 bits virtual                                                    
power management:                                                                                      

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6           
model           : 15          
model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping        : 10
cpu MHz         : 800.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips        : 4393.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

:confused:

---

### Post by philinux on 2009-08-02
Karmic is 15 Seconds
Jaunty is 20 Seconds

Jaunty seems to have a bit of a hang at the start.

---

### Post by Jay_Bee on 2009-08-02
Bootchart says 20 seconds but my stopwatch says 32

---

### Post by MacUntu on 2009-08-02
Ok, for your viewing pleasure:

10.67 sec.

[[img]http://img.xrmb2.net/538478.jpg[/img]](http://img.xrmb2.net/images/538478.png)

[LIST]
[*] 7200rpm notebook hard disk
[*] Stock kernel (one tailored to my system -> 9.24 sec.)
[*] Readahead list optimization like I always do (created a complete list with the 'profile' parameter, tared and untared the files some times to bring them physically closer together on disk, sorted the list by the file's start block)
[*] Upstart (saves about two seconds, converted like described here: [http://ubuntuforums.org/showthread.php?t=727224](http://ubuntuforums.org/showthread.php?t=727224))
[/LIST]

But as already said, the really interesting thing is GRUB -> desktop. You can reduce the session load time a bit with readahead but the bigger changes have to be done code-wise.

> **BUGabundo said:**
> For those that *really* want to measure their boot *and* login time, you can hack the /etc/rc5.d/S99stop-bootchart and add a line with a sleep X time on line 41.

Or you just could add "bootchart=nostop" to GRUBS's kernel line (you have to manually stop it after the session is loaded, of course). :)

---

### Post by fifth on 2009-08-02
25.99 seconds here.

---

### Post by terry_gardener on 2009-08-02
15.86

---

### Post by cecilpierce on 2009-08-02
I cant get either pybootchartgui or bootchart to work, Parse error: empty state: '/var/log' does not contain a valid bootchart, how can I fix it ?

---

### Post by MacUntu on 2009-08-02
Do you have a tgz file in /var/log/bootchart? If so, does
```
bootchart -f png -o /home/<your user>/Desktop/bootchart.png /var/log/bootchart/<tgz file>
```
create a chart?

---

### Post by cecilpierce on 2009-08-02
tried it,

warning: path '/var/log/bootchart/bootchart.tgz' does not exist, ignoring.
Parse error: empty state: '/var/log/bootchart/bootchart.tgz' does not contain a valid bootchart

Not sure whats wrong or what to do ?
this is what I typed: bootchart -f png -o /home/cecil/Desktop/bootchart.png /var/log/bootchart/bootchart.tgz

---

### Post by fifth on 2009-08-02
> **cecilpierce said:**
> tried it,

warning: path '/var/log/bootchart/bootchart.tgz' does not exist, ignoring.
Parse error: empty state: '/var/log/bootchart/bootchart.tgz' does not contain a valid bootchart

Not sure whats wrong or what to do ?
this is what I typed: bootchart -f png -o /home/cecil/Desktop/bootchart.png /var/log/bootchart/bootchart.tgz

Did you reboot after installing bootchart?

---

### Post by cecilpierce on 2009-08-02
OK thanks MacUntu and fifth now I have a .png,
now see if i did it right with the attachment thing.

---

### Post by Stereotypical Rage on 2009-08-02
Mine is nearly 2 mins in length! (1:47.30). It was 5 mins with Jaunty!!

Something would appear to be wrong. I have long suspected my HDD to be the culprit, but hdparm output seems OK for SATAII drives.

Average of 3 tests:
Timing cached reads:   15028 MB in  6.00 seconds = 2504.67 MB/sec
Timing buffered disk reads:  824 MB in  9.04 seconds =  91.15 MB/sec

---

### Post by wayne_cat on 2009-08-02
> **Stereotypical Rage said:**
> Mine is nearly 2 mins in length! (1:47.30). It was 5 mins with Jaunty!!

Something would appear to be wrong. I have long suspected my HDD to be the culprit, but hdparm output seems OK for SATAII drives.

Average of 3 tests:
Timing cached reads:   15028 MB in  6.00 seconds = 2504.67 MB/sec
Timing buffered disk reads:  824 MB in  9.04 seconds =  91.15 MB/sec

Do you really need ntpd?

---

### Post by Stereotypical Rage on 2009-08-02
> **wayne_cat said:**
> Do you really need ntpd?

Probably not.

---

### Post by billyShears on 2009-08-02
27 seconds on my athlon xp 1700+

---

### Post by phenest on 2009-08-02
> **MadsRH said:**
> It is a common misunderstanding that Karmic will boot in 10 seconds. The 10 seconds boot is target for Karmic+1

Even still, Karmic is quicker than Jaunty.
(Jaunty left, Karmic right)

---

### Post by MacUntu on 2009-08-02
> **phenest said:**
> Even still, Karmic is quicker than Jaunty.
(Jaunty left, Karmic right)

Jaunty's 44 - 23 for fsck = 21 = Karmic! :D

---

### Post by phenest on 2009-08-02
> **MacUntu said:**
> Jaunty's 44 - 23 for fsck = 21 = Karmic! :D

Ha! Never noticed that! Yeah, I have another for Jaunty without the check, and it's 20seconds. :lol:

---

### Post by Seventh Reign on 2009-08-02
1:10 seconds with the input/output floppy error

:23 seconds after I disabled the floppy drive from the bios

I'll test my Jaunty installs later for comparison. 
(Edit: 26 seconds for Mint 7)
(Edit2:  Thats Mint 7 running ext3 not ext4 .. I re-installed last night .. too many lock ups)

---

### Post by Hairy_Palms on 2009-08-02
16 seconds which is 6 seconds faster than jaunty :)

---

### Post by bjorkiii on 2009-08-04
By disabling the floppy drive in bios i have gone from over 1 minute 30ish to 19 seconds 

but i cant show the log thing because im incapable of working out what to do marvelous eh

---

### Post by keypox on 2009-08-04
> **bjorkiii said:**
> By disabling the floppy drive in bios i have gone from over 1 minute 30ish to 19 seconds 

but i cant show the log thing because im incapable of working out what to do marvelous eh

you gotta install it, its in synaptic. I think lol never used it.

---

### Post by taavikko on 2009-08-07
My chart shows that this laptop is a piece of junk...
even when splash removed and concurrency set to shell

And when you add the login->desktop it's a whole lotta more... :)

---

### Post by SeanBlader on 2009-08-10
> **taavikko said:**
> My chart shows that this laptop is a piece of junk...
even when splash removed and concurrency set to shell

And when you add the login->desktop it's a whole lotta more... :)

Taavikko, it looks to me like all you need is a faster hard drive. Notice how the disk utilization is mostly capped throughout boot? If you really want to embarrass windows with your boot times, an SSD in there will make the DV5 absolutely scream. Then you'd be waiting on the Athlon to keep up, but you'd probably be looking at a sub 10 second bootchart.

I attached mine from my relatively slow 1.4ghz Dell Adamo, but with the SSD it comes up with boot times that are faster than significantly more powerful systems. If I could cap out my processor during boot, then I'd be happy. It would probably take more research than I have time for.

---

### Post by wayne_cat on 2009-08-10
> **SeanBlader said:**
> Taavikko, it looks to me like all you need is a faster hard drive. Notice how the disk utilization is mostly capped throughout boot? If you really want to embarrass windows with your boot times, an SSD in there will make the DV5 absolutely scream. Then you'd be waiting on the Athlon to keep up, but you'd probably be looking at a sub 10 second bootchart.

I attached mine from my relatively slow 1.4ghz Dell Adamo, but with the SSD it comes up with boot times that are faster than significantly more powerful systems. If I could cap out my processor during boot, then I'd be happy. It would probably take more research than I have time for.

wow ... 11 seconds ... there it is (almost) ... the 10 seconds milestone.

---

### Post by tekstr1der on 2009-08-10
> **wayne_cat said:**
> wow ... 11 seconds ... there it is (almost) ... the 10 seconds milestone.

I sure hope the are not using an SSD based system as the standard by which to achieve the 10 second boot goal.

---

### Post by taavikko on 2009-08-10
> **tekstr1der said:**
> I sure hope the are not using an SSD based system as the standard by which to achieve the 10 second boot goal.

The reference machine for the boot was "dell mini 9" or something like that, which contains a 8GB SSD disk.
This is wrong way to go, IMHO.

Although I would like to have one good SSD disk, don't like spending 300€ for it.
And would prefer not to buy "dell mini 9" just to see boot speed increases ;)

---

### Post by wayne_cat on 2009-08-10
> **taavikko said:**
> The reference machine for the boot was "dell mini 9" or something like that, which contains a 8GB SSD disk.
This is wrong way to go, IMHO.

Although I would like to have one good SSD disk, don't like spending 300€ for it.
And would prefer not to buy "dell mini 9" just to see boot speed increases ;)

yes ... the dell with a SSD is the reference system

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html)

---

### Post by tekstr1der on 2009-08-10
> **wayne_cat said:**
> yes ... the dell with a SSD is the reference system

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html)

Oh my! I remember it was a netbook, but I never looked at the full spec. Popping an SSD into even the slowest (read Atom) system is going to boost boot times considerably for any OS.

On the positive side, the Dell Mini 9 has a crappy SSD implementation. On the negative side, I guess I can just forget about my SSD-less netbook booting in 10 seconds then.

---

### Post by MacUntu on 2009-08-10
> **wayne_cat said:**
> wow ... 11 seconds ... there it is (almost) ... the 10 seconds milestone.

Don't wanna spoil the party, but 10 seconds are the target for a full boot to desktop. :P

> **SeanBlader said:**
> Taavikko, it looks to me like all you need is a faster hard drive. 

If you have spare SSDs, I'll take one too. :KS:P I think six seconds should be possible considering all the red stuff: [http://img.xrmb2.net/images/538478.png](http://img.xrmb2.net/images/538478.png)

---

### Post by infamousrev on 2009-08-10
> **taavikko said:**
> The reference machine for the boot was "dell mini 9" or something like that, which contains a 8GB SSD disk.
This is wrong way to go, IMHO.

Although I would like to have one good SSD disk, don't like spending 300€ for it.
And would prefer not to buy "dell mini 9" just to see boot speed increases ;)

I have a Asus 1000HE with a fast SSD drive and 2 gb memory.

Here is my bootchart, cpu seems to limit it.

---

### Post by infamousrev on 2009-08-10
> **tekstr1der said:**
> Oh my! I remember it was a netbook, but I never looked at the full spec. Popping an SSD into even the slowest (read Atom) system is going to boost boot times considerably for any OS.

On the positive side, the Dell Mini 9 has a crappy SSD implementation. On the negative side, I guess I can just forget about my SSD-less netbook booting in 10 seconds then.


CPU is an issue as well so optimization for that is good for my netbook :)

---

### Post by wayne_cat on 2009-08-10
> **MacUntu said:**
> Don't wanna spoil the party, but 10 seconds are the target for a full boot to desktop. :P


Just saw it in the specs ... thats really bad .. they will have to fiddle around with a lot of things.

---

### Post by infamousrev on 2009-08-10
Just noticed my boot process is sleeping for 5 seconds without aperant reason.

> [    2.193671] [drm] LVDS-8: set mode 1024x600 e
[    2.874401] xor: automatically using best checksumming function: pIII_sse
[    2.892016]    pIII_sse  :  4984.000 MB/sec
[    2.892022] xor: using function: pIII_sse (4984.000 MB/sec)
[    2.898329] device-mapper: dm-raid45: initialized v0.2594b
[    3.124163] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.124189] ATL1E 0000:03:00.0: setting latency timer to 64
[    8.714682] EXT4-fs (sda8): barriers enabled
[    8.721232] kjournald2 starting: pid 1169, dev sda8:8, commit interval 5 seconds
[    8.721277] EXT4-fs (sda8): delayed allocation enabled
[    8.721285] EXT4-fs: file extents enabled
[    8.722679] EXT4-fs: mballoc enabled
[    8.722707] EXT4-fs (sda8): mounted filesystem with ordered data mode



Any ideas what causes this?

---

### Post by MacUntu on 2009-08-10
> **wayne_cat said:**
> they will have to fiddle around with a lot of things.
Sounds like fun. :D Upstart in charge, session start improved...  even if the sights are set high, I'm sure Karmic+1 will be a blast. :)

> **infamousrev said:**
> Just noticed my boot process is sleeping for 5 seconds without aperant reason. Any ideas what causes this?
Maybe this is the problem: [http://ubuntuforums.org/showpost.php?p=6562165&postcount=3](http://ubuntuforums.org/showpost.php?p=6562165&postcount=3)

---

### Post by taavikko on 2009-08-10
I have these hickups on my boot scene

```
[    2.796973] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.190893] udev: starting version 145

```
that's 2,4 seconds

```
[   11.560370] type=1505 audit(1249918541.023:8): operation="profile_load" pid=2012 name=/usr/sbin/tcpdump
[   14.864553] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
```
that's 3,3 seconds

```
[   14.889542] Bridge firewalling registered
[   17.182088] [drm] Setting GART location based on new memory map

```
that's 2,3 seconds

```
[   17.456518] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.915229] CPU0 attaching NULL sched-domain.
[
```
that's 2,4 seconds

there are some serious tweaking ahead :)

Luckily I hardly care if the boot takes a 25s or 45s since the real performance should be focused on the desktop usage.

---

### Post by infamousrev on 2009-08-10
> **MacUntu said:**
> Sounds like fun. :D Upstart in charge, session start improved...  even if the sights are set high, I'm sure Karmic+1 will be a blast. :)


Maybe this is the problem: [http://ubuntuforums.org/showpost.php?p=6562165&postcount=3](http://ubuntuforums.org/showpost.php?p=6562165&postcount=3)


Thank you, your advise just made my bootup 5 seconds faster :)

---

### Post by shafin on 2009-08-10
After moving to 2.30 kernel+ext4 in jaunty, I'm getting close to 16 s in a normal 7200rpm HDD. And my boot includes a lot of process that are not installed by default. What is more remarkable,I upgraded this system from Hardy>Intrepid>Jaunty. Installed bootchart in intrepid, so here are two for comparison, see that the time almost got half.

I certainly hope that the upgrade to Karmik will see it shed these 6s.

---

### Post by MrQuantum on 2009-08-10
Hi@all!

I'm new to this forum and want to post the bootchart (karmic koala Xfce up to date) for my system: I've a ThinkPad X40 with Pentium M 1.5 Ghz, 16 GB Transcend SSD,

[COLOR=Blue][COLOR=Black]my boot time is[/COLOR]** 14.5 s**.[/COLOR]

Thank's to all developers, keep up the good work! :biggrin:

Chris

---

### Post by celticbhoy on 2009-08-10
32.13 on aspire one 120G hd model.

---

### Post by Starks on 2009-08-10
I hope this topic is helping the data-starved boot devs.

---

### Post by autocrosser on 2009-08-10
Well--the new rebuild I did last week finally shows some improvement...23 sec...

---

### Post by infamousrev on 2009-08-11
ASUS 1000HE
Intel Atom 280N

[COLOR=Red]Boot time: 10s[/COLOR]

---

### Post by FraggedLocust on 2009-08-11
mine's around 23 - 30 seconds. I noticed on my desktop it hit 17 seconds regularly with Karmic Alpha 2.

---

### Post by Sub101 on 2009-08-11
31 secs.

---

### Post by xagapiou on 2009-08-11
Jaunty: 0.31
Karmic: 0.17

Same hardware

---

### Post by ghindo on 2009-08-14
22 seconds.  Not too shabby.  Anybody know why there are multiple instances of "devkits-disks-pa" and "blkid" appearing?

---

### Post by wayne_cat on 2009-08-14
> **ghindo said:**
> 22 seconds.  Not too shabby.  Anybody know why there are multiple instances of "devkits-disks-pa" and "blkid" appearing?

how many partitions do you have?

```
root@macbook:/etc# blkid 
/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sda2: UUID="3e35fc08-9a5b-3bc8-8f8e-acbeb12f8c47" LABEL="Leopard" TYPE="hfsplus" 
/dev/sda3: LABEL="Karmic" UUID="5ce9e0fc-200a-4a75-affd-3b682ff87444" TYPE="ext3" 
/dev/sda4: UUID="62ebc5d2-5e34-43fb-8e53-b4a2ea7eb60d" TYPE="ext3" 
/dev/sda5: LABEL="Chroot" UUID="04c56e06-3db5-4c99-8f3b-790e0b458b7e" TYPE="ext3" 
/dev/sda6: LABEL="Data" UUID="a3add5da-bd81-4c27-9ede-a9ee0d9aa232" TYPE="ext4" 
/dev/sda7: LABEL="Export" UUID="e071be62-e1a9-4471-95e1-bd36f57efa8c" TYPE="ext4" 
root@macbook:/etc# 

```

---

### Post by ghindo on 2009-08-14
> **wayne_cat said:**
> how many partitions do you have?Three:  /, /home, and swap.  / and /home are ext4.
**EDIT:** Although I do have about 14 gigs unallocated on my hard drive.

---

### Post by Starks on 2009-09-22
Increased 7 seconds since August...

[http://img176.imageshack.us/img176/2191/kingfisherkarmic2009092.png](http://img176.imageshack.us/img176/2191/kingfisherkarmic2009092.png)

---

### Post by Longinus00 on 2009-09-22
My bootup hasn't really changed much from jaunty. I blame it on my slow laptop hard drive.

On my desktop I get 17 or so seconds in virtualbox but I don't have a copy of that right now.

---

### Post by hgergo on 2009-09-22
since the last update boot is 45 sec :|

---

### Post by Longinus00 on 2009-09-22
> **hgergo said:**
> since the last update boot is 45 sec :|

It looks like your computer is sleeping for a good 10 seconds there. Any idea what that is about?

---

### Post by taavikko on 2009-09-22
Hmm, not too bad performance. without autologin...

---

### Post by hgergo on 2009-09-22
hmm the gdm is not starting i mut pres alt f8 and than f7 or wht the conbintion is to start it

---

### Post by LiquidMeson on 2009-09-22
5 seconds.

---

### Post by Squonk07 on 2009-09-22
0:28 here. Of course, it's rather meaningless as I have nothing else with which to compare it. It's a good benchmark for the future, at any rate. Not exactly blowing the doors off anything, but still under 0:30.

[CENTER][ATTACH]129395[/ATTACH][/CENTER]

---

### Post by excogitation on 2009-09-22
0:58 on a Vaio P11Z - Atom Z520 (1.33GHz) with 1.8" hdd

btw - wouldn't it be a good idea to implement an upload statistics feature in bootchart?
I'd like to have a look at such a database ;-)

---

### Post by Jay_Bee on 2009-09-22
Unfortunately my boot times regressed with recent updates and ubuntu now takes about 20 seconds longer to boot. It was around 20 seconds in Karmic alpha 2 and now it takes around 40.

---

### Post by Compintuit on 2009-09-22
Well, after installing bootchart, I got confirmation that it wasn't just the stopwatch on my ipod speeding up the clock while I booted. 39 seconds. I saw few worse bootcharts :( Really, I just want to be up in 20 seconds, browsing the web in 25. But, ohhh I hate my BIOS's 9.7s start time.

---

### Post by solitaire on 2009-09-22
Average time for my Jaunty was +/-30 sec
First boot with all today's updates (udev fixed) was 23 Seconds
^_^
Probably a few things i could shut down but the Karmic install is virtually clean...

System is a HP 550 (Celeron 2Ghz with 1Gb ram).
Need to up the ram to 4Gb sometime soon!

---

### Post by excogitation on 2009-09-23
opposed to yesterday ... it now takes twice as long to boot ...

---

### Post by Nickedynick on 2009-09-23
I get 1:13 now from GRUB to desktop. To be fair, that's also with 4 or 5 of my own programs loading (Skype, Dropbox, etc.) so it'd probably be closer to a minute as a default install.

I'm glad they changed bootchart - it's far more useful now.

---

### Post by cyberkilla on 2009-09-23
[COLOR="Silver"]No bootchart done yet - it keeps giving me errors and preventing boot.[/COLOR]

Still, I have used a stopwatch to count the time it takes to boot. I know they are shooting for karmic+1 all of a sudden, but this is still pretty bad on my hardware - Vista boots faster.

**63.4** seconds to get from just after I press return on the GRUB screen until the Karmic xsplash thing actually appears. There is a large chunk of this time when the screen is just blank (I might as well be seeing the console).

**18.9** seconds to get from the beginning of the xsplash until the GDM login screen appears. The OS is still loading in the background too. Damn, it's slow.

I'll get the timings for Vista again, and append them to this post if I have the time.

The hardware isn't so bad (not state-of-the-art, but under 2 years old):
- Sony Vaio VGN-AR41E
- Intel Core2 Duo @1.80GHz
- 2GB 667MHz Kingston RAM
- 120GB HDD (standard laptop RPM)
- NVidia GeForce 8400M GT ~256MB VRAM

I suppose my concern isn't actually with the overall time, but with the fact that the splash screen appears too late to be useful.

Has anybody gauged the overhead that _usplash_ incurs? I can't imagine it adding more than a couple of seconds to load. If I'm waiting over a minute before I even see a splash screen, I might as well be seeing usplash. 
Didn't usplash even provide a progress bar, to actually depict boot progress?

What is the overall plan here? I'm confused.:P

EDIT: I have a bootchart now. Is there anything unique about my case? Something I can remove to speed things up a bit? Thanks in advance.

EDIT #2: I have managed to shave some time off by enabling autologin. I thought I'd upload that one too..

---

### Post by Hairy_Palms on 2009-09-23
a fair bit slower than jaunty here, hopefully itll pick up before release, though i should say i never installed xpslash and am still chugging along fine with usplash

---

### Post by shakaran on 2009-09-23
1' 58'' I break the mean! :(

---

### Post by godhika on 2009-09-23
> **excogitation said:**
> opposed to yesterday ... it now takes twice as long to boot ...

It's not a bug it's a feature. If you look at your bootcharts after this mornings update you will see that bootchart now measures the time until every service is running (panels,compiz etc....). So your boot time should actually stayed the same, bootchart measures it only more accurately now - so finally no more lying to ourselves.

---

### Post by Longinus00 on 2009-09-23
> **godhika said:**
> It's not a bug it's a feature. If you look at your bootcharts after this mornings update you will see that bootchart now measures the time until every service is running (panels,compiz etc....). So your boot time should actually stayed the same, bootchart measures it only more accurately now - so finally no more lying to ourselves.

Okay, I was just about to post some weird bootchart bug because I could swear the computer wasn't taking *that* long to boot up.

Does this make bootchart less useful for people that don't do automatic login? If they have to try to type their passwords as fast as possible it's going to be hard to keep their bootcharts consistent.

Also, even with automatic login on, there seems to be lots of downtime where the computer isn't doing much of anything anymore.

---

### Post by celticbhoy on 2009-09-23
Last check August 10th - 32secs

Now with new Bootchart & updates I get a paltry 1:31 secs


:cry:

---

### Post by cyberkilla on 2009-09-23
> **celticbhoy said:**
> Last check August 10th - 32secs

Now with new Bootchart & updates I get a paltry 1:31 secs


:cry:

It has been explained above several times. The timeframe it records is longer now, as it counts until your system is completely booted.

---

### Post by solitaire on 2009-09-23
> **celticbhoy said:**
> Last check August 10th - 32secs

Now with new Bootchart & updates I get a paltry 1:31 secs


:cry:


Owch!!

Mine went from 23s (after yesterday's updates!)  to 1m10s (after today's updates!!) >_<

Though the boots are timing 2 different things (I think) Old bootchart was to the login screen and the new one times it all the way to a working desktop.

But I still like to get it sub 60s (might have to get an SSD) >_< boo! lol

---

### Post by celticbhoy on 2009-09-23
> **cyberkilla said:**
> It has been explained above several times. The timeframe it records is longer now, as it counts until your system is completely booted.

I did read above, and realize that bootchart now times until the full desktop has loaded. I just meant to the difference is quite considerable, and compared to others on this thread is a very poor time.

---

### Post by godhika on 2009-09-23
> **celticbhoy said:**
> I did read above, and realize that bootchart now times until the full desktop has loaded. I just meant to the difference is quite considerable, and compared to others on this thread is a very poor time.

Well the new bootchart is only around since a few hours, to compare your times with those posted before is more or less a meaningless exercise (ok, not totaly meaningless if you take a closer look at the bootcharts, but only looking at the total time is like comparing apples with oranges). And if you look at the last few times posted you are not that bad off.

---

### Post by excogitation on 2009-09-23
I think it would be a good idea to also include the time to where it was measured before to keep the comparability.

---

### Post by Longinus00 on 2009-09-23
I guess they could have two separate bootcharts. One that only goes until where the previous version stopped, and one that goes until login. This way everyone is happy.

---

### Post by orlox on 2009-09-23
Mine takes something like ~128s

---

### Post by Longinus00 on 2009-09-23
Okay, I've noticed something weird going on. When exactly does bootchart decide that it's time to end the timer? 

Running karmic in VBOX I timed my bootup (from after sunbios fade to desktop) to around 23 seconds. My bootchart says 1 minute but it's obviously counting lots of stuff after I've already gotten into gnome. You can see in the boot chart that I'm using firefox for more than 30 seconds without it counting as having finished booting.

*edited example*

---

### Post by blakamin on 2009-09-23
Mine is just scary...

---

### Post by Schrotthaufen on 2009-09-23
Is this new bootchart a bug or a feature?

---

### Post by NCLI on 2009-09-23
I'm pretty sure it's a feature added in preparation for measuring how close we can get to 10s in Lucid.

---

### Post by philinux on 2009-09-23
Last one of mine was 1.02 mins to Desktop.

---

### Post by Longinus00 on 2009-09-23
> **NCLI said:**
> I'm pretty sure it's a feature added in preparation for measuring how close we can get to 10s in Lucid.

Currently it keeps counting even after you're done booting up. My bootchart show me browsing firefox for 30 seconds before it decides that I've finished booting.

---

### Post by philinux on 2009-09-24
I just time my boot up and it was 23 seconds to the login screen and 7 seconds to desktop. And the desktop was responsive ie firefox fired up straight away. There was still some disk activity.

Bootchart png file had not even turned up at this stage. It eventually showed with a time of 1min 7secs.

---

### Post by dxxvi on 2009-09-24
Yeah, I also see swiftfox in my boot chart (67 secs).

---

### Post by wfp on 2009-09-24
Looks like a minute and seven seconds to me. Maybe too much Vodka again tonight. For me that is. Looks like  sreadahead is still giving you problems

---

### Post by MacUntu on 2009-09-24
Looks more like 34 seconds to me - don't concentrate on the 'time:'-value as bootchart runs longer than needed. Just look at I/O- and CPU-load - if your system is idling, it's most likely done with loading the session. ;)

---

### Post by dadedo123 on 2009-09-24
Why does the  bootchart differ a lot from a computer to another?

---

### Post by andrewabc on 2009-09-24
> **dadedo123 said:**
> Why does the  bootchart differ a lot from a computer to another?

Different hardware. Old computers take longer. Also with different hardware you get different drivers. People with Solid state drives will have 1/2 boot time as normal hard drives.

Some people have different software installed or running on boot, so that would also change what is running.

---

### Post by bear24rw on 2009-09-24
Does anyone else have a problem with bootchart not generating images? It generated the tgz but no png. This is happening on both my computers and a friends all of which are up to date karmics

---

### Post by tjeremiah on 2009-09-27
dont have bootchart but timed it myself and it ranges from 15 - 20 seconds.

---

### Post by maestrobwh1 on 2009-09-27
For those of you have a expresscard slot and your bios recognizes it at boot time:

Installing Karmic (using Kubuntu here) on a UDMA (using a Kingston 266X) supported CF card in an expresscard reader, I am seeing boot times and performance way less "laggy" than my similarly equipped desktop (processor and ram are about the same).  Boot time on my laptop is about 20 seconds.  Desktop with SATA standard drive is about 45.

I mention this because the CF card (8GB) and the reader cost me a total of about $75 and rival the performance of an SSD, AND you can keep whatever is installed on your HD without touching it.  I took my HD out prior to the install, which slowed down the install because both bios and the Karmic CD were giving some ATA device not found warnings during startup.  Still, I like having two disks with bootloaders in case something goes awry with a dis. I also forced grub to remap the drives after I put the drive back in.  (sudo grub-mkdevicemap)

I also experimented it by installing Karmic on a 4 GB micro SD card in a usb reader.  Boot time is fast, and it seems to operate normally EXCEPT much like in the past, if too much r/w happens at the same time (i.e. package upgrades/installs), you will get the typical slowdown from a USB device.  Browsing the net and such with no other operations going on are excellent however.  Hardy was almost unusable when installed in this fashion when using the net (it may have been the version of Firefox at the time as well).

---

### Post by seamuso on 2009-09-27
How to shave 45 seconds from your bootchart .. 

```
sudo nano /etc/init/bootchart.conf
```

comment out this section ```

#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script


```

Before -[ATTACH]129954[/ATTACH]

After - [attach]129953[/attach]

---

### Post by andrewabc on 2009-09-27
> **seamuso said:**
> How to shave 45 seconds from your bootchart .. 

```
sudo nano /etc/init/bootchart.conf
```

comment out this section ```

#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script


```


That's quite the disk throughput spike at 191 and 258mb/s
Do you have an SSD or is it just an anomaly?
I'm guessing not an SSD if boottime takes 28 seconds. It takes me 19 seconds on jaunty with normal hard drive, and my processor is worse than yours. Glad you found where to edit out the extra time. Makes image too big and larger filesize unnecessarily. I could see a couple seconds maybe, but 45 is silly.

---

### Post by seamuso on 2009-09-27
> **andrewabc said:**
> That's quite the disk throughput spike at 191 and 258mb/s
Do you have an SSD or is it just an anomaly?
I'm guessing not an SSD if boottime takes 28 seconds. It takes me 19 seconds on jaunty with normal hard drive, and my processor is worse than yours. Glad you found where to edit out the extra time. Makes image too big and larger filesize unnecessarily. I could see a couple seconds maybe, but 45 is silly.

It's probably my raid starting up and mounting .. 4x500GB disk raid5 ntfs-3g (shared data/storage drive win7/Ubuntu)
```

/dev/mapper/nvidia_cjfahbac:
 Timing buffered disk reads:  748 MB in  3.00 seconds = 248.95 MB/sec

/dev/mapper/nvidia_cjfahbac:
 Timing cached reads:   7882 MB in  2.00 seconds = 3944.25 MB/sec

```

---

### Post by momo971 on 2009-09-27
> **seamuso said:**
> How to shave 45 seconds from your bootchart .. 

```
sudo nano /etc/init/bootchart.conf
```

comment out this section ```

#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script


```


Bootcharts with i5 750 and 32GB SSD !

Before 54 sec [ATTACH]129971[/ATTACH]

After  8 sec [ATTACH]129972[/ATTACH]

---

### Post by solitaire on 2009-09-27
> **seamuso said:**
> How to shave 45 seconds from your bootchart .. 

```
sudo nano /etc/init/bootchart.conf
```comment out this section ```

#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script


```Before -[ATTACH]129954[/ATTACH]

After - [attach]129953[/attach]


Hmm... This might be just me, But I can't find that file anywhere!?! >_<
I don't have a /etc/init/ folder but got a /etc/init.d/ one
and no bootchart.conf file anywhere! :(

---

### Post by momo971 on 2009-09-27
> **solitaire said:**
> Hmm... This might be just me, But I can't find that file anywhere!?! >_<
I don't have a /etc/init/ folder but got a /etc/init.d/ one
and no bootchart.conf file anywhere! :(

Just in case, did you install bootchart ?

```
sudo apt-get install bootchart
```

---

### Post by dadedo123 on 2009-09-27
> **seamuso said:**
> How to shave 45 seconds from your bootchart .. 

```
sudo nano /etc/init/bootchart.conf
```

comment out this section ```

#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script


```

Before -[ATTACH]129954[/ATTACH]

After - [attach]129953[/attach]
Wow! cool! Will this command mess up my pc?

---

### Post by MacUntu on 2009-09-27
No, it will do exactly nothing else than reduce the size of your bootchart and the number shown next to "time:". It won't reduce your boot time.

---

### Post by solitaire on 2009-09-27
> **momo971 said:**
> Just in case, did you install bootchart ?

```
sudo apt-get install bootchart
```


yes! it's installed (see earlier in the thread for my charts!)
[B]
*update*
[slaps head]Urgh! [/slaps head]
Helps if i'm in the correct OS!! D'oh!
I was in 9.04 that's why I could not find the files!! lol[/B]

---

### Post by seamuso on 2009-09-27
> **MacUntu said:**
> No, it will do exactly nothing else than reduce the size of your bootchart and the number shown next to "time:". It won't reduce your boot time.

I just posted it because it gives a way to get times back into context with the times in the original posts in the thread.

The real question is that by giving it a 45sec sleep time, if a system has completed the boot before that 45sec time is up, does the bootchart time take that into consideration? If my real boot time is 28s + 15s (to the point the sleep is allowing the system to reach), am I going to see 43s or 113s (to the end of the 45s sleep).

---

### Post by MacUntu on 2009-09-27
> **seamuso said:**
> The real question is that by giving it a 45sec sleep time, if a system has completed the boot before that 45sec time is up, does the bootchart time take that into consideration?
No. How it's done now is just the easiest way to deal with ppl having different startup applications, daemons or whatever to run. There's no defined end-point so there's this 45 sec. sleep.

When the plots show no I/O- and CPU-activity, you can consider your session usable. You can subtract the timespan from that point to the end of the chart from those 45 sec., but commenting out that whole line will - on many systems - cut off the bootchart way before the session's loaded. :)

---

### Post by seamuso on 2009-09-27
> **MacUntu said:**
> No. How it's done now is just the easiest way to deal with ppl having different startup applications, daemons or whatever to run. There's no defined end-point so there's this 45 sec. sleep.

When the plots show no I/O- and CPU-activity, you can consider your session usable. You can subtract the timespan from that point to the end of the chart from those 45 sec., but commenting out that whole line will - on many systems - cut off the bootchart way before the session's loaded. :)

With the sleep time set for 120s -

boot time is now 2:23s

[ATTACH]130006[/ATTACH]

I think that bootchart is waiting for itself to finish and counting that as part of the startup time

---

### Post by cimh on 2009-10-02
Well I prefer to measure from switch on to usable desktop by hand - it saves a lot of bother and its exactly what interests me.

Karmic beta is taking 50-60s whereas 9.4 was under 40s. So I tend to agree with most people on this list - karmic is slower not faster than 9.04 - lets hope they can improve things before launch.

cimh
asus eee 901

---

### Post by cimh on 2009-10-02
> **cimh said:**
> Karmic beta is taking 50-60s whereas 9.4 was under 40s. So I tend to agree with most people on this list - karmic is slower not faster than 9.04 - lets hope they can improve things before launch.


this link enabled me to instantly lower the boot time from 60 to 35s 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1658344.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1658344.html)

the problem seems to be sreadahead disabling it leads to a dramatic speed up.

cimh
asus eee 901

---

### Post by vredley on 2009-10-02
> **cimh said:**
> Well I prefer to measure from switch on to usable desktop by hand - it saves a lot of bother and its exactly what interests me.

Karmic beta is taking 50-60s whereas 9.4 was under 40s. So I tend to agree with most people on this list - karmic is slower not faster than 9.04 - lets hope they can improve things before launch.

cimh
asus eee 901
Jaunty took about 43 seconds to boot into GNOME/Metacity on my Eee 4G, while Karmic boots in around 50. Disabling kernel mode-setting and Xsplash brought it down to 44, but it ain't a pretty sight.

---

### Post by MacUntu on 2009-10-02
One step back, two steps forward. :)

---

### Post by cimh on 2009-10-02
> **vredley said:**
> ...Karmic boots in around 50. Disabling kernel mode-setting and Xsplash brought it down to 44, but it ain't a pretty sight.

Disabling xsplash brings me down to 30s!! - thanks for the tip

how do you disable kms - does everything work fine if I do?

cimh
901

---

### Post by Longinus00 on 2009-10-02
Some these workarounds are getting pretty ridiculous. Disabling KMS? sreadahead? Just take out that parameter on bootchart that was mentioned a few pages back and marvel at your faster boot times.

---

### Post by jmmL on 2009-10-02
> **Longinus00 said:**
> Some these workarounds are getting pretty ridiculous. Disabling KMS? sreadahead? Just take out that parameter on bootchart that was mentioned a few pages back and marvel at your faster boot times.

Maybe my sarcasm-o-meter is off, but that change to bootchart just stopped it recording 45 seconds of data - it didn't make anyone boot any quicker. So the charts generated were shorter because they only recorded the kernel booting to gdm, whereas the default (now) is to record an extra 45 seconds on top of this just to see what's happening as users log in.

I don't disagree with you fundamentally - I'm not thrilled at the boot performance of karmic. I do however reckon that my boot (grub to completed desktop) has gone from 90 seconds with jaunty to about 75 with karmic - a noticeable improvement. It feels like there's going to be a lot of work needed for the 10s SSD / 15s HDD boots for lucid.

---

### Post by Longinus00 on 2009-10-02
> **jmmL said:**
> Maybe my sarcasm-o-meter is off, but that change to bootchart just stopped it recording 45 seconds of data - it didn't make anyone boot any quicker. So the charts generated were shorter because they only recorded the kernel booting to gdm, whereas the default (now) is to record an extra 45 seconds on top of this just to see what's happening as users log in.

I don't disagree with you fundamentally - I'm not thrilled at the boot performance of karmic. I do however reckon that my boot (grub to completed desktop) has gone from 90 seconds with jaunty to about 75 with karmic - a noticeable improvement. It feels like there's going to be a lot of work needed for the 10s SSD / 15s HDD boots for lucid.

I was indeed being very sarcastic. There are already people out there with 10s ssd bootcharts but I haven't heard anything about progress into faster hdd boot times.

---

### Post by vredley on 2009-10-02
> **cimh said:**
> Disabling xsplash brings me down to 30s!! - thanks for the tip

how do you disable kms - does everything work fine if I do?

cimh
901

To check whether your system will run without KMS, you can make a temporary change to GRUB. Press and hold Shift before GRUB starts and the menu should appear. Press 'e' to edit the first (default) entry in the menu, use the arrow keys to move down to the line beginning with 'linux', and add 'nomodeset' to the end, after 'quiet splash'. Then press Ctrl+x to boot.

If nothing explodes, you can make this change permanent. Open /etc/default/grub, go to the GRUB_CMDLINE_LINUX_DEFAULT line, and add 'nomodeset' to the part in quotes. Save the file, run 'sudo update-grub', and Bob should theoretically be your uncle.

(EDIT: After the latest updates, it now boots faster with KMS enabled. I'm down to 39 seconds. :D )

> **Longinus00 said:**
> Some these workarounds are getting pretty ridiculous.

The challenge is irresistible. :)

---

### Post by Longinus00 on 2009-10-02
> **vredley said:**
> To check whether your system will run without KMS, you can make a temporary change to GRUB. Press and hold Shift before GRUB starts and the menu should appear. Press 'e' to edit the first (default) entry in the menu, use the arrow keys to move down to the line beginning with 'linux', and add 'nomodeset' to the end, after 'quiet splash'. Then press Ctrl+x to boot.

If nothing explodes, you can make this change permanent. Open /etc/default/grub, go to the GRUB_CMDLINE_LINUX_DEFAULT line, and add 'nomodeset' to the part in quotes. Save the file, run 'sudo update-grub', and Bob should theoretically be your uncle.



The challenge is irresistible. :)

Well, you could also instruct him on how to physically remove KMS from the kernel and recompile it. Also enabling BFS in the process.

---

### Post by MacUntu on 2009-10-02
Running sreadahead in the foreground doesn't reduce the boot time significantly so I guess the pack file is not yet optimized for HDDs (files sorted by block numbers).

I'd also like to point to this bug (or better call it task): [https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/432089](https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/432089)

---

### Post by vredley on 2009-10-02
> **Longinus00 said:**
> Well, you could also instruct him on how to physically remove KMS from the kernel and recompile it. Also enabling BFS in the process.
Ah, now you're being silly. :p

If hacks and mods get your blood pressure up, you wouldn't last five minutes in the Eeeuser forums. One member was (seriously?) thinking about drilling a load of holes in the case to make it lighter. :)

---

### Post by Longinus00 on 2009-10-02
> **vredley said:**
> Ah, now you're being silly. :p

If hacks and mods get your blood pressure up, you wouldn't last five minutes in the Eeeuser forums. One member was (seriously?) thinking about drilling a load of holes in the case to make it lighter. :)

Well, I was kinda serious about the BFS part. ;)

---

### Post by renkinjutsu on 2009-10-02
Make wayy!! jaunty coming through!:P

---

### Post by jmmL on 2009-10-02
> **renkinjutsu said:**
> Make wayy!! jaunty coming through!:P

Nice time. I was getting ~14 seconds kernel boots (on spinning media) with -30 in jaunty. I'm on about ~21 with karmic now, which coincidentally is about what I got with -28 in jaunty.
Are you using a HDD or SSD for those times? It has a high peak transfer rate.

As a side note, it would be nice if bootchart could record information about the disk as well - make, model, capacity. It would probably be more useful than the CPU information we currently have, as boot is disk-bound.

---

### Post by renkinjutsu on 2009-10-02
> **jmmL said:**
> Nice time. I was getting ~14 seconds kernel boots (on spinning media) with -30 in jaunty. I'm on about ~21 with karmic now, which coincidentally is about what I got with -28 in jaunty.
Are you using a HDD or SSD for those times? It has a high peak transfer rate.

As a side note, it would be nice if bootchart could record information about the disk as well - make, model, capacity. It would probably be more useful than the CPU information we currently have, as boot is disk-bound.

```
 *-disk
       description: ATA Disk
       product: Hitachi HDT72101
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: ST6O
       serial: STF607MH1S8MRW
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000b7cb
```
then
```
*-volume
       description: Extended partition
       physical id: 1
       bus info: scsi@0:0.0.0,1
       logical name: /dev/sda1
       size: 931GiB
       capacity: 931GiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume:0
          description: Linux swap / Solaris partition
          physical id: 5
          logical name: /dev/sda5
          capacity: 2384MiB
          capabilities: nofs
     *-logicalvolume:1
          description: Linux filesystem partition
          physical id: 6
          logical name: /dev/sda6
          logical name: /
          capacity: 15GiB
          configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
     *-logicalvolume:2
          description: Linux filesystem partition
          physical id: 7
          logical name: /dev/sda7
          logical name: /home
          capacity: 894GiB
          configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
     *-logicalvolume:3
          description: Linux filesystem partition
          physical id: 8
          logical name: /dev/sda8
          capacity: 18GiB
```

---

### Post by DanaG on 2009-10-02
Hmm, my boot time is way, way way longer than it was in Jaunty.

Edit: ... then again, perhaps it's not all that different, if I include the 45 seconds also with the bootcharts of the old boot method.... but it's still way uglier.  No usplash.

---

### Post by Longinus00 on 2009-10-02
> **renkinjutsu said:**
> Make wayy!! jaunty coming through!:P

Are you running in virtualbox or vmware?

---

### Post by renkinjutsu on 2009-10-02
nope... nothing of that sort

also a little bit of detail: I installed using the minimum install and i disabled GDM and usplash

---

### Post by Ocxic on 2009-10-02
Great improvement from jaunty(25-40sec) to karmic(10sec).
I was like "holy s**t" after the first reboot when the upgrade completed

---

### Post by cecilpierce on 2009-10-02
A few days ago I was getting .24, now its 1.15, how can you guys be down around .15 ?

---

### Post by bear24rw on 2009-10-02
both me and a friends boot times like doubled since the beta

---

### Post by Longinus00 on 2009-10-02
> **cecilpierce said:**
> A few days ago I was getting .24, now its 1.15, how can you guys be down around .15 ?

Bootcharts no longer record boot times, they no record boot time + 45 seconds.

Maybe someone should start a new thread with that in the first post?

---

### Post by cimh on 2009-10-03
A few posts back I reported that removing sreadahead nearly halved my boot time - well it was only temporary and the boot was soon back to 1 minute.

an update to day has really speeded things up - I also went ahead and altered grub to remove splash and added nomodeset. I'm not sure they made a lot of difference but the boot still looks good - no text on screen or flashing just the small swirling cursor. Its very fast - from switch on to desktop 29s!!

thanks for the suggestions 

cimh
asus eee 901 ssd

---

### Post by Melk79 on 2009-10-03
I just upgraded to Karmic and am wondering what happened.  My boot time went to 2:01 from something around 34 sec on Jaunty.  Can anyone tell what is the biggest culprit and how to adjust?  Truth is I don't mind the boot, it has been dressed up very nice and is integrated very well.  Nice transition to the desktop!

---

### Post by Longinus00 on 2009-10-03
> **Melk79 said:**
> I just upgraded to Karmic and am wondering what happened.  My boot time went to 2:01 from something around 34 sec on Jaunty.  Can anyone tell what is the biggest culprit and how to adjust?  Truth is I don't mind the boot, it has been dressed up very nice and is integrated very well.  Nice transition to the desktop!

You bootup times are very similar, karmic just counts where to stop the bootchart differently than jaunty.

---

### Post by celticbhoy on 2009-10-04
> **Melk79 said:**
> I just upgraded to Karmic and am wondering what happened.  My boot time went to 2:01 from something around 34 sec on Jaunty.  Can anyone tell what is the biggest culprit and how to adjust?  Truth is I don't mind the boot, it has been dressed up very nice and is integrated very well.  Nice transition to the desktop!

Jaunty checked to GDM, Karmic checks to full desktop.

---

### Post by lean on 2009-10-04
> **Longinus00 said:**
> You bootup times are very similar, karmic just counts where to stop the bootchart differently than jaunty.

How can you say that, did you even look at the bootchart? Xsplash starts after 45 seconds, this value should be faster than the jaunty boot time.

---

### Post by ~Las~ on 2009-10-04
Here's mine:-).I used to get 40+s in jaunty.

---

### Post by Melk79 on 2009-10-04
Well, I turned off the print queue applet (cause I rarely print anything anyway) and updated today.  Brought it down to 1:14.  I really wish I could get the new splash screen to start sooner.  I have around 15 seconds of a cursor blinking and then the rundown of apparmor and a few other tasks until it starts.  My shutdown got better after the update.  Goes straight to the ubuntu logo and no Nvidia white ugliness right before power off.

---

### Post by andrewabc on 2009-10-04
Jaunty 64 bit OCZ Vertex 60gb. 10 seconds. Aligned to 512kb as per OCZ linux guide.
On hard drive it was 19 seconds. 3 year old computer. ICH8

Karmic beta failed to install to it because of supposed faulty cd. Intel xorg cpu bug made karmic unusable anyway.

---

### Post by renkinjutsu on 2009-10-04
> **andrewabc said:**
> Jaunty 64 bit OCZ Vertex 60gb. 10 seconds. Aligned to 512kb as per OCZ linux guide.
On hard drive it was 19 seconds. 3 year old computer. ICH8

Karmic beta failed to install to it because of supposed faulty cd. Intel xorg cpu bug made karmic unusable anyway.

Hey there!
we have similar speeds, except your boot speed is 1 second faster!
Do you have default ubuntu install?

---

### Post by andrewabc on 2009-10-04
> **renkinjutsu said:**
> Hey there!
we have similar speeds, except your boot speed is 1 second faster!
Do you have default ubuntu install?

Yes default Jaunty install. No updates installed either. I just installed it today and am starting to get all my apps and stuff installed and configured.

I've booted 4 times so far with bootchart. 3/4 bootcharts are 10 seconds. 1 is 11 seconds.

---

### Post by renkinjutsu on 2009-10-04
> **andrewabc said:**
> Yes default Jaunty install. No updates installed either. I just installed it today and am starting to get all my apps and stuff installed and configured.

I've booted 4 times so far with bootchart. 3/4 bootcharts are 10 seconds. 1 is 11 seconds.

my install is a minimum install with some services disabled, but i do have NFS, ssh and apache starting up at boot.. but those shouldn't take long to boot anyway.

Mayhaps the numbers would be different on a 64bit install.. but i'm not sure.. I'm using 32bit jaunty right now, but i'm going to move to 64bit Karmic when it comes out of beta! .. can't wait!


but what i really want to know is why both our peak I/O speeds are so high.. do you have a Hitachi HDD (that's what i have)?

---

### Post by andrewabc on 2009-10-04
> **renkinjutsu said:**
> my install is a minimum install with some services disabled, but i do have NFS, ssh and apache starting up at boot.. but those shouldn't take long to boot anyway.

Mayhaps the numbers would be different on a 64bit install.. but i'm not sure.. I'm using 32bit jaunty right now, but i'm going to move to 64bit Karmic when it comes out of beta! .. can't wait!


but what i really want to know is why both our peak I/O speeds are so high.. do you have a Hitachi HDD (that's what i have)?

320GB Hitachi
Hmm, maybe that is why it is high, like when another guy on here said he had a RAID and that is why his number was so high.

I'll install bootchart to my HDD jaunty install and see if the number is higher now with ssd attached.

EDIT:
Nope, still 53mb/s on hard drive install (19 seconds). so speed is probably correct. It would be read speed.

---

### Post by renkinjutsu on 2009-10-04
> **andrewabc said:**
> 320GB Hitachi
Hmm, maybe that is why it is high, like when another guy on here said he had a RAID and that is why his number was so high.

I'll install bootchart to my HDD jaunty install and see if the number is higher now with ssd attached.

EDIT:
Nope, still 53mb/s on hard drive install (19 seconds). so speed is probably correct. It would be read speed.
wait.. your 10 second boot.. Was that on a harddrive install or SSD?

my install was on a harddrive.. and i'm just wondering why the peak speed is high, because someone pointed it out to me.

---

### Post by andrewabc on 2009-10-04
> **renkinjutsu said:**
> wait.. your 10 second boot.. Was that on a harddrive install or SSD?

my install was on a harddrive.. and i'm just wondering why the peak speed is high, because someone pointed it out to me.

My 10 second bootchart was on SSD.
I'm guessing you have newer hardware than me.

Dunno why your read speed would be so high if only a single hard drive.

---

### Post by praveenmarkandu on 2009-10-04
holy crap. i felt it was long but i didnt expect it to be 70 seconds long. can someone tell me whats wrong with my boot or if im reading it incorrectly.

---

### Post by MacUntu on 2009-10-05
Played around with sreadahead (put into foreground, now back using 128K readahead size) and the pack file (packed and unpacked the files to bring them physically closer together, sorted the list by file's first block number) - down to 23 sec. (was 28 sec.):

[ATTACH]130826[/ATTACH]

> **andrewabc said:**
> My 10 second bootchart was on SSD.
I'm guessing you have newer hardware than me.

Yeah, your "old" hardware is really no match to the SSD. 10 sec. are very good but not mind-blowing for just GRUB->GDM (Karmic's bootchart now runs for the full boot time).

---

### Post by Clifweb on 2009-10-05
Slow boot time aspecialy to load GRUB.

---

### Post by Miguel on 2009-10-05
On my Thinkpad T400 (5400 rpm HDD) I've gone from about 27s to GDM login to about 50. That went down a bit after converting the root partition into ext4. I'm really disappointed with the boot times, although this being an upgrade may have something to do. Kubuntu karmic boots to kdm in about 25 s (or used to).

The current xsplash theme looks bad, load very late and the animation goes far too fast. With kms enabled, I go from standard res to terminus standard res to kms to xsplash to gdm to xsplash to gnome. Those are way too many transitions, and more than I used to see in jaunty.

---

### Post by jm.mico on 2009-10-05
****... 1:37 for my Dell notebook.

I've just updated my Karmic to the beta, and run a "boot race" with my little brother similar vista powered notebook. Very disappointing, I 'want to believe' that this is due to some hardware initialization routines which do not properly work given my hardware (which is though, quite standard)

Any guru having a look at my boot times and pointing out WTF is producing such a loong bot time? 

HD is 5400, 80Gb with 4GB-DDR2 and Core2-2GHz... Should't be that bad or?

Cheers.

Jm

---

### Post by andrewabc on 2009-10-05
WITH NEW BOOTCHART 45 SECONDS IS ADDED AFTER GDM(?).

No one reads the thread?
zomg my bootchart is now 1 minutes instead of 20 seconds...
Someone posted a way to disable the 45 second delay.

---

### Post by MacUntu on 2009-10-06
> **andrewabc said:**
> No one reads the thread?

No one looks at the charts? ;) At least jm.mico's boot time IS that long and the chart looks cut off so it might be even longer. Don't know why, though. :confused:

**Edit:**
Had time to do fresh installs and compared Jaunty final to Karmic beta (up-to-date):

_PC (six years old, 5400rpm hard disk)_
[COLOR="Blue"]Jaunty full boot: 30 seconds[/COLOR] (ign. 7 sec. caused by a BIOS bug)
[COLOR="Red"]Karmic full boot: 30 seconds[/COLOR]

[ATTACH]130976[/ATTACH] vs. [ATTACH]130977[/ATTACH]

_Notebook (three years old, 5400rpm hard disk)_
[COLOR="Blue"]Jaunty full boot - 28 seconds[/COLOR]
[COLOR="Red"]Karmic full boot - 30 seconds[/COLOR]

[ATTACH]130978[/ATTACH] vs. [ATTACH]130979[/ATTACH]

So no real changes between Jaunty and Karmic for those two machines. I'm curious what Lucid will bring... 8-)

---

### Post by jm.mico on 2009-10-06
@MacUntu


Your results sadly mean that there is really something wrong with my boot up times. I will investigate further and try to find the reason/-s.

But, definitely there is someone looking at the charts :)

Jm

---

### Post by Miguel on 2009-10-07
There's something wrong with mine, too. I fear this is caused by a dist-upgrade instead of a clean install, although I'm certainly *not* doing a clean instal in the coming weeks. I've got more important things to do than installing the whole system and reconfiguring it again. But 50s to GDM login suck big time.

EDIT: Here's my bootchart.

---

### Post by asenyshyn on 2009-10-07
Does anybody have idea how to speed this up?

---

### Post by Miguel on 2009-10-07
> **asenyshyn said:**
> Does anybody have idea how to speed this up?

Do a fresh install of Jaunty

EDIT: Don't take it bad, it was meant to be a cynic comment.

---

### Post by asenyshyn on 2009-10-07
> **Miguel said:**
> Do a fresh install of Jaunty

EDIT: Don't take it bad, it was meant to be a cynic comment.

=) actually I'm going to do so after release

---

### Post by cimh on 2009-10-08
Hi for a really impressive karmic boot time I suggest you forget gnome and use LXDE, the results are stunning. My eee is booting from switch on to desktop in 21s. Another member is reporting 18s with his eee901. this suggests that the karmic programmers are really doing their stuff but gnome is real slow. 

LXDE is a lot lighter than gnome and there are disadvantages because of that. boot time isnt very important on a main pc cos most of us leave em on. But it is important on netbooks and if they can keep it at about 20s that truly is amazing for a full blown distro.

The other thing I would say (tongue in cheek) is forget boot chart and use a stop watch. 

cimh
901: karmic LXDE

---

### Post by surfed on 2009-10-10
I have auto-login on but 30 seconds to the desktop is not bad i think...

---

### Post by Miguel on 2009-10-10
> **surfed said:**
> I have auto-login on but 30 seconds to the desktop is not bad i think...

To put that time into context, my T400 laptop (5400rpm HD) takes between 23 and 27s from GDM to a fully loaded default Ubuntu Gnome. That is of course the first login, the next are almost instantaneous. 30s to a fully loaded desktop is a pretty good time (but you have nice hardware).

---

### Post by kimda on 2009-10-10
I tested both my desktop and my new acer timeline (1810T) notebook today.

---

### Post by MacUntu on 2009-10-10
> **kimda said:**
> I tested both my desktop and my new acer timeline (1810T) notebook today.

This couchdb thingy in the second chart is strange. :/

I would check on both machines if the UUID ```
cat /etc/initramfs-tools/conf.d/resume
``` returns matches the one ```
sudo blkid
``` shows for the partition with "TYPE='swap'". If not, change it in the resume file (don't forget to remove the quotes). [Not sure if you need to issue "sudo update-initramfs -u -k all" to make the change work].

---

### Post by kimda on 2009-10-10
Hi MacUntu,

I did like you said, but after rebooting the swap value in blkid and the resume file were different again. I haven't tried it on the laptop. Could it be because my swap is encrypted? 

```

kim@athena:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=742e1837-5093-4749-9024-2a9f1561937d
kim@athena:~$ sudo blkid | grep -i swap
/dev/mapper/cryptswap1: UUID="73e2d99f-4d49-4897-902b-5d1b2fda9e90" TYPE="swap" 

```

---

### Post by MacUntu on 2009-10-10
> **kimda said:**
> Could it be because my swap is encrypted? 

Good question. Possible, but I cannot answer that question for sure, sorry. I only know that different values cause this exec/sleep delay in the beginning of the boot.

---

### Post by kimda on 2009-10-10
I've just checked the notebook. It also has different values like the desktop. Ditching couchdb on the desktop shaved 3 secs of the total boottime of the desktop.

Btw. both are complete new installations.

---

### Post by jmmL on 2009-10-10
I also have that endless couchdb/sleep cycle. If it helps I don't have any swap on this machine whatsoever.

---

### Post by alan2796 on 2009-10-10
Acer Aspire 5610z bit slowe than i would like but maby this is normal ? 
i noticed when i add a CPU Scaling monitor it shows CPU 0 and CPU 1 however that boot chart shows only one CPU is that correct ?

---

### Post by davidryderuk on 2009-10-10
Hi,
I've got an eeepc 1000 (with an ssd drive). Originally I had quite a slow start up. However I then tried the automatic  login mode which was much faster. What's strange though is that after switching back to the manual login mode I'm pretty sure my machine still starts up quicker than it did before. 

I've posted the boot charts below. The times shown are those I timed with a stop watch, so their pretty rough. I've noticed that in the first boot chart sreadahead seems to stay in the background until I've logged in, where as in the third boot chart it exits before the log in screen. 

**Boot 1 - manual login (1:10)**
[ATTACH]131457[/ATTACH]

**Boot 2 - automatic login (0:39)**
[ATTACH]131458[/ATTACH]

**Boot 3 - manual login (0:50)**
[ATTACH]131460[/ATTACH]

---

### Post by imafatmess on 2009-10-10
Karmic is takes over 4 times as long to boot up...

Any ideas why this is?

Jaunty Manual login:
-> [http://ubuntuforums.org/attachment.php?attachmentid=131476&stc=1&d=1255190401](http://ubuntuforums.org/attachment.php?attachmentid=131476&stc=1&d=1255190401)
Karmic Manual login:
-> [http://ubuntuforums.org/attachment.php?attachmentid=131484&stc=1&d=1255190401](http://ubuntuforums.org/attachment.php?attachmentid=131484&stc=1&d=1255190401)
Karmic Auto login:
-> [http://ubuntuforums.org/attachment.php?attachmentid=131484&stc=1&d=1255190401](http://ubuntuforums.org/attachment.php?attachmentid=131484&stc=1&d=1255190401)

---

### Post by Longinus00 on 2009-10-10
> **imafatmess said:**
> Karmic is takes over 4 times as long to boot up...

Any ideas why this is?



Do you mind deleting those [img] links? You already attached the images as thumbnails. It's really messing up the page.

---

### Post by kimda on 2009-10-10
> **imafatmess said:**
> Karmic is takes over 4 times as long to boot up...

Any ideas why this is?


Because gnome startup is included after login. In jaunty it was before login. Hence the longer times.

---

### Post by imafatmess on 2009-10-10
> **kimda said:**
> Because gnome startup is included after login. In jaunty it was before login. Hence the longer times.

I did realise this, however, it still takes at least twice as long as before

Oh and sorry about the huge pictures, I didn't realise

---

### Post by renkinjutsu on 2009-10-10
i just installed Karmic... and even though it boots in LESS time, it boots SLOWER than my jaunty install because Jaunty loaded MORE things than karmic in almost the same amount of time, and there was a higher peak transfer =[

(jaunty bootchart in sig)

---

### Post by GrumpyBob on 2009-10-13
I also see these repeated couchdb cycles in my laptop's bootchart. Very slow boot time, and this is with current Karmic (is this beta).  I've been looking round the forums for a clue as to what do about this...

Robert

---

### Post by Longinus00 on 2009-10-13
> **GrumpyBob said:**
> I also see these repeated couchdb cycles in my laptop's bootchart. Very slow boot time, and this is with current Karmic (is this beta).  I've been looking round the forums for a clue as to what do about this...

Robert

I'm glad I'm not the only one. I made a post about it here but nobody replied.
[http://ubuntuforums.org/showthread.php?t=1284319](http://ubuntuforums.org/showthread.php?t=1284319)

---

### Post by philinux on 2009-10-14
Yep I just noticed this. Boot time went from 1.07 Monday to 2.01 today. Also had white logo then black screen for ages. No xsplash.

Just updating, 128 meg of updates, and will then reboot see if it goes away.

---

### Post by philinux on 2009-10-14
Gone down to 1.12 but couchdb is causing problems still.

---

### Post by davidmohammed on 2009-10-14
my boot chart shows the 20 second delay between usplash and xsplash - any ideas how to reduce the "black" screen interval between these?

---

### Post by wnelson on 2009-10-14
Try the following in /etc/usplash.conf xres=1024 yres=768 to see if lower values than the ones currently in the usplash.conf

---

### Post by davidmohammed on 2009-10-14
...

usplash.conf was empty.  I've tried adding the two params and running "sudo update-usplash-theme usplash-theme-ubuntu" - however no improvement is observed.  

after usplash, a cursor appears for approx 5 secs, then the screen goes black for 10-15 secs before xsplash is displayed.  The HDD light indicates something is constantly occurring (i.e. no pauses).  I suppose there isnt a way to force xsplash to display much earlier in the bootup sequence?

---

### Post by null_pointer_us on 2009-10-15
Ubuntu 9.10 64-bit guest running under VBox 2.2.4 (Vista x64 SP2 host)
Stock install + guest additions 2.2.4 and compiz/3D effects.

Boot activity (to usable desktop) lasts about 23 seconds, after that the chart contains random desktop stuff (presumably from the 45 second delay):

[LIST=1]
[*]Manual Login, forgot I was timing boot -_-'
[*]Auto Login
[*]Auto Login
[/LIST]

Overall, not bad for a VM. :)

EDIT: Speaking of extreme/silly mods, I'm surprised no one tried booting off a RAM disk.

---

### Post by nuovodna on 2009-10-15
Too many secs :(

---

### Post by humphreybc on 2009-10-26
Mine takes forever... 1 min, 8 seconds on relatively fast hardware.

Pretty damn **** if you ask me.

---

### Post by Rob2687 on 2009-10-26
Decent for aging hardware.

[[img]http://u1.imgupload.co.uk/1256601600/thumb_1b2f_robert_laptop_karmic_20091026_1.png[/img]](http://u1.imgupload.co.uk/1256601600/1b2f_robert_laptop_karmic_20091026_1.png)

---

### Post by andrewabc on 2009-10-27
> **humphreybc said:**
> Mine takes forever... 1 min, 8 seconds on relatively fast hardware.

Pretty damn **** if you ask me.

You do know that bootchart adds 45 seconds more than previous bootchart?

---

### Post by philinux on 2009-10-27
> **andrewabc said:**
> You do know that bootchart adds 45 seconds more than previous bootchart?

Thats because the previous bootchart stopped the clock at the GDM. ;)

---

### Post by Miguel on 2009-10-27
> **andrewabc said:**
> You do know that bootchart adds 45 seconds more than previous bootchart?

I don't know if he knows it. What I know is that, from his bootchart, he needed 40s to get into GDM. My T400 (slightly faster processor, probably identical HD speeds) needs 37s to get into KDM. I don't know how much it takes into GDM, since Kubuntu is a clean install, while my ubuntu partition is an upgrade that takes forever to boot.

Still, I'd bet a beer that humphreybc was used 25s into gdm. I mean, that's mostly what I used to see. What this means is that, although faster boot speed is advertised everywhere, many people with traditional HDs are seeing awful boot times. Especially people that have upgraded.

---

