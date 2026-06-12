---
title: "Ubuntu 7.10 and SATA HDD via SATA RAID controller INITIO inic162x"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by AsleepHunter on 2007-10-19
Hi everyone,

I have an anoying problem. I was using Ubuntu 7.04 then I bought 400Gb SATA HDD, there were no sata connections in my motherboard so I had to buy a SATA controller. So now I have SATA Raid controller INITIO inic162x everything worked fine until I enabled ntfs-3g after that I could't mount my SATA, so I had to leave it ro. Now I am trying to install Ubuntu 7.10 booting from Live CD, but  it don't see my SATA at all. I think maybe it is because Ubuntu 7.10 has intergrated ntfs-3g or maybe something else.. Could anybody help me and sugest some work around how could I install Ubuntu 7.10 on my SATA HDD. I forgot to say that i have a dual boot system and on windows xp everything works fine. Maybe there is a way to disable that integrated ntfs-3g from live cd that I could see my SATA??

Sorry for my bad english.

---

### Post by beaver86 on 2007-10-30
Did you find a solution for this SATA controller ?

Because, you're not the only one having this problem...

---

### Post by AsleepHunter on 2007-10-30
Actualy yes but no , there is a way to make ubuntu to see your HDD but it may corupt your data or even hdd, you can try to use older kernel for example latest version which was in fasty, but i had a lot of problems ( video drivers, usb suport..), so now i will wait while someone wil fix that inic162x driver to suport 48lba.

---

### Post by colgate on 2007-11-14
hi,
in this thread
[http://ubuntuforums.org/showthread.php?t=597705](http://ubuntuforums.org/showthread.php?t=597705)

I did some experimets ... please, take a look!

Federico

---

