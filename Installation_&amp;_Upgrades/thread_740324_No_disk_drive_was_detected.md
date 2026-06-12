---
title: "No disk drive was detected"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by tcity5 on 2008-03-30
The installation was working quite well until Partition Time.  It says that no disk drive was detected.  I have a Seagate 120GB internal as my hard drive, and it worked fine when I had Windows XP installed.  I looked through the drivers I could choose and tried both 'seagate' and 'sg'.  Neither worked, and it is still undetected.  Any ideas?

---

### Post by StOoZ on 2008-03-30
can you post the output of:
> lshw

---

### Post by tcity5 on 2008-03-30
I'm sorry, I don't think I understand.  This is my first time installing linux on a local machine.  What do you need me to post?

---

### Post by pseudo-random on 2008-03-30
```
lshw
``` is a command you need to enter in a terminal to retrieve hardware information.
I take it you won't be able to get there since it won't install.
Do you know more about the Hard drive(s). Is it RAID by any chance?

---

### Post by tcity5 on 2008-03-30
It is a Seagate Model ST3120020A 120GB.
Configuration VAK-03

Not much other information on there.  I might run the BIOS to see if that will detect it.

Edit: Okay, I ran the BIOS and the installation now detects the Hard Drive.  should I go with resize IDE1 master, use entire disk, use entire disk with LVM, or use entire disk with encrypted LVM?

---

### Post by SeePU on 2008-04-01
> Edit: Okay, I ran the BIOS and the installation now detects the Hard Drive.  What do you mean by 'ran the BIOS?'

I have a similar (same?) problem in that I cannot boot up a Live CD of any recent distro (Ubuntu, Fedora etc.) and be able to 'see' my partitions.   GParted displays 'no disk drive was detected.'

Is anyone else having this problem? 

My theory was that something in the newer kernel effects (older?) IDE hard drives.    I am only suggesting this, though, because other IDE drives were tried in different hardware but the same problem existed.   I am using an older Compaq Deskpro EN SFF with a 20GB IDE (ATA) HDD.  

If I tried a distro with an older kernel (pre-2.6.20), the drives/partitions were detected.   

Any ideas????

---

### Post by tcity5 on 2008-04-03
> **SeePU said:**
> What do you mean by 'ran the BIOS?'

I have a similar (same?) problem in that I cannot boot up a Live CD of any recent distro (Ubuntu, Fedora etc.) and be able to 'see' my partitions.   GParted displays 'no disk drive was detected.'

Is anyone else having this problem? 

My theory was that something in the newer kernel effects (older?) IDE hard drives.    I am only suggesting this, though, because other IDE drives were tried in different hardware but the same problem existed.   I am using an older Compaq Deskpro EN SFF with a 20GB IDE (ATA) HDD.  

If I tried a distro with an older kernel (pre-2.6.20), the drives/partitions were detected.   

Any ideas????

As soon as you power on your computer, run the BIOS by tapping F1/F2 until you see your BIOS.  It is usually one of these keys that brings it up.  Supposedly it is sometimes 'Del', but I have never seen that.  Once in your BIOS, find your main disc drive and choose auto detect.

---

