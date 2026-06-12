---
title: "installation Problems"
date: 2022-01-09
forum: Installation &amp; Upgrades
---

### Post by ratty01 on 2022-01-09
Hi I've used Ubuntu for a number of years but still a novice I'm afraid. Stupidly I did an upgrade from 20.04 to 20.14 and messed the system up. The system has a SSD with operating system on and a couple of Hard drives for data etc. So I've now got to a point where I've done a clean install erased SSD several times trying 20.04 and I get to the home screen but the system is unusable really slow and often locks. It has a N Vidia graphics N610-2GD3H/Lp  card which I saw some errors at on point but it seems to have the driver installed when I look at the N Vidia X Server 390.144. Can someone help with ideas at what to do next as I've been 3 days on this now and at a bit of a loss. I just want to get back to 20.04 it had been running well for months :-(

Cheers

John

---

### Post by ratty01 on 2022-01-09
so looking in the logs I get lots of watchdog: BUG soft lockup - CPU#2 stuck for 23s! [alsa-sink-HDMI :1570]

also INFO: task ...blocks

---

### Post by ratty01 on 2022-01-09
I've removed
 Nvidia card and using on board graphics and system seems ok. Will now try a fresh install of 21.10 and will report back.

---

### Post by yancek on 2022-01-09
>  Will now try a fresh install of 21.10 and will report back. 

Just a suggestion as 21.10 is a short term release.  If your20.04 is currently functioning, you might wait untl April when 22.04 (LTS) is released.

---

### Post by ratty01 on 2022-01-09
Thanks Yancek good suggestion - It was a disaster so back on 20.04 - Now need to get everything working again ;-) Anyway I have a working system again and the graphics card has gone in the box of bits. I only put it in because I need ed a HDMI connection and it has been working fine for a year. Anyway found another way to connect and back up and running.

Certainly makes me explore ubuntu a bit more than normal :-)

Cheers all this thread can be closed

---

### Post by MAFoElffen on 2022-01-11
To close the as "solved", go to the Thread Tools link in the upper right of the page, and select "solved".

---

### Post by guiverc on 2022-01-11
FYI:

Ubuntu has two fully supported & QA-tested paths.  (QA=Quality Assurance)

From one release to the next (ie. from 20.04 that was to 20.10; or the 2020-October release).
From one LTS release to the next LTS release (ie. from 20.04 to 22.04.1; release opens **after **the .1 has been released).

I have no idea what you actually upgraded to; as the format of Ubuntu releases is *year.month* and of course there is no 14th month (20.14), so you could mean 21.04 (*thus skipping 20.10*) or something very different.  

Yes Ubuntu tools will allow upgrade (*if they can*), thus your attempt to go to 20.10 would have allowed you to *release-upgrade* to 21.04 (the next *supported* release) and that path is CI tested, but it didn't get the QA testing that 20.04 to 20.10, or 20.10 to 21.04 received.  The path (eg. 20.04 to 21.04) does get some testing, but it's only a fraction of the intended path (20.04->20.10, 20.10->21.04). It exists for users who failed to *release-upgrade* in time.

I didn't see you specify if it's a desktop or server install; but if I have issues with a desktop *release-upgrade* I just re-install over it, as you can re-install a desktop system
- without touching user files
- having the system auto-reinstall your *manually installed *packages IF available in Ubuntu repositories for the new release

System directories are wiped before being re-install, so if you have server apps (which regularly store conf/config files inside system directories) these of course will need to be restored from backups; but desktop apps don't do that; storing conf/config files in $HOME or user directories which aren't touched UNLESS you manually opted to format during install. This install type is triggered by the non-format of partitions.  

 This method of install also works when changing releases; eg. I have systems where I've *jumped* from 20.10 to 21.04, back to 20.04, returned to 21.04 etc and loads of what seem like stupid jumps; but it's the install I'm QA-testing & my user files (esp. music) & programs (*I don't use default music players purposely so I can ensure apps survive re-install*) are part of how I assess it all works as expected.   This type of re-install may allow you to *fix* issues with your *incorrect/invalid* 20.14*???* release, or if you prefer go back to 20.04 LTS. esp. if it's a desktop system.  Of course I'd backup first.

(Our next release is 20.04.4; then 22.04.. so my tests are usually what's next to be released; currently *jammy* and *focal.4* are my most common switches; more so once 21.04 is EOL)

---

