---
title: "Terminal Won't Load"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by swalsh on 2005-04-27
So i got Kubuntu installed finally at about 3am last night.  I was trying to load up my sound card drivers and installed some other software packages from Kynaptic.  The terminal won't load, firefox won't load and some other programs won't load up.  I see them in the task bar with the hourglass, but then they just disappear.  What's the deal?

Thanks

---

### Post by alastair on 2005-04-27
I don't know. But the first thing I would do is :

a) check system logs e.g. /var/log/syslog
b) check for what's written (any logs?) in your home dir

For b), I'd switch to a VT (CTRL+ALT+F1, say), then login as myself and :

ls -lrta

i.e. latest/newest files/dirs are at the bottom of the list. There might be some logs, or something worth looking at.

---

### Post by nad on 2005-04-27
This is typical of low resource problems. What are your computer specs?

---

### Post by swalsh on 2005-04-27
I have an AMD 1.2Ghz, 512 RAM, GeForce 5200.  I'm running Hoary off a 3gb partition with a 180mb swap drive.  The same thing happens with several other programs also.  I would like to convert over to Kubuntu permanantly, but don't want to leave Windoze in the dust.  There are still some apps that I need over there.

TIA

---

### Post by nad on 2005-04-28
You are at the low end with your 3G partition and 180M swap size.

What is the ouput of: df -hl  and: cat /proc/meminfo  ?

---

### Post by swalsh on 2005-04-28
df -hl:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             3.1G  2.4G  519M  83% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                  3.1G  2.4G  519M  83% /.dev
none                  5.0M  2.9M  2.2M  57% /dev
/dev/hda1              54G   40G   15G  74% /media/windows

cat /proc/meminfo

MemTotal:       516500 kB
MemFree:         28304 kB
Buffers:         26916 kB
Cached:         233956 kB
SwapCached:          0 kB
Active:         296280 kB
Inactive:       149164 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       516500 kB
LowFree:         28304 kB
SwapTotal:      176672 kB
SwapFree:       173784 kB
Dirty:              96 kB
Writeback:           0 kB
Mapped:         253396 kB
Slab:            33048 kB
CommitLimit:    434920 kB
Committed_AS:   566352 kB
PageTables:       2760 kB
VmallocTotal:   516016 kB
VmallocUsed:      5180 kB
VmallocChunk:   510684 kB

---

### Post by nad on 2005-04-28
Well, there is little to suspect here. I figured that your partition was nearly full, but, that wouldn't cause program opening problems unless your usage were closer to 100%. Your ram memory is fine, only about half allocated. Maybe run memtest to check it out.

Have you read any of your logs? After firefox fails to open, type: tail /var/log/messages  to see if anything is written to the system log. You could also tail /var/log/gdm/:0.log and ~/.xsession-errors  and view the running table of processes by running the top program to see if there is an obvious culprit hogging resources.

---

### Post by swalsh on 2005-04-28
I am definetly an idiot.  Firefox wouldn't load by using the Synaptic Installer, but as soon as I downloaded it from the site, it worked just fine.  I did figure out how to get to "a terminal", but not the one I wanted.  I can work out of the "Konsole" just fine.  Thanks for all the quick replies.  That's one of the main reasons I switched.  Wonderful user support.  

Thanks again

---

### Post by nad on 2005-04-28
You're welcome. I glad you were able to work it out.

---

