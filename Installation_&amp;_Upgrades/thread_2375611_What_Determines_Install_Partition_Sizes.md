---
title: "What Determines Install Partition Sizes"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2017-10-26
I have an 80 GB drive that I had installed Ubuntu 14.04 LTS on and was a spare for a while. I put it into a new build to test the hardware. Everything worked fine and I updated it to 16.04 LTS. After all the updates and removing unnecessary old components, there was 64.5 GB free. I decided to do a fresh reinstall with a 16.04 LTS DVD thinking I might get more space and have a cleaner install. However, after the install, it only has 40 GB free. It created a Filesystem Partition 1 of 46 GB and an Extended Partition 2 of 34 GB and a Swap Partition 5 of 34 GB. Does it determine the partition sizes based on memory? This PC has 32 GB RAM and the PC I originally installed 14.04 on had something like 4 GB RAM. So I'm thinking it created a larger Swap Partition based on the amount of memory?

---

### Post by oldfred on 2017-10-26
One of the reasons I prefer something else install option. You have control over sizes and locations of partitions.

Back when computers had 256MB, 512 MB or similar sizes of RAM swap was 2X RAM. 
When we got to 4GB of RAM, system almost never used swap and swap only had to be sizes close to size of RAM in GiB for hibernation. But new SSD boot so fast, you really do not need hibernation.
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 


Many with larger amounts of RAM have installed without swap at all.
I normally suggest 2GB.

Note that with 17.04 or later, swap file is used and not swap partition. But if swap partition is found, it will still use it.

---

### Post by HDTimeshifter on 2017-10-26
So I'm guessing with 32 GB RAM, I can delete the swap partition entirely? I'm pretty sure all my computers have at least 4 GB RAM, so probably want to check the swap partition sizes on all of them and delete or decrease the sizes to 2 GB.

I've been researching SSDs for awhile and read that hibernation should be turned off with them since that decreases their lifespan. I can not find any setting in 16.04 power configuration for hibernation. I only see a Suspend setting, which I'm hoping is a sleep mode that turns off all power except enough to preserve the contents in the RAM. Has hibernation been deprecated in Ubuntu and only Suspend (sleep) remains? I plan to replace the 9 year old motherboard and 8 GB RAM in my main computer with this newer motherboard/CPU/memory with the hope of also replacing the hard drives with an SSD in the very near future.

---

### Post by oldfred on 2017-10-26
If redoing drives that may go into newer UEFI computer, convert to gpt partitioning.
The only reason to keep MBR partitioning is if drive has Windows in BIOS boot mode.
Windows only boots in BIOS mode from MBR, and only in UEFI mode from gpt.
But Ubuntu can boot in BIOS mode or UEFI mode from gpt if you have correct supporting partitions.

I converted to gpt in about 2011 with BIOS only, then later started adding an ESP for future use if I wanted to move drive to a newer UEFI system.
Even most of my flash drives are now gpt, but they also are larger & many have a full install of Ubuntu.

SSD are fast enough that I see no advantage to hibernation. Have never used it, Windows uses it by default as it boots so slow it needs lots of help.

SSD life is comparable to HDD life, or not forever, but will last a long time if they do not fail early.
 SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)

---

