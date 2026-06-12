---
title: "preseed partman-auto/expert_recipe doc?"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by hfturner on 2008-09-22
What I want to do is create two fixed sized partitions and then
have the third partition use whatever is left of the disk. This
is what I am doing:

d-i partman-auto/expert_recipe string                         \
      ccs-ws ::                                               \
              10000 10 10000 ext3                             \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
              .                                               \
              1000 200 200% linux-swap                        \
                      $primary{ }                             \
                      method{ swap } format{ }                \
              .                                               \
              100 20000 500000 ext3                           \
                      $primary{ }                             \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /scr }                      \
              .
d-i partman-auto/choose_recipe select ccs-ws

This "works" but only because the maximum sizes all fit within
the disk I am installing on. But it leaves about 20% of the 
disk unused. I have seen numerous examples of people using a
much larger number where I have 500000 and the implication is
that it will use as much as the disk has space for. At least
that has been my interpretation.  Doesn't work for me.
I get an error saying the partition goes outside the disk,
or some such. What I have not been able to find and would
really appreciate is a pointer to is some documentation about
how the "priority" field is really supposed to be used.
Clearly I am confused on this issue. Any help would be
greatly appreciated.

---

### Post by hfturner on 2008-09-24
For the record, if I take the "$primary{ }" out of the
partition that I want to take up the rest of the disk,
it works, albeit by making it in an extended partition.
I would prefer to keep it a primary partition but I can
live with it this way. But if anybody know how to make
this work with a primary partition, I'm still interested.

---

