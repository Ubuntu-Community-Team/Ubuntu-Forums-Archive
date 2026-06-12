---
title: "Rough start but need some help"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2010-08-31
Hey guys I highly doubt I may get my issue resolved here. But here goes nothing. I had to work for a client of my boss and install and ancient relic on their machine known as "SCO Unix 5 OpenServer"
And all went well and it installed no problems. I went through a lot of stuff to try to get the system to pick up their tape drive, but it turned out the scsi controllers on the board were not functioning. We had to send her data off one of the tapes to her corporate office after recovering it using WinTAR. The lady  sent back the data and said in order for her to read the data we had to install the software in unix, this is where the spawn of hell comes in. The scsi cdrom isnt being read, I try "mount -r /dev/cd0 /mnt/cdrom" no scsi device found, when it was working yesterday. I dont get it. so I gave up. So I contacted her and said what program is used to read the data, she says Acucobol, I have been looking everywhere for a windows replacement to read this data, with my luck it has not turned out great. So she sent me her program to install in unix, but I have no idea how to begin the installation or even know where it starts. I grabbed the list of files to the program and maybe you guys can point me in the right direction. Files listed below:

```

a_termcap
AcuPgms.lib
acushare
cblconfig
cblhelp
cblutil
config.311
config.base
config.base.1201
config.base.627
config.base.powd
config.base.pre3.1
config.base.prebin
config.base.prebin.test
config.base.predp
config.base.prepo
config.base.prey2k
config.base.sbii
config.base.sjr
config.base.wd
config.base.wdak
config.baseim
config.bob
config.carlos
config.daniela
config.evie
config.good
config.heidi
config.kevin
config.kirsten
config.kp
config.mdl
config.mgt
config.mike
config.mitzi
config.nancy
config.newguy
config.res
config.rick
config.run
config.run.bob
config.run.carlos
config.run.daniela
config.run.evie
config.run.heidi
config.run.kevin
config.run.mike
config.run.mitzi
config.run.nancy
config.run.rick
config.run.sally
config.run.steve
config.run.suzanne
config.run.unisun
config.runncp
config.runnsup
config.sally
config.sally.kp
config.sally.orig
config.sbii
config.sjr
config.steve
config.susan
config.suzanne
config.suzie
config.temp
config.unisun
config.wd
config.wd.old
config4.base
config85.c
direct.c
filetbl.c
filname.txt
fowlerpo.os
fowlerpo.par
fowlerpo.rc
libacuterm.a
libclnt.a
libconnectc.a
libfsi.a
liblib.a
libmemory.a
libmessage.a
libruncbl.a
libstdlib.a
libvision.a
logutil
lp0
Makefile
namelist
READ_ME
RELEASE
runcbl
runcbl.alc
ship.sums
sub.c
sub.h
sub85.c
temp
termcap.0803
termcap.22200
termcap.22500
termcap.mgt
termcap.run
termcap.sjr
uucp_command
vio
vutil
zqzf5lp

This is in a different directory

config.base
config.idy
config.msg
config.run
filname.txt
namelist
termcap.run


```

Any help would rock and will greatly be appreciated!.

---

