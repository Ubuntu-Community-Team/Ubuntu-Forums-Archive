---
title: "how should i setup this system?"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by cpz on 2006-06-30
In my 2nd week of "playing" with Linux, I'm hooked.. tried quite a few flavors already and have come back to Ubuntu.  Seems to have the best of all worlds for my tastes..  It really is so cool to have tried 4 distros of linux in about 2 hours..  Apologize for the long post but could use the expert's opinions/guidance.

My dilemma as I'm not very creative.. I have 7 currently "unused" hard drives (list below) across 2 computers.  The thought is to have a downstairs linux server, upstairs HTPC.  These would be connected via Netgear's Rangemax wireless router (says 300mbs, but we'll see) to stream content anywhere & print from anywhere.  I say "unused" because i can move around my current data until something is setup.   

The linux server will support file and print sharing to the windows xp based HTPC (wireless), wife's computer (cat5) and work laptop (wireless).  Played with SMB and can get that working again.  Haven't tried CUPS yet.. but figure that's later.

1 Maxtor 40GB - IDE - currently running 6.06 ubuntu
3 WD 160GB - IDE
1 WD 160GB - SATA
1 Maxtor 300GB - SATA
1 WD 200GB - SATA

I would like to use RAID 5 and have the option to grow over time (i.e. buy more 300gb drives).  I have an extra 2 channel IDE PCI card based on the recommendation to use only 1 bus per drive.  The MB obviously has 2 IDE controllers too.

my thinking is to put the 200gb & 300gb sata drives in the xp HTPC box, the rest in the linux server.  keep /, et al on the 40gb maxtor (keeping some for tmp space), creating mdadm raid 5 on the 4x160 drives with no spare for the time being..

i have about 120gb of mp3, 200gb of backed-up dvds, and about 15gb of personal/work data.  i don't want to lose it (i know a backup plan is a must even with RAID)  so something like..
```

   htpcserver (RAID5)
      /music
         /artist 1..n
      /movies
         /archived movie 1..n
      /pics
      /data

```

```

   hptc (xp machine/ Media Portal (great software btw))
      c:
      d: current movies 
      e: recorded tv files (i.e. tivo)

```

is my thinking rationale?  other ideas or better ways to configure this?  any advice/guidance welcomed and appreciated.

thx

---

