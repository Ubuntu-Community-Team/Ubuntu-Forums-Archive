---
title: "Great Frustration"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by kubobbu on 2007-04-10
After allowing my old IBM Thinkpad with 192MB of Ram and a new 40GB hard drive to crank along for more than 24 hours, it appears that Kubuntu finally installed itself.

I can't be sure, because when I try to boot from the hard disk, I get a Grub 18 error, which means the BIOS can't find the loader and the kernal.

My drive is partitioned as follows according to QTParted (run from the CD):

      /dev/hda1     ext 3         Active    36,82GB   start  .03MB  end 36.82GB
    /dev/hda2     extended   458.97MB
  /dev/hda5      linux-swap   454.94

I have a feeling I'm missing a Boot partition, but I thought the installer was supposed to do that. Or if there is one, it apparently is not set low enough on the disk for the BIOS to find it.

Can anyone help with the proper partioning so I can get this thing to boot.  I'd really love to get this running.  By the way, had the same problem with an Xbuntu intall, which was faster but still led to the Grub 18 error.

Thanks...

---

### Post by zvacet on 2007-04-10
You give to much space to the root partition.That partition can be from 5-10.Make separate home partition.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Herman on 2007-04-12
A long time ago I had a 6.0 GB hard disk in an old PC chips 'Book PC', with 400Mhz celeron CPU and 128 MB ram. Eventually the hard disk failed due to bearing problems I think, judging from the small oil stain I saw near the center of the spindle.

I bought a 40.0 GB hard drive to replace it. I could easily partition the disk and install Ubuntu all right,  but no matter what I tried, I could not get an operating system to boot. Eventually it dawned on me that I was up against the infamous 33 GB hard disk drive limit. I wasted a lot of time and effort before I learned about that. In the end I had to give up and buy a 30.0 GB hard disk for the computer and use the 40.0 GB in an external USB case, which turns out to be a great asset.

I'm not sure if your problem could be the same as mine or not. Maybe you already know about that. You would probably be able to check by watching for your BIOS version info as your computer boots up. If you don't see it there, it will be in '[Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information")' in CMOS. You should be able to google that and / or your motherboard make and model to find out what hard disk size is supported in your PC.

Regards, Herman  :D

---

