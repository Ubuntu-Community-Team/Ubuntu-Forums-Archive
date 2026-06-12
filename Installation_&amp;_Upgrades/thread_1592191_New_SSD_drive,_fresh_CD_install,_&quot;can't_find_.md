---
title: "New SSD drive, fresh CD install, &quot;can't find active filesystem&quot;"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by jirish on 2010-10-10
Hi All,

Have just brought a new 60GB SSD drive:

[https://www.aria.co.uk/Products/Components/Hard+Drives+%28SSD%29/G.SKILL+Phoenix+Pro+60GB+2.5%22+SATA-II+Solid+State+Hard+Drive+?productId=41155](https://www.aria.co.uk/Products/Components/Hard+Drives+%28SSD%29/G.SKILL+Phoenix+Pro+60GB+2.5%22+SATA-II+Solid+State+Hard+Drive+?productId=41155)

And have put it in my laptop:

[http://www.amazon.com/HP-Pavilion-DV4-1220US-14-1-Inch-Processor/dp/B001NPDKWG](http://www.amazon.com/HP-Pavilion-DV4-1220US-14-1-Inch-Processor/dp/B001NPDKWG)

But when I try and install Ubuntu 10.04 AMD64, it fails before i even get to any options, and just says something about not being able to find an active filesystem (that's not the exact message, but thought I'd see if anyone knew what to do before swapping hard drives again)

Any ideas?

---

### Post by jirish on 2010-10-10
Also, the hard disk test in the BIOS comes back as all OK.

Does this sound like it might be a broken drive?

---

### Post by dino99 on 2010-10-10
format this ssd before installation, with partedmagic for example (boot on partedmagic to do it)

[http://partedmagic.com/](http://partedmagic.com/)

note: google around ssd+maverick, that can help

[http://ubuntuforums.org/showthread.php?t=1587384](http://ubuntuforums.org/showthread.php?t=1587384)

---

### Post by jirish on 2010-10-11
Good idea, and I really thought that had fixed it, but it appears the problem is far more annoying...

First time I booted into Pmagic and formatted I then booted from a Ubuntu CD and it got further than it had before, up to the first option of whether to install or boot ubuntu from the CD. Problem was the CD was the wrong version (had downloaded and tried several) so I put in the 10.10 amd64 beta one thinking it would work now, but it didn't! Got exactly the same error as before. 

Then when I tried the version I had just had some progress with again, I got the error on that one too!!! I then spent several hours repartitioning and formatting, occasionally it would let me get past the error, but never when I had the version I wanted in. Got the exact error now, which was:

"**Unable to find a medium containing a live file system**"

Then I'd given up and put my hard drive back in, but I'd left the CD in the tray and when it booted it had the same problem again, but this time on my original drive!?! So appears the problem is not with the ssd drive. Without the CD in, my old installation booted fine from the old hard drive, but the live CDs all gave a similar error to the other drive, comes at the same point but instead says something about being unable to mount file system.

I noticed my laptop had some metal spikes to check if the plastic covering the hard disk space was in place, and I had been testing without screwing it all back in, so put that back in but gave me same problem. The metal plate on the cover is a bit broken though, may not be closing the circuit properly. Does anyone know if something like that could cause trouble with install, but allow to boot from the hard drive without any trouble?

Any other ideas? This is getting really annoying :(

---

