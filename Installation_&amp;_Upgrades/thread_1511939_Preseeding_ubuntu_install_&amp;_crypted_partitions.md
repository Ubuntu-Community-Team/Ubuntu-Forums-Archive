---
title: "Preseeding ubuntu install &amp; crypted partitions"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by marcinpz on 2010-06-17
Hi,
1. I need help with preeseding file in Ubuntu Lucid Alternative. I have my own installation preseed file, but I don't know how to setup crypted partitions there. I need half automatic installation process. Now I have a partman-auto section like this:
```

d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              60 65 70 ext4                                  \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              900 4000 20000 ext4                       \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
                      options/noatime{ noatime }              \
              .                                               \
              64 512 300% linux-swap                          \
                      method{ swap } format{ }                \
   

```and I want my root partition to be encrypted (but not LVM) with password (given by user). And a swap partition to be encrypted with random password. I would like to give user option to agree partition setup, but automaticaly create this setup.

2. Is it possible in above partman recipe to auto create some partition only when there is enough free space??

Thanks!

---

