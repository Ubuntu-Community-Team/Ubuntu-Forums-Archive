---
title: "Software RAID Install Questions"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by SupaRice on 2007-02-10
So, I've tried installing Ubuntu on my system.  It's an Asus mb with a "raid" option for SATA drives. I've tried to follow this guide, which I've used successfully in the past:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

However on this system, after installing dmraid it tells me that there are no raid drives.

Ubuntu sees all of my drives individually just fine.  However I want to setup some form or RAID on them.  I'm stuck and confused.  Is there an easier way to setup software RAID in Unbuntu?  I've tried searching without luck.  I've done this many times before with Debian, and it's really easy.  Am I just being dumb and missing something?

Thanks in advance for your help!

Output I get with dmraid...
```

root@ubuntu:/home/ubuntu# dpkg-reconfigure dmraid
 * Shutting down DMRAID devices...                                       [ ok ]
 * Setting up DMRAID devices...                                          [ ok ]
root@ubuntu:/home/ubuntu# find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

```

```

root@ubuntu:/home/ubuntu# dmraid -ay
No RAID disks
root@ubuntu:/home/ubuntu# dmraid -r
No RAID disks
root@ubuntu:/home/ubuntu# dmraid -ay -vvvv
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/hdb
NOTICE: /dev/hda: hpt37x discovering
NOTICE: /dev/hda: hpt45x discovering
NOTICE: /dev/hda: isw    discovering
NOTICE: /dev/hda: lsi    discovering
NOTICE: /dev/hda: nvidia discovering
NOTICE: /dev/hda: pdc    discovering
NOTICE: /dev/hda: sil    discovering
NOTICE: /dev/hda: via    discovering
NOTICE: /dev/sda: hpt37x discovering
NOTICE: /dev/sda: hpt45x discovering
NOTICE: /dev/sda: isw    discovering
NOTICE: /dev/sda: lsi    discovering
NOTICE: /dev/sda: nvidia discovering
NOTICE: /dev/sda: pdc    discovering
NOTICE: /dev/sda: sil    discovering
NOTICE: /dev/sda: via    discovering
NOTICE: /dev/sdb: hpt37x discovering
NOTICE: /dev/sdb: hpt45x discovering
NOTICE: /dev/sdb: isw    discovering
NOTICE: /dev/sdb: lsi    discovering
NOTICE: /dev/sdb: nvidia discovering
NOTICE: /dev/sdb: pdc    discovering
NOTICE: /dev/sdb: sil    discovering
NOTICE: /dev/sdb: via    discovering
No RAID disks
WARN: unlocking /var/lock/dmraid/.lock
root@ubuntu:/home/ubuntu#

```

---

### Post by vgrisham on 2007-02-11
I found myself in the same situation. My ASUS mobo has two raid controllers, and neither Dapper nor Edgy could finish an install onto a raid array. 

I'm going to try a pure software raid within the next few weeks, and I plan on using these instructions: 

[http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188) 
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

Keep in mind that you will not use your onboard/BIOS raid controller to accomplish this. Ubuntu will fake the whole array.

Good luck,
Vaughn

---

### Post by SupaRice on 2007-02-12
I guess what is holding me up is that I follow the directions and install dmraid, and then it doesn't see anything:

```

root@ubuntu:/home/ubuntu# dmraid -ay
No RAID disks
root@ubuntu:/home/ubuntu# dmraid -r
No RAID disks
root@ubuntu:

```

I'm pretty sure I'm just doing something wrong, because it looks like Ubuntu sees it.  But it doesn't show up in GParted:

[img]http://i6.photobucket.com/albums/y213/suparice/Screenshot-1.png[/img]

---

