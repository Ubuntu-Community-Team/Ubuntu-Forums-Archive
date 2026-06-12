---
title: "motherboard died"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by elite0083 on 2012-11-15
I had to buy a new motherboard because my old one crapped out on me, the only problem is I couldn't get the exact same model and now I get an error when I try to run ubuntu saying run kernal first. I am currently running from a live disk, but was wondering if there is anything I can do except reinstall.

---

### Post by darkod on 2012-11-15
I think it should boot fine on a new board. Did you use maybe uefi boot on the old one or legacy bios boot?

Is the hdd recognized correctly in bios? Is the sata mode same, for example AHCI, like you had on the old board?

Do you get the grub2 boot menu as normal?

---

### Post by elite0083 on 2012-11-15
It won't boot like normal. I get grub 2 to come up and when I click ubuntu it gives me the error I mentioned. everything is the same I believe. the exact error is error: file not found error: run kernal first

---

### Post by darkod on 2012-11-15
From live mode can you open the partitions on the hdd and view the content?

Double check that the new board is not in UEFI boot mode. New boards have the uefi option but I don't know how they come by default.

I wouldn't think that a new board would confuse it so much that it doesn't boot, but I might be wrong.

---

### Post by elite0083 on 2012-11-15
From the live disk I can open the hdd and see everything that is in it. this motherboard doesn't have uefi it just has standard bios

---

### Post by darkod on 2012-11-15
If it stops with a grub rescue> prompt, try listing all disks/partitions with:
ls (small LS)

If that shows you the partitions you expect, like (hd0,msdos1),(hd0,msdos5), you can try booting if you know which one is the root partition, like #1, #5, etc.

---

### Post by elite0083 on 2012-11-15
it isn't a grub rescue error. it lists all of the os I have but when I select ubuntu it looks like this 

error: file not found.
error: you need to load kernel first.

---

### Post by darkod on 2012-11-15
Slipped my mind. In that case, at the grub menu hit 'c' for command prompt and see what the listing shows you.

It sounds like it doesn't see the disk/partition, but lets see if that is so and why.

---

### Post by elite0083 on 2012-11-15
i'll restart and try that and post right after

---

### Post by elite0083 on 2012-11-15
I booted in and did a c and from there I did an ls and it showed the hdd. So it sees them.... was it suppose to show them without me doing anything?

---

### Post by darkod on 2012-11-15
Can you post the results from live mode of:
sudo fdisk -l

and from the grub prompt from:
ls

---

### Post by elite0083 on 2012-11-21
I tried to run boot repair, but to no avail. I had grub coming up and  listing everything, but it still wasn't working right. I don't think  there was any proprietary stuff because I was using the generic drivers  and the on board video card. I tried to redownload 12.04, to see if  there was a repair feature, but there wasn't one. I finally gave up and  just reinstall it hoping that the new one would recognize the old one  and transfer stuff over like it had in the past, but it didn't and I  ended up having to start all the way over. thank you for the help  anyway.

---

