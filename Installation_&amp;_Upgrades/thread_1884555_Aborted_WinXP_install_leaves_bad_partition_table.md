---
title: "Aborted WinXP install leaves bad partition table"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by lbriner on 2011-11-21
The bottom line of my problem is that when I run WinXP setup to put as a dual boot on my laptop, diskpart displays a single partition of 131Gb when in reality I have a 160Gb drive with Ubuntu occupying 100, unallocated space of 50 and the rest as two other linux mounts. If I run up Ubuntu, GParted displays the information correctly so I don't understand what Windows is displaying.
This is what I did.
1) Had installation of 11.10 occupying entire hard disk.
2) Booted from live CD to resize the main partition down to 100Gb to allow around 50 for Win XP.
3) Booted Windows XP 64 bit setup and the partitions were displayed correctly.
4) Installed and ran up Windows XP and would all have been fine except most of the 64 bit drivers were missing so decided to use 32 bit instead.
5) Ran Win XP 32 bit setup to hopefully spot the Windows partition and overwrite it but it displayed 131Gb as a single partition of [Unknown] which I think means ext3!
6) I assumed this was because I had not gone and re-run grub so I booted back into the live CD, ran the boot-repair program which brought back the grub menu and allowed me to boot Ubuntu again.
7) Ran win xp 32 bit setup again but it still shows incorrectly.
8) Re-checked in GParted in my Ubuntu install and this is definitely correct.

Can anyone please help?

---

### Post by lechien73 on 2011-11-21
What has probably happened is that you have a GUID partition table (GPT). Windows XP 64-bit recognises and can work with GPT, but 32-bit can't.

You can confirm this by downloading the boot info script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net) and posting the contents of the RESULTS.TXT file here.

Here's more info from [Microsoft's website]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/guid_partition_table.mspx?mfr=true"), but I'm almost 100% sure that's the problem.

---

### Post by lbriner on 2011-11-21
Spot on. Thanks for that. I will now reset the MBR with the correct partition information from GParted.

---

### Post by lechien73 on 2011-11-21
Great, if you get chance could you use the **Thread Tools** menu above and mark this as [SOLVED]?

Thanks

---

