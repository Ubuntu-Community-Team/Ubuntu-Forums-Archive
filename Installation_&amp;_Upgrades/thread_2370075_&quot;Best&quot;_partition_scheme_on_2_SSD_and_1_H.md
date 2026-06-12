---
title: "&quot;Best&quot; partition scheme on 2 SSD and 1 HDD?"
date: 2017-08-30
forum: Installation &amp; Upgrades
---

### Post by lebawurscht on 2017-08-30
Hello,

i would like to install Ubuntu on 2 SSD an 1 HDD (128GB SSD, 1TB SSD, 1TB HDD) [COLOR=#000000]and I'm trying to figure out the "best" partitioning scheme for that.

Based on my knowledge I would put the big SSD on /, HDD on /home and small SSD swap.

[/COLOR][COLOR=#000000]Thanks for your advice.[/COLOR]

---

### Post by death-pro on 2017-08-30
if you do swap partition on SSD, you will decrease the life and performance of SSD. Because when swap partition is using, the system continuously write and delete data from disk. As you know SSDs have write limits. So i suggest you to do swap partition on HDD.

For instance my system has 2 OS, 2 Disk.[ATTACH=CONFIG]276546[/ATTACH][ATTACH=CONFIG]276547[/ATTACH]

---

### Post by sp40140 on 2017-08-30
128 GB ssd for swap is way overkill. In fact I suggest you install Ubuntu on 128GB ssd. Actually 128 GB is overkill for Ubunutu install as well.
once you install ubuntu on 128 GB, You can leave both 1TB hdd as data drives and mount them on /media. That way you can swap them out without any access / privilege issues. It would be lot flexible set-up as it will allow you take them out and put it in different system or if you have dual boot, windows can access without any workarounds. 
Latest Ubuntu doesn't even ask for / create partition for swap. it just creates a 2GB swap file.

---

### Post by Impavidus on 2017-08-30
No way you need 128GB swap. If you want to hibernate, make swap a bit larger than your ram. Else, about 2GB should be sufficient. Some people don't use swap at all. It's so slow that you don't want to use it.

1TB for / is overkill too. Something like 20GB is fine, but you could use your entire 128GB SSD. The only sensible way to use a 1TB drive is to store your media collection.

---

### Post by oldfred on 2017-08-30
My first SSD was 64GB and I had two / (root) partitions on it.
My current 128GB has 3 installs & another 30GB unallocated. They say to leave a few GB unused with SSD so newer SSD can manage use. I have well exceeded that.

I do like to have an install on every larger drive, even if in a smaller / (root) partition of 15GB, just for emergency boot.

With 17.04 and latter, you do not automatically get a swap partition but it uses a swap file.
       Starting from 17.04 Zesty Zapus release, instead of creating swap partitions, swapfiles will be used by default for non-lvm based installations.
no more than 5% of free disk space or 2GiB, whichever is lower. 

Because I have multiple installs, I keep /home inside / (root) but link all data from large data partition into /home (into most installs), so it looks like standard configuration, but data actually is on HDD in another partition. My /home then is mostly the hidden user configuration files & is very small.

I typically have latest LTS installed but then when new LTS comes out add another / partition. Then I can still boot older install. I will probably overwrite my 14.04 with 18.04, but may just add another 25 or 30GB.

Is system UEFI or BIOS? How much RAM?
If over 4GB of RAM you may not need much swap, or 2GB. And just do not hibernate, it boots fast anyway.
Unless BIOS system & installing Windows best to use gpt partitioning. You can use gpt with BIOS or UEFI with Ubuntu and later can easily change if you want. If drive is MBR much more difficult to convert to gpt.

---

