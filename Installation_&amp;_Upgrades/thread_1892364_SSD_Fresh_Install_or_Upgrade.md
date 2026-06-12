---
title: "SSD Fresh Install or Upgrade"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by EienTatsu on 2011-12-07
I'm currently running ubuntu on my desktop with a root drive and a seperate home drive. I bought a 120 Gig ssd and am not sure how I should go about installing ubuntu on it. Moving it from the desktop or clean install. And if moving it how would I do that.

---

### Post by Basher101 on 2011-12-07
a clean install is advised. Also, make sure that NO SWAP is on the SSD. If you are indeed in the need of SWAP, place it onto a HDD.

regards

---

### Post by EienTatsu on 2011-12-07
Okay, how would you advise getting my data back from my old install. Any way to keep applications, settings or just start from scratch?

---

### Post by Basher101 on 2011-12-07
if you have your /home on a different partition you could keep all your files...otherwise just back up your data. 

Or start from scratch if it is not too much work to get it back the way it was..

---

### Post by EienTatsu on 2011-12-20
I just installed my OCZ agility 3 ssd and I opened up Gparted to partition it but the drive is not found any help?

---

### Post by dabl on 2011-12-20
Two suggestions.

1. Your motherboard model and BIOS are important to solve drive recognition issues, so please post those.

2. OCZ has a good user forum -- have you checked that?  There's a Linux section, or there was the last time I needed it.

---

### Post by EienTatsu on 2011-12-20
> **dabl said:**
> Two suggestions.

1. Your motherboard model and BIOS are important to solve drive recognition issues, so please post those.

2. OCZ has a good user forum -- have you checked that?  There's a Linux section, or there was the last time I needed it.

I have an asus P7p55d-e pro motherboard. I'm reading those forums right now. Just as a note the drive shows up in POST and in windows. The drive also doesn't show up under SATA drives in BIOS but does under Hard Drives as an IDE drive

---

### Post by darkod on 2011-12-20
> **EienTatsu said:**
> I have an asus P7p55d-e pro motherboard. I'm reading those forums right now. Just as a note the drive shows up in POST and in windows. The drive also doesn't show up under SATA drives in BIOS but does under Hard Drives as an IDE drive

Double check in bios you have SATA mode at AHCI, although it should work as IDE too. But it's a shame using SSD at IDE.

If the setting is at IDE maybe it confuses things. No way a SSD should appear as IDE.

PS. Try it connected to other sata ports on the mobo too.

---

### Post by EienTatsu on 2011-12-20
I tried AHCI to with no success I'll try connecting to other SATA ports.

---

### Post by EienTatsu on 2011-12-20
I had to set the SATA III ports to AHCI in the advanced section of my BIOS, thanks for the help.

---

