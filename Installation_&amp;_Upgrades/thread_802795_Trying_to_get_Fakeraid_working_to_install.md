---
title: "Trying to get Fakeraid working to install"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by RobbieCrash on 2008-05-21
I'm trying to install on a fakeraid array, and one hdd is not showing up in one of my arrays. 

I have 8 hdds in 4 arrays. The nvidia raid bios says all are healthy, and all arrays show up as active in ubuntu. 

3 of the arrays show up correctly, but one of them shows up as just the one drive. 

The drive that is not showing up in the dmraid discovery is /dev/sdd which does show up in gparted and is mountable.

The array that is messed up contains one WD 160GB drive, and one WD 120GB drive. The nvidia bios shows this correctly as a 111.9 GB drive. Before someone tells me I can't use mismatched drive sizes, one of the other arrays is comprised of a WD200 and a WD220, another a WD300 and a WD350.

Following this: [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

Got me this information:

Relevant portion of 'dmraid -ay -vvv -d'
```

NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: nvidia metadata discovered
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: nvidia metadata discovered
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
```

```
# dmraid -b
/dev/sdh:    586072368 total, "WD-WCAMR1181959"
/dev/sdg:    625142448 total, "WD-WCASF0081172"
/dev/sdf:    976773168 total, "WD-WCAS83623195"
/dev/sde:    976773168 total, "WD-WCAS83632135"
/dev/sdd:    234441648 total, "WD-WMA8C4315678"
/dev/sdc:    390721968 total, "WD-WMAL81300703"
/dev/sdb:    312581808 total, "WD-WCAP99925748"
/dev/sda:    390721968 total, "WD-WMAEH1678357"
```

```
# dmraid -rD
/dev/sdh: nvidia, "nvidia_idifdahh", mirror, ok, 586072366 sectors, data@ 0
/dev/sdg: nvidia, "nvidia_idifdahh", mirror, ok, 625142446 sectors, data@ 0
/dev/sdf: nvidia, "nvidia_ddefbebi", mirror, ok, 976773166 sectors, data@ 0
/dev/sde: nvidia, "nvidia_ddefbebi", mirror, ok, 976773166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_agbfbeih", mirror, ok, 390721966 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_efehehea", mirror, ok, 312581806 sectors, data@ 0
/dev/sda: nvidia, "nvidia_agbfbeih", mirror, ok, 390721966 sectors, data@ 0
```

Both of the HDDs in the questionable array are working harddrives, and have no filesystems on them.

Anyone know why the second hdd won't show up?

---

### Post by iaculallad on 2008-05-21
Use the Ubuntu alternate cd and it works effortlessly with raid. Try not to use dmraid.

---

