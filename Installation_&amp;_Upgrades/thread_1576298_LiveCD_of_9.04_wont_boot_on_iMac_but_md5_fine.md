---
title: "LiveCD of 9.04 wont boot on iMac but md5 fine"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Amacha on 2010-09-17
Trying a LiveCD of 9.04 and it wont boot on iMac 8,1 with Intel CoreDuo2. Using rEFIt or not doesn't help, boot to cd gives a black screen with overlength cursor and takes no keyboard input (CAPS light wont even come on). No splash screen or chance to get a prompt. md5 check of cd against iso file using dd is fine and matches published md5. Tried alternative (text) cd iso and same story. Tried Bootcamp for the initial partitioning and no difference. Mac installation cd boots fine as does OSX, burned cd from multiple machines and no joy. Graphics is an ATI Radeon HD2400. Mac running OSX 10.5.8 Any ideas?

---

### Post by pastalavista on 2010-09-17
I'm just guessing because I don't use Apple products any more but it sounds to me like a BIOS issue. Look for any kind of anti-virus or other restrictions for allowable boot software/devices in BIOS. Also, have you tried a bootable USB flash drive? Also, why aren't you trying 10.04?

---

### Post by Amacha on 2010-09-17
From what I have read iMac uses EFI instead of BIOS- however plenty of people have Ubuntu dual booted with OSX 10.5.x. The EFI firmware has no updates for the 8,2 generation iMac and I can't see how to boot the cd and pass options through the EFI shell in rEFIt. I can rule out anti-virus in this case.

I'm keen on 9.04 to harmonize dependencies and libraries with another Ubuntu Jaunty install to keep programming simple. I'll try 10.04 to see if this is a specific version issue.

---

### Post by pastalavista on 2010-09-17
Right, BIOS is sort of emulated by rEFIt and can't boot from USB or something... this link might help. 
[http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/]("http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/")
good luck

---

### Post by Amacha on 2010-09-22
Thanks for the pointer- the issue seemed to be that the free partition was HFS+ formatted. I used boot camp to shrink the primary partition but indicated I wasn't "ready" to install windows- i guess it never progressed to a FAT or NTFS formatting step. Having spotted that rEFIt doesn't handle ext* formats well I wondered if having the "new" partition FAT formatted would help. I erased (quick formatted) the secondary partition as FAT32 using the mac Disk Utility tool and the **livecd works!** Which is odd as the CD hasn't changed a whit. I'll try and recreate the error by reformatting HFS+ and test just leaving freespace.

NB I had tried the 9.10 livecd prior to reformatting and the same black screen issue arose.

---

### Post by Amacha on 2010-09-22
Strange followup- reformatting mac OS (journaled) causes problem to reappear however turning the partition to freespace or FAT32 doesn't fix the problem. Using rEFIt to shut the system down, unplugging the machine, re-plugging and booting into cd through rEFIt worked. Or it could be a co-incidence and a function of the number of boot attempts.
[B]
final note- my experiments show only shutting the machine down and physically unplugging it has been the determining factor in getting livecd to work[/B]. This is somewhat consistent with [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677) under the additional issues section. The initial format of the partition is a furfy.

---

