---
title: "Complete install on RAID1 + LVM?"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by madverb on 2012-12-03
I was doing a bit of research to see if this was possible. I wanted to install the entirety of Ubuntu (desktop), including /boot and everything on LVM on top of software RAID1.
```
sda | sdb   sdc | sdd 
    |           |
  RAID1       RAID1   
          |
         LVM
  |   |   |     |
/boot / /swap /home
```
Hopefully the above shows what I want to do (ignoring lack of fs). I am currently unsure whether this is possible because of old documentation that seems to present conflicting information. I don't really care if it isn't possible but I am very interested.

---

### Post by darkod on 2012-12-04
It should be. Earlier you had to made /boot partition outside the LVM so it can work, but grub2 these days can handle LVM without separate /boot outside the LVM.

So, making two raid1 mdadm arrays, and then using them as physical devices for your LVM should be just fine.

You can also do a test in VBox first.

---

### Post by madverb on 2012-12-04
Excellent! Thanks for the response. I figured it was doable but there is so many conflicting opinions around the place. My understanding was that it is achievable with grub2 as it can see the RAID + LVM from the MBR.

---

