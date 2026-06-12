---
title: "hdparm -S spindown doesn't work after upgrade to 16.04 anymore"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by seanloony on 2016-04-24
```
sudo hdparm -S 10 /dev/disk/by-id/... 
```
has no effect after upgrade

entries in /etc/hdparm.conf are ignored too:
```

/dev/disk/by-id/ata-WDC_WD60EZRX-blabla {
   spindown_time = 150
}
```
```


sudo hdparm -y /dev/sdX 
```
still works


In 15.10 the -S switch worked as expected manually and with the /etc/hdparm.conf

---

### Post by seanloony on 2016-05-03
Solution:
Use the graphical gnome-disks utility, set there the spin down parameter.
This tool writes a config file for the specific drive to /etc/udisks2 which contains the value for the hdparm -S  value:
e.g.:
```

cat /etc/udisks2/<yourhdd>.conf
[ATA]
StandbyTimeout=241

```

---

