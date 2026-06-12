---
title: "System-&gt;Admin-&gt;Disk Utility-&gt;Benchmark results"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-04-27
Post your benchmark results. I only did read benchmark as it gave error for read/write saying hard drive needs to be empty (I'm running RC on liveusb)

I have asus eeebox b202 160gb 5400RPM

I'm really interested to see what people get and whether this benchmark utility gives 1/2 decent results.

Anyone with SSD please test. I want to see if it gives out numbers similar to what ssd are supposed to provide or if not good for ssd benchmarking. Wondering whether worth it to buy 30gb ssd for eeebox as read/write speeds are slow for obvious reasons (I already have 60gb ssd in main computer).

Oddly it states my hard drive is connected by ATA, but I'm pretty sure it is SATA (ICH7, SATA IDE host controller).

I ran the test on my ocz rally2 usb stick and got 31.1 min read, 34.9 max read, 34mb/s average read. Average access time 0.9ms

[[IMG]http://img442.imageshack.us/img442/6176/screenshot160gbharddisk.th.png[/IMG]](http://img442.imageshack.us/i/screenshot160gbharddisk.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

EDIT:
The ATA thing is probably a bug, as it says all HDD/SSD are ATA for model.

---

### Post by Tweak42 on 2010-04-27
Thanks for pointing out the nifty bench utility feature. :)

Your drive may be showing up under IDE mode if you don't have the controller set to ahci/sata in the bios.  Just beware switching modes can halt a WinXP partition from booting; linux, vista and win7 seem handle switching it ok.

I'm using a 60gb SSD (indilinx barefoot chip), intel sata ICH8M controller.

min: 83.2 MB/s
max: 231.7 MB/s
avg: 192.4 MB/s
avg access: 0.2ms

---

### Post by sdowney717 on 2010-04-27
neat utility
this is my output for a sata 750GB

---

### Post by andrewabc on 2010-04-27
Thanks for the info Tweak42. Glad to see 192 average, I have 60gb indilinx as well. Great stuff, and prices are dropping good now.
Maybe change your signature to say 60gb SSD? :)

Thanks for the HDD benchmark sdowney717

EDIT:
60gb ocz vertex
min 177.5
max 229.7
avg 221.3
access time 0.2ms
Above is good news. I have old firmware(1.3), but I am only using 6gb, so that is probably why so fast.

320gb Hitachi 7200rpm 8mb cache
min 37.2
max 78.5
avg 63.9
access time 13.6 ms

1tb WD caviar green 64mb cache
min 48.8
max 117.9
avg 85.7
access time 14.3 ms

Can anyone confirm if safe to do read/write benchmark? Don't want to screw any of my stuff up.

---

### Post by tokyobadger on 2010-04-27
WD 640G 7200rpm 32M cache
Min 38.6
Max 119.6
Avg 97.3
Acc 12.2

WD 150G Velociraptor 10k rpm 16M cache
Min 45.2
Max 131.3
Avg 106.3
Acc 7.1

WD 150G Raptor 10k rpm 16M cache
Min 51.8
Max 77.0
Avg 68.7
Acc 8.3

Those were first runs - repeat them and the numbers change a bit (not much)

---

### Post by cariboo on 2010-04-27
I got 2X250Gb drives in this system 1 SATA and 1 PATA

---

### Post by tad1073 on 2010-04-28
640gb ATA WDC WD6400AAKS-22A7B0
other specs are in my sig.

---

### Post by Onesimus on 2010-04-28
Wouldn't it be really useful to indicate somewhere on these plots what the green dots and the blue line actually meant ?

Do the green dots refer to the left-hand axis or the right-hand axis ?

Wouldn't it be great if the axes were labelled, rather than just giving units, and expecting the user to guess ?

How do you actually interpret the blue line ?  It just doesn't seem to make sense ?  How can a reading be for 0% of the time, or for that matter 100% of the time ?

From a data analysis point of view it is a poor representation of data.

---

### Post by ViRMiN on 2010-04-28
One of my MD RAID arrays across 3 x ST31500341AS disks:

[IMG]http://i212.photobucket.com/albums/cc195/ViRMiN/Ubuntu/Screenshot-23TBRAID-10Array23TBRAID.png[/IMG]

---

### Post by MacUntu on 2010-04-28
1TB WD Caviar Black WD1001FALS-00E3A0:

Read min: 63.5 MB/s
Read max: 138.3 MB/s
Raad avg: 106.5 MB/s
Access avg: 14.2 ms

[ATTACH]154522[/ATTACH]

Right now Ubuntu is installed at the end of the disk - time to get rid of Windows 7 and give Ubuntu the much faster beginning. :D

---

### Post by Erlander on 2010-04-28
> **Tweak42 said:**
> Thanks for pointing out the nifty bench utility feature. :)

Your drive may be showing up under IDE mode if you don't have the controller set to ahci/sata in the bios.  Just beware switching modes can halt a WinXP partition from booting; linux, vista and win7 seem handle switching it ok.



Thank you for this info.

I has wondered why I was getting error messages "ATA1 device not ready. Softreset failed" on bootup.

Changing over to ahic/sata fixed that and although Ubuntu could read the Win XP partitions XP did not boot.  I see a re-install of Win XP coming up! Sigh!

---

### Post by buellman on 2010-04-28
250GB WD Caviar Blue WD2500AAKS-00B3A0 (ext4):

Read min: 41.8 MB/s
Read max: 97.1 MB/s
Read avg: 75.4 MB/s
Access avg: 16.5 ms

1TB WD Caviar Green WD10EADS-00L5B1 (ext3):

Read min: 44.3 MB/s
Read max: 92.0 MB/s
Read avg: 73.9 MB/s
Access avg: 14.1 ms

BTW: It would be cool if we could have some sort of Database like [HD Tune]("http://www.hdtune.com/testresults.html") has.

**Edit**: Both hdds are completely encrypted if that means anything.

---

### Post by buellman on 2010-04-28
> **andrewabc said:**
> Can anyone confirm if safe to do read/write benchmark? Don't want to screw any of my stuff up.

Try it :-D It will tell you the following:
> A partition table was detected - write benchmarking requires the disk to be completely empty

---

### Post by P4man on 2010-04-28
As someone else already asked: **is the read/write test destructive?** Would be nice if they made that more clear!
(edit already answered above)

Anyway, rather than bragging about how fast my raided ssds are, lets see who can post a **slower** result than this:

Min read 10.3 MB/s (!)
Max read 30.7 MB/s
Avg read 24.8 MB/s

avg access time: 17.8ms

Thats using a prehistoric 40GB notebook drive. (and interestingly, ubuntu is still rather snappy on it).

[[img]http://www.ubuntu-pics.de/thumb/54730/40_gb_hard_disk__ata_hts548040m9at00______benchmark_001_XNZJYL.png[/img]](http://www.ubuntu-pics.de/bild/54730/40_gb_hard_disk__ata_hts548040m9at00______benchmark_001_XNZJYL.png)

---

### Post by andrewabc on 2010-04-28
> **buellman said:**
> Try it :-D It will tell you the following:

Yes, I noticed that for HDD.
For my SSD it only asked if I was sure I wanted to do the read/write. No mention of it needing to be empty or a partition.
I didn't do it because I figured it would corrupt my SSD install. A better warning would be appreciated as someone is likely to run the test because not enough warning given.

---

### Post by P4man on 2010-04-28
> **andrewabc said:**
> Yes, I noticed that for HDD.
For my SSD it only asked if I was sure I wanted to do the read/write. No mention of it needing to be empty or a partition.
I didn't do it because I figured it would corrupt my SSD install. A better warning would be appreciated as someone is likely to run the test because not enough warning given.
Hmm.. an ssd doesnt have an inner and outer sector and so you wouldnt need to write (or read) across the entire drive to bench it. So quite possibly it just needs some free space on a ssd to test at random?

---

### Post by Milos_SD on 2010-04-28
Western Digital Caviar Green 1TB WD10EADS-00L5B1
Western Digital Caviar Blue 640GB WD6400AAKS-22A7B0
Western Digital Caviar Blue 320GB WD3200AAKS-00VYA0
Maxtor 160GB 6Y160P0

All drives use ext4 file system.

---

### Post by Onesimus on 2010-04-28
The graphical display of the results of the benchmark, I think are not displayed correctly.

What may be more meaningful is having collected the data (read rates and access times) is to sort them in increasing order.  That way the median (i.e at 50% of the time) would be the average.  The lower and upper quartiles (and/or deciles) could also be determined from the dataset.

The upper quartile would then represent the read rate at which 25% of the data exceeds that amount.

The minimum & maximum values are less informative because they may have occurred for an insignificant amount of time.  For example, if you have a maximum read rate of 200MB/s and it is the only reading above 100MB/s, then it isn't particularly meaningful.

The access times should be displayed in a similar way.

---

### Post by andrewabc on 2010-04-28
> **Onesimus said:**
> The graphical display of the results of the benchmark, I think are not displayed correctly.

What may be more meaningful is having collected the data (read rates and access times) is to sort them in increasing order.  That way the median (i.e at 50% of the time) would be the average.  The lower and upper quartiles (and/or deciles) could also be determined from the dataset.

The upper quartile would then represent the read rate at which 25% of the data exceeds that amount.

The minimum & maximum values are less informative because they may have occurred for an insignificant amount of time.  For example, if you have a maximum read rate of 200MB/s and it is the only reading above 100MB/s, then it isn't particularly meaningful.

The access times should be displayed in a similar way.

I didn't notice any major problems. The average would be average for the whole test, not just an average between min/max. Although a 200mb datapoint even though nothing else is above 100mb/s does throw off avg a bit. The way to solve this would be to use statistical analysis to eliminate irregular occurrences (forget proper term) from calculating the averages. But I wouldn't prevent min/max from being shown.

Min and max are good info, true the min/max # might only occur for extremely short period of time and rarely occur, but does show the min/max possible during the test.

Don't see what is wrong with avg latency. Just gives an average of all points. HDD that number is all over the place. SSD it stays pretty much in same spot the whole test.

I agree the program can be improved a lot. It definitely has been improved a lot since 9.10. Hopefully more progress can be made for 10.10

---

### Post by cariboo on 2010-04-28
I've got a Mac G3 running Debian stable PPC, It doesn't have a gui, so here are the hdparm results:

```
/dev/hda:
 Timing cached reads:   358 MB in  2.00 seconds = 178.61 MB/sec
 Timing buffered disk reads:   60 MB in  3.08 seconds =  19.49 MB/sec
```

Model=WDC WD102AA, FwRev=83.10A83

---

### Post by MacUntu on 2010-04-28
> **Onesimus said:**
> (i.e at 50% of the time)

But it isn't 50% of the time - it's 50% of the disk capacity. :idea:

---

### Post by the_one(2) on 2010-04-28
My results using a 30 GB vertex SSD
min: 122.0 MB/s
max: 249.7 MB/s
avg: 197.5 MB/s
avg access: 0.5 ms

---

### Post by Onesimus on 2010-04-29
> **andrewabc said:**
> I didn't notice any major problems. The average would be average for the whole test, not just an average between min/max. Although a 200mb datapoint even though nothing else is above 100mb/s does throw off avg a bit. The way to solve this would be to use statistical analysis to eliminate irregular occurrences (forget proper term) from calculating the averages.


What I am suggesting is a statistical analysis.  There are three ways to calculate the average.  The mean, the median, and the mode.  The average that I am suggesting should be determined is the median (i.e. the 50 percentile - it occurs for 50% of the time).  This would be a better average because it wouldn't be affected by large data points that don't occur very often.  Whereas the mean average would be affected.

> **MacUntu said:**
> But it isn't 50% of the time - it's 50% of the disk capacity. :idea:

Then if that is the case, how does it determine values for 0% of the disk capacity - does it empty the disk ?  Or for 100% does it fill it ?

Until the data is clearly presented and understood how they have been dervied, then there seems little point in posting values on the forum, because it is not entirely clear what the data values actually mean.

---

### Post by P4man on 2010-04-29
> **Onesimus said:**
> W
Then if that is the case, how does it determine values for 0% of the disk capacity - does it empty the disk ?  Or for 100% does it fill it ?
.

You dont understand. A regular harddisk has different performance characteristics  at the inside tracks as on the outside. The outside turns faster (well, the speed of the platter is higher relative to the head) -> higher performance. Nothing to do with how full it is, the graph shows performance from the outside to the inside of the hdd platter.

---

### Post by Onesimus on 2010-04-29
> **P4man said:**
> You dont understand. A regular harddisk has different performance characteristics  at the inside tracks as on the outside. The outside turns faster (well, the speed of the platter is higher relative to the head) -> higher performance. Nothing to do with how full it is, the graph shows performance from the outside to the inside of the hdd platter.

Then wouldn't it be helpful to everyone, if that was stated somewhere. I wouldn't call myself IT illiterate having been a software developer/analyst for 20 years, but I do wonder if developers have gone to the trouble of developing software (perhaps over several months) then would it be too much for them to go that extra mile and spend an hour writing a paragraph or two describing their efforts so those that aren't in the know might appreciate them even more ?

If performance really does improve towards the outer sections of the disk (i.e approaching 100%), shouldn't people be concerned if the performance decreases.  In general, most of the results posted here appear to indicate that performance of the read-rate reduces with increasing disk capacity.

---

### Post by P4man on 2010-04-29
> **Onesimus said:**
> Then wouldn't it be helpful to everyone, if that was stated somewhere. I wouldn't call myself IT illiterate having been a software developer/analyst for 20 years, but I do wonder if developers have gone to the trouble of developing software (perhaps over several months) then would it be too much for them to go that extra mile and spend an hour writing a paragraph or two describing their efforts so those that aren't in the know might appreciate them even more ?

Generally those concerned about the performance of their drives and running benchmarks I think will be aware of this. I also actually find it pretty amazing they included such a nice benchmark here in what is just a disk utility, not a sisoft sandra benchmarking suite, its not like you will find anything like it on windows or os-x by default. Some people are never satisfied :)

But anyway, its open source, so feel free to contribute!

> If performance really does improve towards the outer sections of the disk (i.e approaching 100%), shouldn't people be concerned if the performance decreases.

Im not sure I understand what you are saying. The graph represents 
0% as the outside tracks (which is the beginning) of the hdd where performance (read/write throughput at least) is highest. This is completely normal and by design. Some people partition their drives accordingly, creating "fast" partitions at the beginning of the drive.

>   In general, most of the results posted here appear to indicate that performance of the read-rate reduces with increasing disk capacity.

?
No, not capacity. It decreases near the inside of the drive, but that has no direct relationship with a full or empty drive. It depends entirely where your partitions are and how your OS decides to fill them. You can tune this if you really want, and to some extent OSs are clever and try putting commonly used files at the beginning (outside),  but its really not worth bothering with for most and avoiding fragmentation is a much bigger issue than this.

---

### Post by MacUntu on 2010-04-29
I'm sorry for throwing in the word "capacity". :(

[QUOTE=Onesimus]Then wouldn't it be helpful to everyone, if that was stated somewhere.[/QUOTE]

Definitely.

---

### Post by Onesimus on 2010-04-29
@P4man

Thank you for taking the time to explain things patiently to me.  I am impressed with the ever-growing functionality of the applications that are provided as standard with the default Ubuntu installation.

I suppose I just feel that if more explanation was provided it would be helpful to everyone.

Thanks once again

---

### Post by joker535 on 2010-04-29
Here are the results from my SSD Raid0

[IMG]http://cassetty.dyndns.org/raidbenchmark.png[/IMG]

I am running 10.04 RC with an Intel S5000XVNSATAR mainboard, Dual L5310 Quad Core Xeons over clocked to 2.0Ghz (1333 bus), Thermalright True Black 120 coolers with Scythe 120mm fans, 8G (8x1G) FBDIMMS, OCZ 550W PSU, Yate Loon case and ram fans, Nvidia Quadro FX540 PCIe, Dual Intel X25v 40G SSDs in Raid (R1 /boot, R0 swap and /), Chieftec mid tower EAXT case, Rosewill PCI wireless card.

---

### Post by joker535 on 2010-04-29
Here are the SSDs by themselves.

[IMG]http://cassetty.dyndns.org/sdabenchmark.png[/IMG]

[IMG]http://cassetty.dyndns.org/sdbbenchmark.png[/IMG]

---

### Post by joker535 on 2010-04-29
Here is the output from hdparm

[IMG]http://cassetty.dyndns.org/hdparmboth.png[/IMG]

Of course these are read only tests. Hop this is what you were looking for.

---

### Post by andrewabc on 2010-04-29
> **joker535 said:**
> Here are the SSDs by themselves.


Thanks for the awesome benchmarks.

> **joker535 said:**
> Here is the output from hdparm


Of course these are read only tests. Hop this is what you were looking for.

Well I was looking more for disk utility benchmarks. You could run that and see if it gives similar results.

---

### Post by ulukay on 2010-04-29
[img]http://666kb.com/i/bis2z7b2cibmfg8n6.png[/img]

---

### Post by andrewabc on 2010-04-29
> **ulukay said:**
> image

That's pretty good considering they only advertise Solid2 as having sustained read of up to 170mb/s

---

### Post by P4man on 2010-04-29
How come the intel SSDs show such a dip in the beginning? Not that the performance isnt awesome, just curious?

---

