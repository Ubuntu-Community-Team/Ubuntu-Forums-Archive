---
title: "Upgrade doesn't work! :-("
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by claus on 2007-09-23
Hi all,

for some reason I'm not able to install newer versions of Ubuntu (I'm still using "Breezy") because when the partitioner shows up and I am asked to format the old partitions (I have boot, swap, root, usr, and home in separate partitions each), I am getting the error message that there is no 'root' filesystem (I'm using ReiserFS).

Here's my *fstab*:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs defaults        0       1
/dev/hda1       /boot           reiserfs notail          0       2
/dev/hda8       /home           reiserfs defaults        0       2
/dev/hda7       /usr            reiserfs defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Since I would really love to ugrade to the latest Ubuntu version, my question is, how do I solve this problem?


TIA,

Claus

---

### Post by Pumalite on 2007-09-23
I'm not sure 'Breessy' is supported anymore. You might have to do a clean install of a newer version. Someone will come to confirm or deny this.

---

### Post by claus on 2007-09-23
"Breezy" isn't supported anymore officially, and--as I wrote--I would like to install the *lastest* version, but I would like to keep all of the data inside my 'home' partition. I want to format all of the other partitions--but that's where I'm stuck because of this error message.

Claus

---

### Post by oilchangeguy on 2007-09-23
> **Pumalite said:**
> I'm not sure 'Breessy' is supported anymore. You might have to do a clean install of a newer version. Someone will come to confirm or deny this.

i agree. it's best to do a clean install of a newer version. before you do, backup your data. also post your system specs, it may not be able to run a newer version.

---

### Post by claus on 2007-09-23
> **oilchangeguy said:**
> ... also post your system specs, it may not be able to run a newer version.
Processor: AMD K6 II/350 Mhz
Board: DFI K6BV 3+
Memory: 256 MB
CD-ROM: 48x
Graphics card: NVIDIA RIVA TNT 2 64
Sound card: SoundBlaster 16-bit
No-name ethernet card

I know that the hardware is outdated, but I can't afford a new PC right now.

Thanks for your feedback!

Claus

---

### Post by bapoumba on 2007-09-23
Have you tried a dist-upgrade to dapper?
If choosing to go for a fresh install, did you test from the alternate cd ?

---

### Post by claus on 2007-09-23
> **bapoumba said:**
> Have you tried a dist-upgrade to dapper?
If choosing to go for a fresh install, did you test from the alternate cd ?
Yes, I downloaded & burned the image for Dapper. The live CD works fine (if that's what you are referring to), but, as I said, I am getting this error message 'no root filesystem' when trying to *install* Dapper (I haven't tried higher versions yet, because I wanted to solve this problem first).

Oh, wait a minute! Did you mean by 'dist-upgrade',  via 'apt-get'? No, I didn't try this because I ran into problems when I tried this with Breezy.(I can't recall which ones, though; it has been a while ago.)

Thanks for your response, ;-)

Claus

---

