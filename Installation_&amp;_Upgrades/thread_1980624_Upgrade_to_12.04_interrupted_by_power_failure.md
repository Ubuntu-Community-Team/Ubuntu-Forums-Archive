---
title: "Upgrade to 12.04 interrupted by power failure"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Kahlan2178 on 2012-05-15
There was a very brief power outage as I was upgrading my computer to 12.04, and now I am getting the following message:

"disk boot failure insert system disk and press enter"

I inserted the 12.04 disk and pressed enter, but I'm still getting the same message. 

I have already changed the boot order to CD ROM, and I'm at a bit of a loss as to what to do next.  Has anyone ever experienced this problem before?

---

### Post by kc1di on 2012-05-15
is this a dual boot machine?

---

### Post by Kahlan2178 on 2012-05-15
"is this a dual boot machine?"

No, it's Ubuntu only.

---

### Post by kc1di on 2012-05-15
> **Kahlan2178 said:**
> "is this a dual boot machine?"

No, it's Ubuntu only.

And it does not pick up the cd at all?

---

### Post by jtarin on 2012-05-15
I thin the upgrade and power failure are only coincidental. Boot with your CD and try to recover all files you want to external medium. Was the power failure caused by lightning? Try another drive in that machine. I believe it's hardware failure.

---

### Post by Kahlan2178 on 2012-05-15
> **jtarin said:**
> I thin the upgrade and power failure are only coincidental. Boot with your CD and try to recover all files you want to external medium. Was the power failure caused by lightning? Try another drive in that machine. I believe it's hardware failure.

No, the power failure wasn't caused by lightning, I just live in a rural area, and it happens all of the time.  

I'd love to boot from the CD, but when I try, I get the same message.  Unfortunately, I haven't got another hard drive at the moment.  It was working just fine (plus, it's only a few moths old)  until the power outage.  Also, the computer is plugged into a surge protector, and the laptop that was plugged into the same surge protector is fine.

I seem to recall having a similar problem while upgrading, but that was several computers ago, and I don't remember how I resolved it.

---

### Post by jadtech on 2012-05-15
try USB boot

thing is I have had several upgrade failed attempts they would leave me unable to boot  to the desk top but never got a notice of bootdisk failure or insert system disk ..

---

### Post by Kahlan2178 on 2012-05-15
> **jadtech said:**
> try USB boot

thing is I have had several upgrade failed attempts they would leave me unable to boot  to the desk top but never got a notice of bootdisk failure or insert system disk ..

Thanks.  I'll try that.

---

### Post by jtarin on 2012-05-15
Observe your bios screen when it launches. Does it detect all your HDD and Optical drives? Change the boot order in the bios for the HDD to be first boot,F10 save. Then post results from these two observations.

---

### Post by jadtech on 2012-05-15
> **jtarin said:**
> Observe your bios screen when it launches. Does it detect all your HDD and Optical drives? Change the boot order in the bios for the HDD to be first boot,F10 save. Then post results from these two observations.

almost looks as if its not detecting any drive

---

### Post by jtarin on 2012-05-15
Try disconnecting the Optical drive and see if it detects.Yes? Good .....its your Optical drive. No? Try reconnecting the HD to another SATA plug on the motherboard. Results from this????

---

### Post by jadtech on 2012-05-15
> **jtarin said:**
> Try disconnecting the Optical drive and see if it detects.Yes? Good .....its your Optical drive. No? Try reconnecting the HD to another SATA plug on the motherboard. Results from this????

not my computer just observing from the detail here ..

---

### Post by Kahlan2178 on 2012-05-20
Sorry for the delay, guys.  My internet was out for almost 4 days, and it just came back on.  I was able to boot from an Ubuntu CD, but it is a much older version (9.10, I believe).  The newer one just wouldn't work.

I am not able to mount the hard drive from the disk, and it can't be found on the partition editor, but I can access some of it in the File Browser.  

Swapping wires inside the computer doesn't seem to have made any difference at all, unfortunately.  Any other ideas?  I mean other than chucking the hard drive out the window and getting a new one, that is?  

Thanks!

---

### Post by jtarin on 2012-05-20
Again.....does bios indicate any drives whatsoever?

---

### Post by Kahlan2178 on 2012-05-20
> **jtarin said:**
> Again.....does bios indicate any drives whatsoever?

No.

---

### Post by jtarin on 2012-05-20
Go into bios setup and check thouroughly. If bios doesn't detect any drives....HDD or optical....you have motherboard problems. Even with a surge detector this can happen sometime. Try your drives in another machine and see if they are detectable. This will narrow down the diagnostics to you motherboard. If they are not detectable in another machine it is almost a safe bet you have HDD problems.

---

