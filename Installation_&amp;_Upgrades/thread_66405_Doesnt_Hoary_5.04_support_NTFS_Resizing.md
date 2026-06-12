---
title: "Doesnt Hoary 5.04 support NTFS Resizing?"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by netneo on 2005-09-17
Hello guys

Doesnt Hoary Hedgehog 5.04 support NTFS Resizing?

Shouldnt i use that directly instead of a resizing tool like qt parted?

Will that make a difference?

i am a bit confused as to where to install GRUB for dual boot (Xp and Ubuntu)

Some sites say never install it where ur MBR is placed...

While others say u should do that

could u help me out?

GRUBs installation at the wrong place could make me lose my choice of starting with Windows?

---

### Post by netneo on 2005-09-17
Hey i was just trying a hard disk install of Hoary 5.04

But i guess i panicked when i got this message at the start of the installation

"No partitionable drives detected"!

What does this mean?

Shouldnt i be getting a screen saying i have an 80 gb hdd with partitions of 29.2 gb,29.2 gb and 15.9 gb?

I was planning to use resizing facility in Hoary 5.04 itself(without using qt parted) to resize my smallest partiition to produce free space to install Ubuntu.

By the way..i had  emptiedmy last partition completely i.e it doesnt have any data other than the windows xp swap file of around 800 mb

Can i install Hoary 5.04 directly on it without having to resize it?
I am asking this since i have lots of free space on my other 2 partitions and dont mind using the entire 15.9 gb for Ubuntu.

But why do i get no partitionable hard drives detected!

Same thing happened when i tried to use qt parted...it didnt show any hard disks with any volumes when i tried resizing thru that.

Please help me out.

Thank you

---

### Post by Lord Illidan on 2005-09-17
IS your hard disk an IDE or SATA hard disk?

---

### Post by netneo on 2005-09-17
It is a SATA Hard Disk

My system Specs are
Processor---->AMD Athlon A64 3000+ having Socket 939
Motherboard----->MSI RS480 with ATI x300 Onboard gfx
Ram------>512 Mb DDR
Hard Disk----->Samsung 80 Gb SATA

I had installed WinXp with NTFS and 3 partitions of sizes 29.2,29.2 and 15.9 gb respectively

---

### Post by Lord Illidan on 2005-09-17
The SATA drive is the root of your problems.

I checked it out on this thread : [http://www.ubuntuforums.org/showthread.php?t=5472](http://www.ubuntuforums.org/showthread.php?t=5472)

In short, it means that you either have to set SATA in the BIOS to  "Normal" for the Hoary distro.

Or else wait until October 13 when Breezy Badger comes out, as it should have SATA detection as standard.

---

### Post by netneo on 2005-09-17
Thanks for the link to the thread!
Yup..it seems a lot of people are facing the same problem as me with SATA drives

Since Breezy has a few days to come and Hoary 5.04 might work if i do the changes u suggested...

Could u guide me as to what i have to do..step-by-step

I am a newb and really dont know about how changes to BIOS settings might affect the rest of the system..

What u suggested...would that change anything about Xp that i want to run in a dual boot configuration as well?

Would GRUB get affected?

I would really appreciate if u could help me out soon

Thank you again!

---

