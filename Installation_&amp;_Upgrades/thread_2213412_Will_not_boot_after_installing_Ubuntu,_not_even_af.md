---
title: "Will not boot after installing Ubuntu, not even after Boot Repair"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by Victor_Pambuccian on 2014-03-26
I have installed Ubuntu on an Acer Aspire 3680, wiping out the existing Vista on it. It completed installation, but when it was time to restart, I got a screen letting me know that there is no Operating System. I tried Boot Repair, and it didn't fix the problem either. The code to be written down for Boot Repair is

[http://paste.ubuntu.com/7158020/](http://paste.ubuntu.com/7158020/)

Any ideas what to do next?

Thanks,

---

### Post by oldfred on 2014-03-26
I do not see anything obvious wrong with your install.

Is error from BIOS?
Are you booting from sda or hard drive in BIOS, not flash drive or CD still?

Review BIOS settings to see if anything may limit booting.
Is drive set for AHCI not IDE nor RAID?

---

### Post by westie457 on 2014-03-26
@ oldfred. 
```
[COLOR=#666666][FONT=Verdana]===================[/FONT][/COLOR][FONT=Verdana] fdisk -l:[/FONT]
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00085d6c

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232366079   116182016   83  Linux
/dev/sda2       232368126   234440703     1036289    5  Extended
/dev/sda5       232368128   234440703     1036288   82  Linux swap / Solaris


[COLOR=#ff0000]Partition outside the disk detected[/COLOR].

[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBR of sda.
[FONT=Verdana]Additional repair will be performed: unhide-bootmenu-10s[/FONT]
```

Could this be the problem?

---

### Post by oldfred on 2014-03-26
If you have installer DVD still mounted it gives that error. 

Hard drive seems ok.
drive shows 234441648 sectors which is more than 234440703  shown for end of extended and swap.And extended starts after end of sda1 so it does not overlap.

---

### Post by fantab on 2014-03-26
While you are reviewing BIOS settings check under 'Boot' for HDD boot priority, ie which HDD is set to boot first. Is it HDD or USB or DVD? HDD should be first.
If USB or DVD is first and if there is either a DVD or USB plugged in then BIOS will search for those and report the error you have....

---

