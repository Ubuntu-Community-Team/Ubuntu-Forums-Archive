---
title: "Installing into a SSD"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by kgangulw on 2008-10-06
Hi,

I'm trying to install Ubuntu onto my laptop. I don't want to install it on my HDD since I'm not sure what effects it'll have Vista. So I'm going to install it on a SSD drive i have. 

The question is, will it have a effect on vista if I install on the SSD? OR Is it safer to remove the hard drive completely and go with the installation?

Thanks

---

### Post by Patb on 2008-10-06
Herman's [Dual Boot site]("http://users.bigpond.net.au/hermanzone/") will help you.  He's an Aussie so you can't go wrong!

Cheers, Pat.

---

### Post by gcclinux on 2008-10-08
same topic different question.

I have a Dell Inspiron 1525 N-Series
Intel® Core™ 2 Duo Processor T8100 (2.10 GHz, 800 MHz FSB
WEBCAM	2.0 Mega pixel web camera
15.4" Wide Screen WXGA+ (1440 x 900) Display with TrueLife™
2048MB 667MHz Dual Channel DDR2 SDRAM [2x1024]
120GB (5400rpm) SATA Hard Drive
Integrated Intel® Graphic Media Accelerator X3100
8x DVD+/-RW Optical drive - N-Series
Intel® Pro Wireless 3945 802.11a/b/g
**Ubuntu 8.04**

Everything works perfectly except I want more speed, so I am thinking of buying a 	
OCZ Core Series V2 Solid State Drive - 120GB - SSD to fit in the laptop, question is, will Ubuntu install without any problems or do i need special drivers, special way of installing, etc, etc

This is the only time I don't just try it out for myself because one of those 120G SSD cost allot of money and i want to be sure it will work before I spend all this money buying a SSD.


Please advise & Many Thanks

---

### Post by Herman on 2008-10-08
I don't have one (yet), but I wish I did! :)

I think you should be able to just install Ubuntu in your SSD the same way as if your were installing in a hard disk, but that's just my personal opinion. 
You should ask at [OCZ Forums]("http://www.ocztechnologyforum.com/forum/forumdisplay.php?f=88") and see what the experts have to say. 
At a quick glance I can already see some posts there from other Ubuntu users.

Regards, Herman :)

---

### Post by Patb on 2008-10-09
Gcc, for what it's worth, I have successfully installed Ubuntu 8.0.4 on an 8Gb SSD in an Acer Asire One and so far everything works (after some tinkering).  However, there are some basic differences in the way you set up the SSD vs a conventional HD, mostly to do with avoiding unnecessary writes to disk.  

Some useful [recommendations for Ubuntu on the Aspire One are here]("https://help.ubuntu.com/community/AspireOne") and I imagine some of these suggestions would equally apply to your intended OCZ SSD drive, particularly the section "Reducing SSD Wear".  

One other hopefully useful hint: for my SSD, write speed is not particularly fast and brands differ significantly.  You might do more homework than I did (;)) on your intended brand of SSD beforehand.  

Hope this helps. Cheers, Pat.

---

### Post by Herman on 2008-10-09
I'm fairly sure things will vary between brands of SSD.

 Tony, one of the OCZ Forums moderators, said in this thread, [ssd core best filesystem/settings under linux]("http://www.ocztechnologyforum.com/forum/showthread.php?t=41662&highlight=linux"),
> I just let Ubuntu do its thing for me, DIY laptop 64GB core and Ubuntu 32bitThere's no harm in being cautious though. I'm still looking around in the [OCZ Forums]("http://www.ocztechnologyforum.com/forum/forumdisplay.php?f=45"), I expect to have time to look properly over the weekend.

:) At this stage I must say that Ubuntu seems to be very well represented there.

I found that the Reiser File System is much faster than Ext2 or Ext3 in the flash memory I ran a few tests in with benchmarking software, and it's a difference you can really feel too!
That does vary between brands of flash memory, in some brands the difference is negligible, but I haven't found one in which ReiserFS is slower yet.

Regards, Herman :)

---

### Post by dabl on 2008-10-09
> **Patb said:**
> 

  However, there are some basic differences in the way you set up the SSD vs a conventional HD, mostly to do with avoiding unnecessary writes to disk.  



That's correct, as I learned when setting up Linux on my Asus Eee PC, which has only a 4GB SSD.  While a conventional hard drive has an "infinite" ability to re-write bits on the media ("infinite" for practical purposes, not literally), SSDs have a very finite limitation on erase/re-write cycles.  Therefore, you either need to install a non-journalling filesystem (ext2), or else use the available options for ext3 to cut the writing frequency way down.

Here's a thread with useful details, along with some speculation and controversy on the topic:

[http://forum.eeeuser.com/viewtopic.php?id=890](http://forum.eeeuser.com/viewtopic.php?id=890)

:)

---

### Post by Herman on 2008-10-12
**Dabl and Patb are both right to be advising special steps to be taken when installing in small flash memories where the endurance of the flash memory is not known. (Not advertised).**

I would imagine that the endurance of the EeePC's 4001MB SILICONMOTION SM would be a lot more than the 10000 writes per cell, (the figure that rozojc quoted in Dabl's eeeuser.com web forums link.
Most flash memory these days has an endurance of between 100000 and 1000000 write-erase-cycles per cell, and of course with 'wear leveling', we're not able to keep on writing the the same cells repeatedly even if we wanted to.
(Presuming the  4001MB SILICONMOTION SM uses wear leveling. I think it would need to).

[B]I have been taking a closer look into flash memory wear and I found the following interesting web site, [Accurately judging endurance for solid-state storage]("http://www.edn.com/article/CA6298274.html") - EDN, 1/19/2006 - Gary Drossel
I took the equation found in that web page and made a spreadsheet for it, and it's great fun to play with the numbers in it.[/B]

There were a number of areas of concern cited in the eeeusers.com forum about using a standard Linux installation in the flash memory, and in other websites I researched.

One worry was the **file system journal.**
I tried to find out how much data is written and how often and I've come up with a value of 1 kb of data 60 times per minute, (although I have read in another website that the file system journal is updated only every five seconds).

Even only a 1 kb write would force the flash memory to re-write an entire cell though, and the size of these cells can vary between brands and types of flash. I picked 128 mb for the size of each cell for use in Gary Drossel equation.

For system logging in **/var/log/messages**, I took a look in mine and my system has been up for 8 hours, with 35 messages, forcing a minimum write of 128 mb each time. Let's just say 100 disk writes per 24 hours for a round number okay?

For firefox, I emptied my** firefox cache** and visited 12 random websites, (includung a youtube video), and found 48 files, all but three were under 128 mb. I'm counting 52 disk writes for that.
Okay, let's say we're going to visit 100 websites per day. 55/12 x 100 = 458 disk writes per day.

I read that **Email messages** average about 11kb in length. Each one means a 128 kb erase block anyway, so the size doesn't matter. 12 emails per day = 12 disk writes.

I have no idea how many disc writes '**atime**' would be responsible for, but I did find a site which said that in Hardy Heron and later, we use 'relatime', so it might not be important to edit /etc/fstab with 'noatime'.
I don't know much about **blkid.tab** and **mtab** either, but they are also supposed to be responsible for some disc writes.

To convert the all except the file system journaling values from writes per day to writes per minute, they each need to be and divided by 24 and then by 60.

I really don't know how much the swap area would be worth. That would very a great deal depending on the other hardware and what programs are used and so on. I just picked a random number for that, (well, I took a guess, if anyone has an idea about how to do better could they please let me know). I used .8 kb per minute.
EDIT: The iostat command should be able to give an idea of how much an operating system writes to the swap area.
Something like, 'iostat -k -d /dev/sda5 5 100 >> swap-report' should work,
```
iostat -k -d /dev/sda5 5 100 >> swap-report
```

I picked a value of .48 kb per minute for the user's normal work, like  saving files, updates and so on.

WIth those added up, I divided by 8 to convert from kb to mb.
The end result is, I figure that with a normal installation, we'd be writing an average of around 1.13 mb per minute to the flash.

Okay, I do realize a few of my figures pretty wild, but I'm doing my best.

**Now, running that through the equation I linked you to earlier, for a 4 GB flash memory, with an endurance of 100000 and 80% full of static data, average 1.13 mb file size, 60 time per minute comes to a predicted life of 2.3 years.**

**If we use all the tricks to reduce disk writes, /var/log/messages by eliminating  swap,   web browser caching, file system journalling, and so on, I make it down from 1.13 mb/min to just 0.06 mb file size, average.** **T****he spreadsheet indicates now a predicted lifetime of 43.29 years. **:)

Now, going back to our worst case scenario, with the 1.13 mb average per minute, for a predicted 2.3 year lifetime for a 4 GB drive, let's see what happens when we change the drive size parameter.
**Entering 120 GB instead of just 4 GB increases the life of the flash to 68.96 years.**

**Now, take into consideration that an OCZ flash memory would have an endurance of at least 1000000 rewrites per cell, and we can expect to do our worst to the ****120GB** **OCZ Core Series V2 Solid State Drive for an  ****expected lifetime of around 7 centuries.**
I don't care if my mathematics *is* a bit *rough*. You at least get the idea that it will be a long time right? 
Actually, OCZ doesn't advertise the endurance as a number of rewrites per call, they just say,> Designed for ultimate reliability, Core V2 SSDs have an excellent 1.5 million hour mean time before failure (MTBF)  **That actually only comes to about 171 years of continuous use. **

So you see,there's a big difference between a 4 GB EeePC flash memory and a 120GB OCZ Core Series V2 Solid State Drive. My main point is that you need to look at the particular flash memory in question and not just think that all flash memory is the same.
Making special changes to Ubuntu may be appropriate for some kinds of flash memory, but it might not be necessary for others.

...and once again, sorry for the wild figures, if anyone can ways to get figures that would be more accurate or can run the equation themselves and see how their results compare with mine it should be interesting. I'm not much of a mathematician, (please accept my apologies for that).

Regards, Herman  :)

---

### Post by Patb on 2008-10-17
Thanks for the resourceful and thoughtful coverage Herman. 

I think a generic how-to on "Ubuntu on SSDs" would be quite timely. I agree with your point about looking at the particular brand and type of SSD and that should certainly be part of the advice. I guess a lot of web articles are overly pessimistic about the life expectancy of SSDs. However, "netbooks" with small (4-8 Gb) SSDs are apparently very popular these days and some of the strategies for reducing disk writes probably make good practical sense for these machines. 

Cheers, Pat.

---

### Post by Patb on 2008-10-19
Inspired by Herman, I have collected a bit more specific information on disk writes for the Acer Aspire One with an 8 GB Intel® Z-P230 PATA Solid-State Drive. 

**Some background: **
I have set up my AA1 so as to minimise disk writes as suggested at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne). This hasn't been difficult. I have simply:
[LIST]
[*]dedicated the whole SSD for the root partition
[*]used ext2 (non journalised) format, rather than ext3
[*]not allocated any swap space, not anywhere (no problem as I have 1.5 Gb RAM and I don't use hibernation)
[*]put my home partition on a separate drive (the left side SD card to be precise)
[*]moved my logs to a temporary filesystem in RAM (which is therefore lost at every shutdown)
[*]put my Firefox cache in RAM
[/LIST]
**Data collection:**
With this setup, I collected disk write data using iostat over a 5 minute period - 30 intervals of 10 seconds each:
```
iostat -kdx /dev/sda 10 30 >> statdata
```During that 5 minutes, I opened a new OpenOffice document and saved a file of about 25K in size. I opened Firefox and browsed about 10 new sites including of course a search on Ubuntu Forums.  I also checked my Thunderbird IMAP email account. I then replicated this exercise to see if there were any wild differences. 

It would be nice of course to compare the results of my modified installation against a "stock standard" installation of Ubuntu 8.0.4.1 with journalised ext3 formatting and home and swap partitions on /dev/sda. Unfortunately, I am not in position to do that myself. But what I did do was to collect the data for my system as set up above and then repeat the exercise with the system logs and Firefox cache located on my root partition. 

**Assumptions:**
I seem to have used a different approach from Herman's in calculating the number and size of disk writes.  I have looked at the output of iostat in terms of the number of write requests which were issued to the drive per second (w/s) and the average number of kilobytes written to the disk per second (wkB/s). I assume that the minimum write block size is 128 Kb (although it may well be 64 Kb or even less - I just don't know) even when the number of Kb needing to be written is much smaller.  I have included a two-fold margin of error to cover for the likelihood that there will be (infrequent) occasions when files significantly larger than 128 Kb are written. I have assumed that whatever system of wear levelling exists, works perfectly. 

**Results:**
Two runs on my existing setup, and two more with the temporary log files on the SSD gave iostat results as follows:
```
                                        Run 1    Run 2
Tmpfs in RAM   Avg writes per sec       0.014    0.021
               Avg Kb written per sec   0.083    0.097
Tmpfs on disk  Avg writes per sec       0.648    0.728
               Avg Kb written per sec   9.49    17.79

```When I put all this data into Drossel's equation, I got an estimated life expectancy of 765 years for my SSD. When I repeated this with the log files on the SSD instead of in RAM, the estimated life expectancy was 22 years. Use a journalised file system, put home and swap partitions on the SSD, increase the proportion of static data on the SSD, and who knows, it might ultimately matter? 

I have tried to attach the Gnumeric spreadsheet file I used to calculate this. It is annotated to explain how I came up with each of the parameters. 

I hope this is useful or at least interesting. It will no doubt reveal how little I know about either maths or computer science, so please bear with me if I have made errors. 

Cheers, Pat.

---

### Post by Herman on 2008-10-25
:) I think we're making some progress here. I like your idea to run the same experiment and I also like your spreadsheet. 

I tried the same (or similar) experiment several times and came up with an average w/s of 6.43 for the default installation to open an OOo document and save it, save a 25 k OOo doc, open 10 websites, search ubuntu web forums and open evolution email.

That is quite a lot more than your 0.02 writes per second, so the specail modifications to reduce disk writes for flash memory drives certainly do seem to be effective.

As you can see below, there is quite a variation in my results, probably depending on whether I received emial and what websites I happened to open.
```
herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.19     4.45    1.79    [COLOR=Sienna]**1.17**[/COLOR]    29.42    22.48    35.04     0.17   57.42   5.41   1.60

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               1.16    13.40   12.78    [COLOR=Red]**9.41**[/COLOR]   144.68    91.33    21.27     1.08   48.85   5.02  11.15

herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.13     4.61    1.92    1.29    30.32    23.60    33.65     0.18   56.46   5.40   1.73

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.54    21.55    3.78    [COLOR=Red]**5.11**[/COLOR]    40.31   106.88    33.11     0.09   10.34   4.10   3.65

herman@herron:~$ uptime
 14:45:07 up  9:26,  2 users,  load average: 1.21, 0.87, 0.50
herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.08     4.75    1.92    1.33    30.11    24.32    33.53     0.18   54.91   5.36   1.74

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.90     5.11    4.65    [COLOR=Red]**2.99**[/COLOR]    63.83    32.68    25.25     0.12   16.16   4.73   3.61

herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.05     4.75    1.94    1.34    30.36    24.38    33.34     0.18   54.06   5.34   1.75

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda             322.10   471.34  115.94   **[COLOR=Red]13.87[/COLOR] ** 1925.82  1944.37    59.62    15.99  123.04   4.36  56.64

herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.01    10.04    3.80    1.56    60.93    46.49    40.09     0.59  110.28   5.09   2.73

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda              10.20     5.87   15.99    [COLOR=Red]**3.90**[/COLOR]   375.40    39.19    41.69     0.65   32.61   5.77  11.47

herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               7.98     9.98    3.88    1.59    63.30    46.33    40.07     0.59  107.48   5.10   2.79

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.70    10.53    2.28    [COLOR=Red]**5.28**[/COLOR]    52.24    63.37    30.60     0.06    7.52   2.99   2.26

herman@herron:~$ uptime
 16:58:55 up 11:40,  2 users,  load average: 0.85, 0.57, 0.53
herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.75     8.61    3.34    1.50    53.99    40.53    39.06     0.51  104.46   5.06   2.45

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.95     6.46    3.08    [COLOR=Red]**4.54**[/COLOR]    31.68    44.07    19.88     0.06    7.74   3.70   2.82

herman@herron:~$ uptime
 17:10:41 up 11:51,  2 users,  load average: 0.26, 0.46, 0.51

herman@herron:~$ iostat -kdx /dev/sda 300 2
Linux 2.6.24-21-generic (herron)     25/10/08

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.69     8.58    3.32    1.54    53.55    40.52    38.75     0.50  102.88   5.03   2.44

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.61    10.05    1.24   [COLOR=Red] **6.34**[/COLOR]    15.25    65.64    21.33     0.04    5.11   2.40   1.82


herman@herron:~$ uptime
 17:19:55 up 12:01,  2 users,  load average: 0.25, 0.36, 0.43

```Replacing your figure of 0.02 write requests per second with 6.43 in your gnumeric spreadsheet gives me an expected lifetime of only 2.38 years if I was running the standard installation in an 8 GB SSD or USB flash memory stick.

Actual usage in real life will vary greatly between different users, of course. Not very many people will be saving Open Ofiice documents and browsing the internet at that kind of a rate. 
On the other hand, there might be some people who do a lot of file sharing, so maybe some people will do even more writing to disk than this.
I know that some days, my computer spends a lot of time relatively idel while I'm away, or when I'm reading information on a web page.
Other times, I'm updating software or downloading an installation CD, and my disk writes could be extremely high.
It would be interesting to run a test for a much longer period of time and preferably when a user doesn't know there will be any measurements being made, so they'll be using the computer naturally.

The other thing is, we're only using a block level endurance specification of 10000, which I think is extremely conservative to say the least. Even 100000 would be conservative. I think most modern flash memories boast of endurance ratings of around a million erase cycles, and scientists are working on flash memory with tens of millions of erase cycles.
If we changed the block level endurance to 100000, that would basically add another zero to the expected life of the flash memory, so it would then be 23.78 years for the default install, under quite heavy use.
Maybe I'm wrong or maybe the realistic figure for most people will be somewhere in between.

What I think we will be able to do is help people to do their own measurements with iostat and they can use your spreadsheet with drossel's equation for estimating their own flash memory life with appropriate figures that apply to the individual. That way people can be as conservative or as carefree as they like.

---

### Post by Herman on 2008-10-25
```
herman@herron:~$ pidstat -d 300 1
Linux 2.6.24-21-generic (herron)     25/10/08

09:39:41          PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
09:44:41         2406      0.01      4.87      0.00  kjournald
09:44:41         5016      0.03      0.00      0.00  dbus-daemon
09:44:41         5139      0.00      0.01      0.00  cupsd
09:44:41         5615      0.01      0.09      0.00  gdm
09:44:41         5848      0.12      1.61      0.08  gconfd-2
09:44:41         6011      0.87      0.00      0.00  metacity
09:44:41         6013      3.71      0.00      0.00  gnome-panel
09:44:41         6014      0.01      0.01      0.00  nautilus
09:44:41         6056      0.05      0.00      0.00  tracker-applet
09:44:41         6058      0.07      0.00      0.00  trackerd
09:44:41         7839      0.43      0.05      0.00  soffice.bin
09:44:41         7857     37.05     19.10      0.61  firefox
09:44:41         7877     18.64      0.03      0.00  gtk-gnash
09:44:41         7878      1.17      0.03      0.00  gtk-gnash
09:44:41         7883      0.00      0.03      0.00  gtk-gnash
09:44:41         7888      0.11      0.01      0.00  gtk-gnash
09:44:41         7889      0.00      0.01      0.00  gtk-gnash
09:44:41         7896      0.27      0.01      0.00  gtk-gnash
09:44:41         7907     17.20      0.61      0.55  evolution
09:44:41         7912      2.72      0.04      0.00  evolution-data-
09:44:41         7936      0.84      0.00      0.00  evolution-excha

Average:          PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
Average:         2406      0.01      4.87      0.00  kjournald
Average:         5016      0.03      0.00      0.00  dbus-daemon
Average:         5139      0.00      0.01      0.00  cupsd
Average:         5615      0.01      0.09      0.00  gdm
Average:         5848      0.12      1.61      0.08  gconfd-2
Average:         6011      0.87      0.00      0.00  metacity
Average:         6013      3.71      0.00      0.00  gnome-panel
Average:         6014      0.01      0.01      0.00  nautilus
Average:         6056      0.05      0.00      0.00  tracker-applet
Average:         6058      0.07      0.00      0.00  trackerd
Average:         7839      0.43      0.05      0.00  soffice.bin
Average:         7857     37.05     19.10      0.61  firefox
Average:         7877     18.64      0.03      0.00  gtk-gnash
Average:         7878      1.17      0.03      0.00  gtk-gnash
Average:         7883      0.00      0.03      0.00  gtk-gnash
Average:         7888      0.11      0.01      0.00  gtk-gnash
Average:         7889      0.00      0.01      0.00  gtk-gnash
Average:         7896      0.27      0.01      0.00  gtk-gnash
Average:         7907     17.20      0.61      0.55  evolution
Average:         7912      2.72      0.04      0.00  evolution-data-
Average:         7936      0.84      0.00      0.00  evolution-excha
```pidstat is another interesting command, the above result is from running pidstat for five minutes while doing the exercises Patb suggested earlier.
This runs pidstat over a five minute (300 second) period one time only.

Another way to run pidstat is to not specify a number of seconds capture period but no number for the number of repetitions. 
```
pidstat -d 2
```That makes pidstat keep showing a snapshot every two seconds of what program(s) is/are writing to the disk. It continues until the user presses 'Ctrl+Z'.
In my standard default install, even when the system is idle kjournald appears very frequently, ( two or three times a minute, more or less), and syslog also appears quite often too.
It's interesting to watch.

---

### Post by Patb on 2008-10-25
Thanks for posting the data, Herman.  
> It would be interesting to run a test for a much longer period of time and preferably when a user doesn't know there will be any measurements being made, so they'll be using the computer naturally.
The same thought has been running through my mind. One little thing I have done is to execute the following script before each shutdown:
```
date >> /home/pat/iostat.log
uptime >> /home/pat/iostat.log
iostat -p sda >> /home/pat/iostat.log
iostat -kdx /dev/sda >> /home/pat/iostat.log
```
The first line of the iostat output is the average since boot time. So I should be able to look at the log file and add up the totals to get a picture over days. It would be possible to log pidstat data there too. I am a very haphazard user though and probably fairly minimalist - you make the important point that others might work in quite different ways. This approach should be fairly useful for anyone in doubt about their system. 
> That is quite a lot more than your 0.02 writes per second, so the special modifications to reduce disk writes for flash memory drives certainly do seem to be effective.
Yes, your pidstat data show most writes are from the journal, Firefox and Evolution. My setup avoids all these.  

As for the spreadsheet, a parameter I am quite unsure of is the I/O block size for writing files. There is an interesting discussion of endurance and block size starting here: [http://www.bitmicro.com/press_resources_flash_ssd_db.php](http://www.bitmicro.com/press_resources_flash_ssd_db.php) It is a bit dated, March 2005, but very informative. This article mentions that: "The most common size of a physical block is currently pegged at 16KB". Now, for my Acer Aspire One, 'sudo tune2fs -l /dev/sda1' gives me a block size of 4K which is presumably the block size used by my operating sysem where the actual minimum physical block size written to the disk is 16K.  This is obviously quite a bit less than the 128K I used in my spreadsheet and if it is correct, the endurance will be significantly better. 

> The other thing is, we're only using a block level endurance specification of 10000, which I think is extremely conservative to say the least. Even 100000 would be conservative.
Agreed, and that is supported by the Bitmicro article. 

Cheers, Pat.

---

### Post by mk6032 on 2010-05-17
I'm running Ubuntu 10.04 LTS amd64 and Windows 7 dual boot. The install worked beautifully and Ubuntu's bootup/shutdown speed is outstanding in comparison to Windows 7. Everything is lightening fast. I have an OCZ Agility series SSD ([http://www.newegg.com/Product/Product.aspx?Item=N82E16820227462](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227462)).

```

matt@mattslaptop:~$ uname -a
Linux mattslaptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
matt@mattslaptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
stepping	: 1
cpu MHz		: 525.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4198.20
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
stepping	: 1
cpu MHz		: 525.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4189.39
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

matt@mattslaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7749       1657       6092          0         90        442
-/+ buffers/cache:       1123       6625
Swap:         1772          0       1772
matt@mattslaptop:~$ bonnie++ -d /tmp -r 6092
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
mattslaptop     12G   328  99 140912  58 73120  36  1646  99 279228  59  5705 224
Latency             26335us     348ms     577ms   18008us   22283us   14196us
Version  1.96       ------Sequential Create------ --------Random Create--------
mattslaptop         -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 18330  57 +++++ +++ 29505  77 26768  81 +++++ +++ 26069  65
Latency              8949us    2190us    4107us     612us     209us      91us
1.96,1.96,mattslaptop,1,1274076376,12G,,328,99,140912,58,73120,36,1646,99,279228,59,5705,224,16,,,,,18330,57,+++++,+++,29505,77,26768,81,+++++,+++,26069,65,26335us,348ms,577ms,18008us,22283us,14196us,8949us,2190us,4107us,612us,209us,91us
matt@mattslaptop:~$ 

```

---

