---
title: "Dual booting on a Folio 13"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2012-07-04
Hello, I'm having difficulty setting up a brand new HP Folio 13 to dual-boot with Windows (I know, I know...). Using both GParted from an Ubuntu 12.04 live USB and Windows' disk utility, when shrinking the Windows partition Ubuntu sees the unused space as "unusable." 

Can anyone tell me why?

Thank you!

---

### Post by msammels on 2012-07-04
How big is the "unusable" space? Have you formatted it?

Generally, Ubuntu likes to have (I think its) 3 partitions.

---

### Post by Nixie Pixel on 2012-07-04
Ugh, apparently there are already 4 primary partitions and one extended. How does a brand new PC have these partitions already? There is only one recovery partition, one system partition, one data partition, and....?

---

### Post by Sabonmu on 2012-12-15
I'm trying to do the same thing.

My Folio 13 only has a 128 Gb SSD, and I was appalled at the space Microsoft was using. 

I resized the Win 7 main partition, made recovery DVDs and deleted the recovery disc and Installed Mint 13.

Normally, my Ubuntu/Mint dual boot installations go like a dream, but this didn't!

Mint recognised Win 7, but didn't add it to Grub. So I ended up just using Mint. 
Now I need Win 7 for an ancient USB CMDA net connection I have, and so I'm back with Win 7 via the factory clean image from the recovery DVDs. 
I hate it. Soo very distracting.

So now I'm looking at deleting the recovery partition, resizing Sys partition  and Installing Ubuntu or Mint in a 15Gb single partition, which is big enough.

But I'm concerned about getting Win 7 into Grub.

Anyway, regarding the Ubuntu/Mint install:

First, beware the Folio 13 is not Linux friendly! It's back lit screen gives problems, so you need to read up on that, there's plenty of advice, and it does work.

Then attach an external screen for the install, so you can see.

Let's see if anyone can advise from there?

---

### Post by oldfred on 2012-12-15
Best to see what is where.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

