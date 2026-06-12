---
title: "Intrepid random freezes"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by raccoonone on 2008-12-01
I recently upgraded to 8.10 from 8.04, and I'm having problems with random freezes. Several times now I've been working (usually with Firefox), and it will stop responding and go all grey, then after a few seconds the mouse will stop responding also. If I wait for ~30secs it will go away and my computer is fine again.
Any suggestions for how I should go about trouble shooting this? At first I wondered if it might be a problem with BOINC since I have that installed and noticed that the default version in Intrepid is a beta version, but I manually upgraded to the latest stable release and it didn't help anything.

I'm running 8.10 x64, and the applications that I usually have open when I've experienced the freezes are: Firefox, Thunderbird, Evolution, Songbird, Pidgin

---

### Post by raccoonone on 2008-12-02
There seems to be some kind of problem communicating with the hard drive. Can someone interpret these errors for me? I don't know what exactly they mean. 

```
Dec  1 20:08:37 Conroe-linux kernel: [40891.820032] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 20:08:37 Conroe-linux kernel: [40891.820041] ata3.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
Dec  1 20:08:37 Conroe-linux kernel: [40891.820041]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
Dec  1 20:08:37 Conroe-linux kernel: [40891.820042]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Dec  1 20:08:37 Conroe-linux kernel: [40891.820044] ata3.00: status: { DRDY }
Dec  1 20:08:37 Conroe-linux kernel: [40891.820059] ata3: soft resetting link
Dec  1 20:08:37 Conroe-linux kernel: [40892.057003] ata3.00: configured for UDMA/33
Dec  1 20:08:37 Conroe-linux kernel: [40892.089064] ata3.01: configured for UDMA/33
Dec  1 20:08:37 Conroe-linux kernel: [40892.089074] ata3: EH complete
Dec  1 20:08:47 Conroe-linux kernel: [40902.088032] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 20:08:47 Conroe-linux kernel: [40902.088040] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Dec  1 20:08:47 Conroe-linux kernel: [40902.088040]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  1 20:08:47 Conroe-linux kernel: [40902.088041]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  1 20:08:47 Conroe-linux kernel: [40902.088043] ata3.01: status: { DRDY }
Dec  1 20:08:47 Conroe-linux kernel: [40902.088058] ata3: soft resetting link
Dec  1 20:08:47 Conroe-linux kernel: [40902.325005] ata3.00: configured for UDMA/33
Dec  1 20:08:47 Conroe-linux kernel: [40902.357067] ata3.01: configured for UDMA/33
Dec  1 20:08:47 Conroe-linux kernel: [40902.357078] ata3: EH complete
Dec  1 20:08:57 Conroe-linux kernel: [40912.356033] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 20:08:57 Conroe-linux kernel: [40912.356040] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Dec  1 20:08:57 Conroe-linux kernel: [40912.356040]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  1 20:08:57 Conroe-linux kernel: [40912.356041]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  1 20:08:57 Conroe-linux kernel: [40912.356043] ata3.01: status: { DRDY }
Dec  1 20:08:57 Conroe-linux kernel: [40912.356057] ata3: soft resetting link
Dec  1 20:08:57 Conroe-linux kernel: [40912.593122] ata3.00: configured for UDMA/33
Dec  1 20:08:57 Conroe-linux kernel: [40912.625187] ata3.01: configured for UDMA/33
Dec  1 20:08:57 Conroe-linux kernel: [40912.625196] ata3: EH complete
Dec  1 20:09:27 Conroe-linux kernel: [40942.628034] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 20:09:27 Conroe-linux kernel: [40942.628043] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  1 20:09:27 Conroe-linux kernel: [40942.628044]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  1 20:09:27 Conroe-linux kernel: [40942.628044]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  1 20:09:27 Conroe-linux kernel: [40942.628046] ata3.00: status: { DRDY }
Dec  1 20:09:27 Conroe-linux kernel: [40942.628061] ata3: soft resetting link
Dec  1 20:09:28 Conroe-linux kernel: [40942.865012] ata3.00: configured for UDMA/33
Dec  1 20:09:28 Conroe-linux kernel: [40942.897076] ata3.01: configured for UDMA/33
Dec  1 20:09:28 Conroe-linux kernel: [40942.897088] ata3: EH complete
Dec  1 20:09:58 Conroe-linux kernel: [40972.904031] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 20:09:58 Conroe-linux kernel: [40972.904040] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Dec  1 20:09:58 Conroe-linux kernel: [40972.904040]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  1 20:09:58 Conroe-linux kernel: [40972.904041]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  1 20:09:58 Conroe-linux kernel: [40972.904043] ata3.01: status: { DRDY }
Dec  1 20:09:58 Conroe-linux kernel: [40972.904057] ata3: soft resetting link
Dec  1 20:09:58 Conroe-linux kernel: [40973.133011] ata3.00: configured for UDMA/33
Dec  1 20:09:58 Conroe-linux kernel: [40973.165076] ata3.01: configured for UDMA/33
Dec  1 20:09:58 Conroe-linux kernel: [40973.165088] ata3: EH complete
Dec  1 20:10:23 Conroe-linux /USR/SBIN/CRON[16138]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

---

### Post by raccoonone on 2008-12-12
I reported this as a bug. <https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307068>

---

### Post by 2hot6ft2 on 2008-12-12
Earlier today someone posted that pidgin has a leak and that if left running it would gradually fill up to 512MB of RAM. Since it's in your list I would start there. Shut pidgin down reboot and see if it still does it without pidgin running. Pure hearsay for what it's worth.

Also pulse audio can cause freezes and the fix for that is here since you have songbird in your list. [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) It also fixes one issue in firefox.

---

### Post by raccoonone on 2008-12-12
I'll look at both of those, but I'm pretty sure I've tracked the problem down to a regression in the kernel. Sorry I forgot to mention that, but in the bug report I found that booting the 2.6.24 kernel solves the problem completely.

---

### Post by 2hot6ft2 on 2008-12-12
As long as you have it solved,

---

### Post by sideshowmel on 2008-12-30
I am having the same problem.  I don't run Pidgin on this machine, but I do run the system 24x7.  

I've been going through this for several months. I first noticed it in Debian Etch, then Debian Lenny, and now Intrepid as well.

I've thought at times it was because I was using mdadm for RAID1 and RAID0.  This problem doesn't go away for me unless I move the ata cables on the motherboard to different ports and start up the system again... sometimes going into runlevel 1 and running fsck on all partitions helps.  Other times I've been able to remove each drive from the mdadm array, zero the superblock, and re-add. If I do this procedure for both disks sometimes it works again.  I found this post by doing a search on strings in the error I pasted below, which are nearly identical to yours above, and this last time the problem occured, moving the SATA ports around did the trick (although in just typing this I can see my resource monitor spiking).  It's an extremely problematic issue, though. It mucks up all kinds of things from ssh to just booting the system.

Any additional info is appreciated. I will read the bug report, and see if I can provide any assistance... I can barely use the system at this point, but based on previous experience with this issue, I know only one thing that will fix it, and even that only lasts a few weeks... a full reinstall.

EDIT... it's baaaackk...
it just took over 4 minutes to submit all the text above the edit.
Also, if it helps... I can hear the HDD "skipping", or something to that effect, immediately before the whole system locks up for several minutes. 
And here are my logs...
```

Dec 30 19:01:11 kaya kernel: [   82.984057] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 30 19:01:11 kaya kernel: [   82.984807] ata4.00: cmd c8/00:20:02:1a:9f/00:00:00:00:00/e0 tag 0 dma 16384 in
Dec 30 19:01:11 kaya kernel: [   82.984811]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 30 19:01:11 kaya kernel: [   82.984942] ata4.00: status: { DRDY }
Dec 30 19:01:11 kaya kernel: [   82.984999] ata4: soft resetting link
Dec 30 19:01:11 kaya kernel: [   83.228455] ata4.00: configured for UDMA/133
Dec 30 19:01:11 kaya kernel: [   83.244377] ata4.01: configured for UDMA/133
Dec 30 19:01:11 kaya kernel: [   83.244395] ata4: EH complete

```

---

### Post by sideshowmel on 2009-01-07
So it would appear that this is, in fact a hardware issue (at least in my case).  Like I said, my mem, mobo, proc, and HDD's all were good.  The one thing I never considered: power supply.

It would appear that one of my drives was consistently receiving too little power.  It just occured to me out of the blue when I was sitting there dealing with this problem and heard what I thought were my fans spinning down, then back up again, within 2 seconds.  

I had been using a splitter that splits one Molex 4-pin adapter into 2 SATA power adapter.  I changed the wire configurations around so that each 4-pin Molex was only allocated one HDD per.  Since then I show 2 days of system uptime with no recurrence of this problem.  

I've since ordered a new power supply, as this one is most certainly about to die.

Thanks for the responses, everyone. Sorry to waste time and effort!

---

