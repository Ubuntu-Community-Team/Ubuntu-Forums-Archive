---
title: "Ubuntu on Soft raid crashed, cannot repair"
date: 2017-12-06
forum: Installation &amp; Upgrades
---

### Post by lseg on 2017-12-06
Hi Guys,

I already spent several days on this. My linux crashed on me last week (file not found in GRUB), when I try to run in recovery mode I get the fact that some modules can not be loaded.

I now would like to run a repair using the Live CD, but It can not find my soft raid. I installed mdadm and detected the drives using "sudomdadm --assemble -scan", but when I start the installation it does not detect an operating system, it somehow can not detect it is on my soft raid.

I tried to help it by mounting them to /mnt/md0 (root directory on Raid 1) and to /mnt/md1 ( home directory on Raid5), but that doesnt work (I can read what is on it in nautilus on /mnt/md0 and 1). For some reason it does not recognize these "images " (not sure how to call it). I just would like to repair the broken linux...

Could you please give me another option to repair this?

Kind regards,

---

