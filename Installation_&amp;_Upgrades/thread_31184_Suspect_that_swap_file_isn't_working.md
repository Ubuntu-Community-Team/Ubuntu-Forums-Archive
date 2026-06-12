---
title: "Suspect that swap file isn't working"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by petehall on 2005-05-02
I'm concerned that my installation of Ubuntu isn't using the swap file at all. I've searched the Internet a little and found a lot of people with what seems to be the same problem, and the response has always been "That's intentional, Linux doesn't use the swap file unless it really really has to, because it makes the system slow to a crawl."

I have 243MB of available RAM in my system. If I open a large image in the GIMP, the RAM usage will generally creep up towards 100%. When it is all used up, the system locks up and is pretty much unusable for about five minutes, until it has sorted itself out. If I've got music playing, I'll hear half-second bursts every twenty seconds or so. I'll admit that this fits my description of "slowing to a crawl", but obviously everyone will have a different idea of what this should mean.

In System Monitor, I currently have the following information displayed:

User memory: 144.0MB of 242.9MB 59.3%
Used swap: 0 bytes of 0 bytes nan %
Devices:
none /dev tmpfs 5.0MB 2.3MB 2.7MB 55%
tmpfs /dev/shm tmpfs 121.4MB 121.4MB 0 bytes 0%
/dev/hda2 / ext3 25.6GB 22.4GB 3.1GB 12%

The "Used swap: 0 bytes of 0 bytes" seems to be highly suspicious.

Please let me know if you can help me.

Thanks.

---

### Post by petehall on 2005-05-02
Okay, I've managed to get my swap working by performing the following three commands as sudo (where hda5 is my swap drive):

swapoff -a
/sbin/mkswap /dev/hda5
swapon -a

Clearly something is going wrong when the system is booting. I'll continue to investigate.

My fstab is:

proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/x	ext3	defaults,errors=remount-ro	0	1
/dev/sda1	/media/sda1	auto	sync,noauto,user,exec	0	0

---

### Post by petehall on 2005-05-02
Found the problem: [http://www.ubuntuforums.org/showthread.php?t=25438](http://www.ubuntuforums.org/showthread.php?t=25438)

---

