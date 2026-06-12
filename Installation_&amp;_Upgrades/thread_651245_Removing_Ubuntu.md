---
title: "Removing Ubuntu"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by kenubu on 2007-12-27
I have Ubuntu installed in a dual boot with Windows on my laptop.  Is there a way to remove Ubuntu and give the disk space back to Windows?  I don’t care about the data in Ubuntu but I would like to preserve the Windows install.

---

### Post by mellowd on 2007-12-27
Use gpart to remove the ubuntu partitions and then fix your mbr. You should then be able to use that hard drive space for Windows again

---

### Post by tech9 on 2007-12-27
> **kenubu said:**
> I have Ubuntu installed in a dual boot with Windows on my laptop.  Is there a way to remove Ubuntu and give the disk space back to Windows?  I don’t care about the data in Ubuntu but I would like to preserve the Windows install.

yes....
bootup with LiveCD
use gparted and delete the partition
Then create another partition and format as NTFS... you may need to use another partition tool for that though

---

### Post by tech9 on 2007-12-27
> **mellowd said:**
> Use gpart to remove the ubuntu partitions and then fix your mbr. You should then be able to use that hard drive space for Windows again

mellowd beat me to it... but as the saying goes "great minds think alike" :)

---

### Post by mellowd on 2007-12-27
> **tech9 said:**
> mellowd beat me to it... but as the saying goes "great minds think alike" :)

:P

---

### Post by kenubu on 2007-12-27
How do I run gpart?  How do I fix  the mbr without destroying Windows?  I'm thinking fdisk /mbr but I think that destroys Windows too?

---

### Post by lswest on 2007-12-27
also, if you want to add the free space to your XP partition just have to resize the XP partition.  Otherwise it's as they say.  and to fix the mbr stick in your XP cd, go into a recovery console and type "fixmbr" i believe...

---

### Post by mellowd on 2007-12-27
Run gpart off the live CD.

Are you running windows XP? If so boot off the Windows CD and go into the recovery console. Once there log onto Windows and then type this at the cli:

```
fixmbr
```

Restart the PC and you're done, it should go straight into Windows. Do this after you have removed the linux partitions

---

### Post by terminal on 2007-12-27
Duh .. 

start  Windows
click start-->run type diskmgmt.msc
there it will show ur windows and linux partition 
Linux partition will be shown unknown . ust right click and format it as ntfs .

---

### Post by tech9 on 2007-12-27
> **kenubu said:**
> How do I run gpart?  How do I fix  the mbr without destroying Windows?  I'm thinking fdisk /mbr but I think that destroys Windows too?

Boot LiveCD

System>Administration>Partition Editor

then 

```
fixmbr
```

---

### Post by mellowd on 2007-12-27
> **terminal said:**
> Duh .. 

start  Windows
click start-->run type diskmgmt.msc
there it will show ur windows and linux partition 
Linux partition will be shown unknown . ust right click and format it as ntfs .


Why Duh?

doing it your way will still leave grub, and on the defaults it wont boot at all. Doing it the correct way is better

---

### Post by tech9 on 2007-12-27
> **terminal said:**
> Duh .. 

start  Windows
click start-->run type diskmgmt.msc
there it will show ur windows and linux partition 
Linux partition will be shown unknown . ust right click and format it as ntfs .

It's not polite to insult [kenubu]("http://ubuntuforums.org/member.php?u=402259"). You were new at one point too; and didn't know much about partitions!

---

### Post by tech9 on 2007-12-27
> **mellowd said:**
> Why Duh?

doing it your way will still leave grub, and on the defaults it wont boot at all. Doing it the correct way is better

+1

---

### Post by kenubu on 2007-12-27
Actually I'm running Windows 2000.  Is there a way to resize the Windows partitition without the CD?

---

### Post by mellowd on 2007-12-27
If you're running dynamic disks then yes. If not you may need an app like partition magic

---

### Post by tech9 on 2007-12-27
> **kenubu said:**
> Actually I'm running Windows 2000.  Is there a way to resize the Windows partitition without the CD?


I don't believe there is a way to resize your partition directly inside windows 2000. You could always look for free partitioning tools to download and resize it from there. I know Partition Magic was a good one for windows, but it's not free.

---

### Post by mellowd on 2007-12-27
> **tech9 said:**
> I don't believe there is a way to resize your partition directly inside windows 2000. You could always look for free partitioning tools to download and resize it from there. I know Partition Magic was a good one for windows, but it's not free.

True, I haven't bothered looking for a free app but there must be at least 1 out there

---

### Post by tech9 on 2007-12-27
> **mellowd said:**
> True, I haven't bothered looking for a free app but there must be at least 1 out there

mellowd, check this link out...

[http://partitionlogic.org.uk/index.html](http://partitionlogic.org.uk/index.html)

I found this tool called **partition logic**. I have already tried it, and it works really well. + it's free

It's an ISO - also same as preinstalled environment (bootable)

@ kenubu... try this out

---

