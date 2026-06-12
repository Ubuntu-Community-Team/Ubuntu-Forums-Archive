---
title: "Lucid Lynx alpha 3 , how to increase boot up time ?"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubfu on 2010-03-03
Booting up fast within 30 sec is good , but will it kill my hard disk ? 
Having an old hard disk , I can hear the arm of the hard disk seeking pushing up to the max loading and reading files.

It'll sure deteriorate the hard disk life.Hoping there's an option to enable fast boot up time and slow boot up time.
This is just for those who are using hard disk which is older than 4-5 years to preserve them.

---

### Post by recluce on 2010-03-03
> **ubfu said:**
> Booting up fast within 30 sec is good , but will it kill my hard disk ? 
Having an old hard disk , I can hear the arm of the hard disk seeking pushing up to the max loading and reading files.

It'll sure deteriorate the hard disk life.Hoping there's an option to enable fast boot up time and slow boot up time.
This is just for those who are using hard disk which is older than 4-5 years to preserve them.

In all honesty, this is the first ever request for slower booting I have seen in my life. I am not sure that this is not an attempt to troll, but with the benefit of the doubt, I will take your question as forthright.

Your hard drive's mechanics are designed to handle the fastest seek times it is capable of - this should not lead to any deterioration of the mechanics or shorten the life span of your drive(s). 

Given that 5 years is the average maximum designed service life of most hard drives, you should run frequent SMART diagnostics to be sure the drives are still in good shape - or you might consider replacing those drives.

---

### Post by psyke83 on 2010-03-03
> **ubfu said:**
> Booting up fast within 30 sec is good , but will it kill my hard disk ? 
Having an old hard disk , I can hear the arm of the hard disk seeking pushing up to the max loading and reading files.

It'll sure deteriorate the hard disk life.Hoping there's an option to enable fast boot up time and slow boot up time.
This is just for those who are using hard disk which is older than 4-5 years to preserve them.

You're kidding, right? If you're not... then no, hard drives can't get damaged from reading/writing files too fast.

As long as the surrounding environment is ideal (drive temperature never exceeds manufacturer threshold, power supply is stable, and the drive always remains steady in place / never subjected to sudden motion or fall), you don't need to worry.

The only ways that software can ruin a drive is by using programs to interface/tamper with the firmware, or perhaps if the operating system does not park the drive heads before shutting down (you will hear the drive emit a loud screech or click as soon as the power turns off). This was a problem in Windows XP (pre-service packs), and in some older versions of Ubuntu. I believe that the problem no longer occurs in recent releases, however.

You can monitor your drive health with the "Disk Utility" (System -> Administration menu). The "Power-off Retract Count" and "Load/Unload Cycle Count" attributes relate to improper shutdowns.

P.S. I own hard drives more than 5 years old with no bad sectors or issues, and I've owned drives less than 2 years old that have spectacularly failed. The longevity of your drive depends more on manufacturer quality and pure luck (that is to say - you didn't receive a drive that may have gotten damaged in transit from the warehouse, for example). If you're truly interested in this subject, you may want to read [this]("http://labs.google.com/papers/disk_failures.html") Google publication.

---

### Post by robert shearer on 2010-03-03
> Given that 5 years is the average maximum designed service life of most hard drives

Trying to get my head around this one. :o

Implies that there is a maximum maximum designed service life as well as a minimum maximum designed service life. ;)

Of the 9 hard drives I run 1 is a year old, 1 is 2 years old, 3 are 5+ years old and 4 are 10+ years old.
SMART diagnostics give them a clean bill of health.

However, I am of the school of thought that boots up when there is something to **do** rather than being booted up all the time.

---

### Post by dino99 on 2010-03-03
i'm happy with Lucid boot time, except at the end: have to wait about 10 or 15 seconds to see title bar (panel) on screen's top.

---

### Post by vishalrao on 2010-03-03
ahahaha i had the same question but for another reason :) [http://ubuntuforums.org/showthread.php?t=1400206](http://ubuntuforums.org/showthread.php?t=1400206)

and no, i was not trolling either :lolflag:

---

### Post by VMC on 2010-03-03
> **psyke83 said:**
> ... If you're truly interested in this subject, you may want to read [this]("http://labs.google.com/papers/disk_failures.html") Google publication.

I read the abstract and found this line interesting:
"...Surprisingly, we found that temperature and activity levels were much less correlated with drive failures than previously reported."

---

### Post by emarkay on 2010-03-03
> **robert shearer said:**
> Trying to get my head around this one. :o
Implies that there is a maximum maximum designed service life as well as a minimum maximum designed service life. 

As one who remembers the old Davong 5Meg Hard Disk Units (!), I know that the lifespan is usually measured as "MTBF" ([I]mean time between failures).  

[/I]Electromechanical devices do fail.  Thermal cycling (cold startup) is one small factor, as is excessive vibration, but the largest failure mode I have encountered is just too much heat.  Overheating anything is not a good idea.  Other than that, while, yes, "if you never use it it will never fail", these units of today have great reliability, and can be externally linked for redundancy if need be.

[http://www.pcguide.com/ref/hdd/perf/qual/specMTBF-c.html](http://www.pcguide.com/ref/hdd/perf/qual/specMTBF-c.html)

[http://forums.cnet.com/5208-7591_102-0.html?threadID=183981](http://forums.cnet.com/5208-7591_102-0.html?threadID=183981)

[http://www.eweek.com/c/a/Data-Storage/Hard-Disk-MTBF-Flap-or-Farce/](http://www.eweek.com/c/a/Data-Storage/Hard-Disk-MTBF-Flap-or-Farce/)

[URL="http://docs.google.com/viewer?a=v&q=cache:q7nqEvSwhZIJ:labs.google.com/papers/disk_failures.pdf+%22hard+disk+lifetime+life%22&hl=en&gl=us&pid=bl&srcid=ADGEEShvzuvEYXdh1yhO0lkXfTbeRY56hp7UC0GJysAZRtxmUu_ftFJlKMx08F_72uDEXlI4tiFJme5OLduNdpGRYeMnrOzabAUUpmf5Z_idY2urJldpF9ONfykBSbHIow18LW4k7EdO&sig=AHIEtbRXtz5xOfHF12rhTwQH8gBXIehhcQ"]
[/URL]

---

### Post by recluce on 2010-03-03
> **emarkay said:**
> As one who remembers the old Davong 5Meg Hard Disk Units (!), I know that the lifespan is usually measured as "MTBF" ([I]mean time between failures).  



Carefull with MTBF. Some drives do have a MTBF that approaches a 100 years. This does NOT mean that any of these drive could really operate for a century, as MTBF does not account for things like material fatigue. Plastics get brittle over time, integrated circuits may chemically fail over long periods of time, the lubricant in the bearing turns to goo, etc.

MTBF should be seen this way: if the MTBF of a drive would be 20 years and I operate 500 of these drives, I should expect 25 drives to fail each year.

The "maximum designed service life" is a recommendation, usually extremely conservative, for how long I can be reasonably sure that material and heat fatigue will not cause an increase in the failure rate. Most drives will run a lot longer than the "maximum designed service life", but it gives you an idea at what point you should start watching that aging drive more closely.

There is something called the "bath tub curve" in all electronics, especially hard drives. This means that you have a high rate of failure in new devices, which rapdily declines to a very low, steady level over a long time. After exceeding the service life, the failure rate slowly and steadily rises again. The resulting curve looks a bit like an old fashioned bath tub.

And I still can't get over the fact that somebody wants Ubuntu to boot slower! :lolflag:

---

