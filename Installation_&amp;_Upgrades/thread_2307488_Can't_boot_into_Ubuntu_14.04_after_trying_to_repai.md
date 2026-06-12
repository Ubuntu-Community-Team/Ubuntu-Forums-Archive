---
title: "Can't boot into Ubuntu 14.04 after trying to repair windows 7"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by leyle on 2015-12-25
I have both Windows 7 and Ubuntu 14.04 installed on my computer - on two different hard drives. After trying to repair a browser issue in Windows 7, I unthinkingly started Windows in the secure mode, which somehow messed with my boot options. I can't boot into ubuntu anymore.

The boot options screen does not show up anymore. 
When I tried to boot into ubuntu from BIOS, I could not find the disk ubuntu is supposed to be installed on. I tried all the boot options in the BIOS, but all lead to windows 7. 
 

I tried boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and got this: 

[http://paste.ubuntu.com/14208714/](http://paste.ubuntu.com/14208714/)


While I was in the Try-Ubuntu-Without-Installing mode, I also could not see the disk that ubuntu is on, only the windows disk.

Any idea what I could do?



PS: I hope I'm in the right thread, but this is my first time posting - I usually find solution to my problems just by browsing this forum, but this time I'm stumped.

---

### Post by yancek on 2015-12-25
Boot repair only shows the 232GB device on which you have windows installed plus the flash drive.  If the drive with Ubuntu doesn't show in the BIOS, it might be dead.  Check that it is securely plugged on both ends.

---

### Post by leyle on 2015-12-25
checked that, but it is still securely inside the computer (- secured with 4 screws)

---

### Post by oldfred on 2015-12-25
No it is the electrical connections, both power & SATA cable.

My very old system with the wide parallel cables always came loose when I opened case. And it usually looked connected, but needed a firm push to fully seat. Most newer SATA cables now have locks so not an issue, some early ones did not.
Or just coincidence that a cable failed.

---

### Post by leyle on 2015-12-25
unfortunately, it really is connected. there are no cables - it is a built-in hard-drive that is directly connected to the laptop and fixed into place. It did not and does not move. Pressing on it does not change anything.

---

### Post by MAFoElffen on 2015-12-26
Please tell us what Brand and model of Laptop.

I concur with the others. From your pastebin, I see one physical hard drive, which has two partitions, which in Windows, since they are named as "Drive C:" and "Drive D:" in Windows file manager, would appear like they are two drives, but are just those 2 partitions on one 250GB drive.

99% of laptops only have room for one physical hard drive. There is that 1% of laptops that have 2 hard drives, but those are exceptions to the norm. If your laptop is one of those exceptions, then that 2nd drive is dead.

If you only have one physical hard drive and you had Ubuntu installed "within" that drive, which only has those 2 NTLS filesystems in those 2 partitions... Did you have Ubuntu installed as WUBI? (which is no longer supported...)

You said you "Repaired Windows..." When you toggled secure boot in BIOS by mistake, was it then that it removed the entry of Ubuntu from the Windows boot manager, that I see as the boot file on partition #1? ("Boot files: /bootmgr /Boot/BCD"...instead of going directly to the Windows system loader files) If so that was the start of where it lost connection to WUBI's boot manager.

To others, nostalgiac WUBI trivia: WUBI used the Windows Boot manager as it's boot manager... To get it the entry back:
[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

So if that was WUBI-- And if you get that back up... And if you don't want to lose what you had, you might start thinking seriously about migrating that to a traditional installation. WUBI does not work with Win 8.x and newer. So when you do your free upgrade from Win 7 to Win 10, if you do not migrate Ubuntu (WUBI) to traditional, it will fail again. (permanently)

---

