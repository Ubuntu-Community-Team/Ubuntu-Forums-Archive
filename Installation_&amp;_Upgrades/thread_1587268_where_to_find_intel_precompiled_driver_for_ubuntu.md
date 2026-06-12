---
title: "where to find intel precompiled driver for ubuntu"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by psihokiller4 on 2010-10-03
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
``````
uname -a
Linux dusanlaptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```I need for:
[http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/tut1b](http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/tut1b)

I know it's old but I don't know where else to start


it sends me to here:
[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+915GM%2fGMS%2c+910GML+Express+Chipset+Family&ProdId=1862&LineId=1101&FamilyId=39](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+915GM%2fGMS%2c+910GML+Express+Chipset+Family&ProdId=1862&LineId=1101&FamilyId=39)

and here

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=1862&#9001;=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=1862&lang=eng")



witch sends me here:

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

and I'm not willing to risk much I don't want to screw my system again

in this year in learning process I did it minimum 9 times witch had to be formated

and I need some help

---

### Post by pastalavista on 2010-10-03
Ubuntu should support your grapics chip. Please post the output of ```
sudo lshw -c video
```

---

### Post by psihokiller4 on 2010-10-03
```
sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f7f00000-f7f7ffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:f7ec0000-f7efffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7f80000-f7ffffff
```

---

### Post by efflandt on 2010-10-03
Not sure exactly what you are trying to do, or why, but the Intel video drivers are already included in Ubuntu, so there is nothing more to install for them.  Are you having any particular problem with your video?

Not sure if a newer Ubuntu version would do anything different for your particular video.  I am guessing from your kernel version that you are running something older than Ubuntu 9.10.

If you install video drivers other than through Hardware Drivers (which would not list any other driver for yours) or Ubuntu packages, then Ubuntu is not going to know anything about them and such drivers may need to be reinstalled after any kernel updates.

---

### Post by psihokiller4 on 2010-10-03
ok thanks I'm trying to get started on openGL programming


and it's difficulty on every step with all libs and programs and everything I'm trying for 4 days now constantly and still didn't get a little result

if i already have graphic accelerator driver than i'll just title it solved thanks guys

---

