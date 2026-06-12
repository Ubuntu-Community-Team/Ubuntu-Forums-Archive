---
title: "partman-auto-raid not using mount options"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by LoOoD on 2012-10-08
I'm testing out preseeding with raid but when the partitions are being mounted they are not obeying the options/noatime { noatime } as specified in the preseed.

Is this preseed config correct?

# raid1
d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb

d-i partman-auto/expert_recipe string \
    multiraid ::                      \
        1 1 1 free                    \
            $iflabel{ gpt } $gptonly{ } $primary{ } method{ biosgrub } . \
        200 200 200 ext3 \
            $gptonly{ } $primary{ } method{ raid } options/noatime{ noatime } raidid{ 1 } . \
        8192 8192 8192 swap \
            $gptonly{ } $primary{ } method{ raid } raidid{ 2 } . \
        10000 20000 1000000000 xfs \
            $gptonly{ } $primary{ } method{ raid } options/noatime{ noatime } raidid{ 3 }  .

d-i partman-auto-raid/recipe string \
    1 2 0 ext3 /boot raidid=1 . \
    1 2 0 swap - raidid=2 . \
    1 2 0 xfs / raidid=3 .

---

### Post by LoOoD on 2012-10-09
BTW this is with lucid that I cam seeing the problem with. I haven't tried precise yet.

---

