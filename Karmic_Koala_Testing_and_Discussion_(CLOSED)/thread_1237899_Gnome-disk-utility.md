---
title: "Gnome-disk-utility"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cariboo on 2009-08-11
Gnome-disk-utility was installed doing updates this morning, after a reboot this afternoon, it is telling me one of my hard drives is dying. As soon as I saw the notification, I downloaded Seatools from Seagates web site and tested my hard drive using both the short and long test. The drive passed without any errors. I haven't turned SMART off yet to see if the notification goes away.

Would this be considered a bug?

---

### Post by psyke83 on 2009-08-11
> **cariboo907 said:**
> Gnome-disk-utility was installed doing updates this morning, after a reboot this afternoon, it is telling me one of my hard drives is dying. As soon as I saw the notification, I downloaded Seatools from Seagates web site and tested my hard drive using both the short and long test. The drive passed without any errors. I haven't turned SMART off yet to see if the notification goes away.

Would this be considered a bug?

Look closely at the results - your disk has bad sectors :). If the operating system is reporting bad sectors, that means that the space allocated for internal bad sector remapping has been exhausted* - which is usually an indication that things will get worse.

*It's hard to tell without seeing the detailed statistics, but if your "uncorrectable sector count" >0, then your disk may fail in the near future.

---

### Post by wayne_cat on 2009-08-11
This is the 3 "one of my disks dies" posting here in the Karmic forum today ... strange

---

### Post by psyke83 on 2009-08-11
> **wayne_cat said:**
> This is the 3 "one of my disks dies" posting here in the Karmic forum today ... strange

What's stranger is that I was never prompted to install gnome-disk-utility, even though I'm completely up-to-date and not using a regional mirror. Was this removed from the default list already?

---

### Post by autocrosser on 2009-08-11
Not too suprising when a important utility gets uploaded...I test my drives about once a month--was "caught" with a bad drive a couple of years ago & lost quite a bit--I now have 4 drives & cross-backup things that are important to me...

I would say that this is just a case of older equipment finally being tested--and about time too...I for one was very glad to see a Smart tool being included as default.

---

### Post by cariboo on 2009-08-11
I didn't do a search on the problem, or I would have added my me too, to the thread. This is the output of smartctl --all /dev/sdb

```
sudo smartctl --all /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250620A
Serial Number:    6QE10TQ9
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Aug 11 19:32:23 2009 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  74) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   090   006    Pre-fail  Always       -       89683279
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       704
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       11
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       194718535
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6904
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       716
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       924
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   062   051   045    Old_age   Always       -       38 (0 21 42 19)
194 Temperature_Celsius     0x0022   038   049   000    Old_age   Always       -       38 (0 11 0 0)
195 Hardware_ECC_Recovered  0x001a   069   051   000    Old_age   Always       -       282294
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6901         -
# 2  Short offline       Completed without error       00%      6901         -

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
```

This drive is a year and a half old, and has been tested before, but with hard drives you never know when they are going to fail.

---

### Post by autocrosser on 2009-08-11
> **psyke83 said:**
> What's stranger is that I was never prompted to install gnome-disk-utility, even though I'm completely up-to-date and not using a regional mirror. Was this removed from the default list already?

That is a bit weird..I updated early this morning & it was included without much fuss...I was watching the updates & looked at it before going to work....

---

### Post by autocrosser on 2009-08-11
You might install gsmartcontrol & compare the output of a full scan between the two---a metrics difference with these programs can cause real panic---


> **cariboo907 said:**
> I didn't do a search on the problem, or I would have added my me too, to the thread. This is the output of smartctl --all /dev/sdb

<SNIP>

This drive is a year and a half old, and has been tested before, but with hard drives you never know when they are going to fail.

I will note that I've had problems with Seagate drives--sent one back last year that had less than 200hours on it due to a failure.

---

### Post by psyke83 on 2009-08-11
> **cariboo907 said:**
> I didn't do a search on the problem, or I would have added my me too, to the thread. This is the output of smartctl --all /dev/sdb

Perhaps your drive uses a strange encoding, but two of the entries look quite suspicious:

```
  1 Raw_Read_Error_Rate     0x000f   115   090   006    Pre-fail  Always       -       89683279
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       194718535

```

However, you have no uncorrectable sectors and only 11 remapped sectors (not too bad for an elderly disk, I suppose).

---

### Post by gaspard.leon on 2009-08-11
Wikipedia ([http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).)

Has a note on the RAW value of "Read Error Rate":
"Seagate drives often report a raw value that is very high even on new drives, and does not thereby indicate a failure." 

I have just looked at my Seagate 7200.7 (from 2003 and still going... can you believe it) and it reports:
```
ID	Attribute Description			Threshold	Value	Worst	"Raw" Data		Status
1	Raw Read Error Rate			6		63	53	34242123	OK: Value is normal
3	Spinup Time				0		96	96	0		OK: Always passes
4	Start/Stop Count			20		100	100	13		OK: Value is normal
5	Reallocated Sector Count		36		100	100	0		OK: Value is normal
7	Seek Error Rate				30		89	60	906912147	OK: Value is normal
9	Power-On Time Count			0		69	69	27767		OK: Always passes
0A	Spinup Retry Count			97		100	100	0		OK: Value is normal
0C	Power Cycle Count			20		100	100	564		OK: Value is normal
C2	Temperature				0		43	51	43		OK: Always passes
C3	Hardware ECC Recovered			0		63	53	34242123	OK: Always passes
C5	Current Pending Sector Count		0		100	100	0		OK: Always passes
C6	Offline Uncorrectable Sector Count	0		100	100	0		OK: Always passes
C7	Ultra ATA CRC Error Rate		0		200	200	0		OK: Always passes
C8	Write Error Rate			0		100	253	0		OK: Always passes
CA	Data Address Mark Errors		0		100	253	0		OK: Always passes

```

So it appears cariboo907's drive could be in normal condition...

Remember for most S.M.A.R.T. "Values", higher is better...
100 is often used for "Normal"...
the "Raw" values are often just proprietary numbers.

In any case the original issue where it mentions bad sectors is the part that interests me how does it determine this?
EDIT: perhaps it just looks at the raw data of "Reallocated_Sector_Ct"

---

### Post by cariboo on 2009-08-12
I just ran the long test using gsmartcontrol, the only differences between the results from smartctl and gsmartcontrol were the tempurature and the power-on times. The hard drive passed both test without any errors. 

I also ran Seatools using both the short and long tests and the drive passed without errors.

To me this looks like a bug.

I would also like to know how palimpsest comes up with bad sector errors.

---

### Post by autocrosser on 2009-08-12
I would agree--I've ran a couple of tests on my equipment & Gnome-disk-utility looks like it's metrics are off a bit--no need to scare people into new hardware without real need---If you do a report--post it & I'll confirm it.....

---

### Post by psyke83 on 2009-08-12
> **cariboo907 said:**
> I just ran the long test using gsmartcontrol, the only differences between the results from smartctl and gsmartcontrol were the tempurature and the power-on times. The hard drive passed both test without any errors. 

I also ran Seatools using both the short and long tests and the drive passed without errors.

To me this looks like a bug.

I would also like to know how palimpsest comes up with bad sector errors.

Technically your drive does have bad sectors - 11 according to your output (Reallocated_Sector_Ct). Reallocated sectors are remapped via your drive's SMART firmware function, and the operating system doesn't know that they exist (excluding applications which poll SMART functions, of course).

When the extra sectors allocated to remap bad sectors is exhausted and more bad sectors are encountered, they are listed as "uncorrectable" in the SMART output, which is then visible to the operating system as bad sectors in fsck (or chkdsk in Windows).

You definitely have bad sectors, but the "good" kind.

---

### Post by psyke83 on 2009-08-12
> **autocrosser said:**
> I would agree--I've ran a couple of tests on my equipment & Gnome-disk-utility looks like it's metrics are off a bit--no need to scare people into new hardware without real need---If you do a report--post it & I'll confirm it.....

If you also get warnings, what's your Reallocated Sector Count and Offline Uncorrectable Sector Count?

---

### Post by autocrosser on 2009-08-12
No warnings from GDU--I just question the metrics being used--or at least the language being used........

---

### Post by psyke83 on 2009-08-12
> **autocrosser said:**
> No warnings from GDU--I just question the metrics being used--or at least the language being used........

If the warning is due to the Reallocated Sector Count, I agree that it's a little excessive to show a notification. But the amber indicator with the bad sector warning should remain, as reallocated sectors can be a sign of trouble on the horizon.

Either way, it'll help to find out what SMART value is causing these notifications to display incorrectly; perhaps the unusual RAW values used by Seagate drives is to blame, as mentioned by gaspard.leon?

---

### Post by cariboo on 2009-08-12
There was already a bug started #[lpbug]412152[/lpbug] I added the results of the short and long tests.

---

### Post by autocrosser on 2009-08-12
Thanks for the "heads-up"  I subscribed to the bug--want to follow it.....

---

### Post by cariboo on 2009-08-12
@psyke83

I agree I do have bad sectors, I think the bad sector threshold is set to low, as one of the bug reporters only had 1 bad sector and and palimpsest popped up.

I'm going to try a low level format, to see if I can get rid of the error message.

---

### Post by psyke83 on 2009-08-12
> **cariboo907 said:**
> @psyke83

I agree I do have bad sectors, I think the bad sector threshold is set to low, as one of the bug reporters only had 1 bad sector and and palimpsest popped up.

I'm going to try a low level format, to see if I can get rid of the error message.

Low level formats aren't really advisable on modern hard disks.

See: [http://en.wikipedia.org/wiki/Disk_formatting#Transition_away_from_LLF](http://en.wikipedia.org/wiki/Disk_formatting#Transition_away_from_LLF)

The only way you can "improve" a drive's SMART health status is to force an uncorrectable sector to become a reallocated sector, but it's complex to do when the sector is on an active filesystem. 

See: [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

---

### Post by Martey on 2009-08-12
> **cariboo907 said:**
> I agree I do have bad sectors, I think the bad sector threshold is set to low, as one of the bug reporters only had 1 bad sector and and palimpsest popped up.

I do not know about anyone else, but I would rather be informed as soon as my drive started accruing bad sectors, so that I could make sure that all of my data was backed up.

---

### Post by Paqman on 2009-08-12
I'm getting this on my Seagate drive too. I've also run the Seagate utility through the long test, and fsck'd my partitions. Definitely a bug, as every indication is that the drive is handling the bad sectors properly.

---

### Post by cariboo on 2009-08-12
According to Seagate, a low level format using their tools, is a way to lock out the bad sectors. In researching this problem, I found out more than I really wanted to know about Seagate hard drives, so I guess for now I'll stick with WD for my hard drives.

@Martey 

I do daily backups,sometimes hourly. I know what it's like to lose important data.

---

### Post by Aries K on 2009-08-12
I'm getting this as well on one of my Hitachi Deskstars.

---

### Post by GeorgeVita on 2009-08-12
Hi, I think it is not manufacturer depended as my Hard Disk ("failing") is:

HD **Toshiba** 60GB MK6037GSX on EeePC 1000H

For now I will just ignore it and test again after clean install of Alpha4.

Regards,
George

P.S. After clean install of the later daily-build, the notice remains.

---

### Post by cariboo on 2009-08-12
I just ran a low level format, basically just writing all zero's to the hard drive, that didn't solve the problem. I saw an email from the bug list this morning, the dev that wrote the app stated that if there is 1 bad sector on the drive, it should be reported, which I agree with, but the notification shouldn't be in your face on every reboot. If this error is still around  on final release, there are going to be lots of hard drives replaced needlessly.

---

### Post by psyke83 on 2009-08-12
> **cariboo907 said:**
> I just ran a low level format, basically just writing all zero's to the hard drive, that didn't solve the problem. I saw an email from the bug list this morning, the dev that wrote the app stated that if there is 1 bad sector on the drive, it should be reported, which I agree with, but the notification shouldn't be in your face on every reboot. If this error is still around  on final release, there are going to be lots of hard drives replaced needlessly.

Just FYI, zero-writing a drive isn't a low-level format. Nowadays a true low-level format can only be done in a factory (or if you can re-flash the firmware and wipe the SMART data). Even so, a LLF still can't repair bad sectors, but you can sometimes force previously "uncorrectable" sectors to become reallocated sectors, and thus allow SMART tests not to fail.

I managed a little bit of "surgery" on my desktop's drive last year - one uncorrectable sector was causing SMART tests to fail, but I forced it to become a reallocated sector using the excellent howto [I mentioned earlier]("http://smartmontools.sourceforge.net/badblockhowto.html#bb").

The presence of reallocated sectors on your drive shouldn't warrant constant notifications, I agree.

---

### Post by cariboo on 2009-08-12
I know that there really isn't a low level format any more, it is just that some of the diagnostc apps I use call it that. I remember low level formatting MFM/RLL drives back in the 80's

I'll just keep on monitoring the drive, if the bad block count starts to climb, I'll replace it.

Does any one know of a way to run s SMART test on a drive in external USB enclosure?

---

### Post by twisted_steel on 2009-08-12
Slightly off topic, but I learned something today thanks to the title bar of that screenshot.

[http://en.wikipedia.org/wiki/Palimpsest](http://en.wikipedia.org/wiki/Palimpsest)

---

### Post by psyke83 on 2009-08-12
> **cariboo907 said:**
> I know that there really isn't a low level format any more, it is just that some of the diagnostc apps I use call it that. I remember low level formatting MFM/RLL drives back in the 80's

I'll just keep on monitoring the drive, if the bad block count starts to climb, I'll replace it.

Does any one know of a way to run s SMART test on a drive in external USB enclosure?

It depends on the enclosure type. There is experimental support to passthrough SMART commands on certain USB -> PATA/SATA bridges.

See the man page for smartctl where it describes the options for "-d TYPE, --device=TYPE".

---

### Post by uBeer on 2009-08-12
> **twisted_steel said:**
> Slightly off topic, but I learned something today thanks to the title bar of that screenshot.

[http://en.wikipedia.org/wiki/Palimpsest](http://en.wikipedia.org/wiki/Palimpsest)

Awesome, smart name for a smart utility.

---

### Post by psyke83 on 2009-08-12
Hmm, smartmontools in our repository is outdated, and it seems that the USB bridge passthrough isn't supported with our version.

Here's the newer man page with the relevant options: [http://smartmontools.sourceforge.net/man/smartctl.8.html](http://smartmontools.sourceforge.net/man/smartctl.8.html)

---

### Post by psyke83 on 2009-08-12
> **cariboo907 said:**
> I know that there really isn't a low level format any more, it is just that some of the diagnostc apps I use call it that. I remember low level formatting MFM/RLL drives back in the 80's

I'll just keep on monitoring the drive, if the bad block count starts to climb, I'll replace it.

Does any one know of a way to run s SMART test on a drive in external USB enclosure?

Ok, I built a 32bit smartmontools package from SVN, and it works on my USB enclosure. If you want to test the package, let me know and I'll PM you the link (I don't think it's appropriate to post on the forum, as it's untested and packaged without the debian patches applied).

---

### Post by plun on 2009-09-20
Fixed....:KS

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/009078.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/009078.html)

"Passed with a few bad sectors"

[[img]http://ubuntu-pics.de/thumb/25174/snapshot19_5NzXCV.png[/img]](http://ubuntu-pics.de/bild/25174/snapshot19_5NzXCV.png)

---

### Post by GeorgeVita on 2009-09-20
> **plun said:**
> Fixed....:KS

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/009078.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/009078.html)

"Passed with a few bad sectors"


Hi **plun**,
this 'update' helped you to **fix** bad sectors OR  just you can 'bypass' the warning message?

Regards,
George

**EDIT:** my disk is also running at 49 Celcius!

---

### Post by plun on 2009-09-20
> **GeorgeVita said:**
> Hi **plun**,
this 'update' helped you to **fix** bad sectors OR  just you can 'bypass' the warning message?


No it doesn't fix any errors as I can see but it classify my disk as OK with minor remarks.
[B]
Menu System > Administration > Disk-Utility[/B]

I am going to check it some more....

---

### Post by MJWitter on 2009-09-20
Plun, not sure if it is very hot in Sweden right now, but you may want to try get some more airflow over that drive, it looks a bit warm(not burning, but warm).

---

### Post by timjohn7 on 2009-10-16
I also have "many bad sectors" on my various elderly hard drives and do regular and frequent backups in case of failures.
I also dont need to be reminded of impending failure every time I reboot... so I switched gnome-disk-utility off in Startup Applications.  I'll run it when I want to.

---

### Post by sideshow on 2009-10-17
> **Aries K said:**
> I'm getting this as well on one of my Hitachi Deskstars.

Me too, in Hitachi and Seagate. I never had a problem in a WD disc.


In 6years:

2x Seagate broken,

1x Hitachi broken.

WD forever.. ](*,)

---

