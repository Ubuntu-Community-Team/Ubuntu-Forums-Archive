---
title: "d-i preseed &amp; lvm"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by rattking on 2012-04-09
Hi all I am trying to automate installation for many boxen using pxe boot and a preseed.
If I go by the predefined partitioning recipes it works. but I need more control over the filesystem layout and lvm naming conventions.
With this expert recipe d-i errors out with "No root file system is defined" and I cant figure out why.
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-auto-lvm/new_vg_name string dom0
d-i partman-auto/expert_recipe string                   \
        dom0 ::                                         \
                256 256 256 ext2                        \
                      $primary{ } $bootable{ }          \
                       method{ format } format{ }       \
                       use_filesystem{ } filesystem{ ext2 }    \
                       device{ /dev/sda }               \
                       mountpoint{ /boot } .            \
                100 1000 1000000000 xfs                 \
                       $defaultignore{ }                \
                       $primary{ }                      \
                       method{ lvm }                    \
#                      device{ /dev/sda }               \
                      vg_name{ dom0 } .                 \
                500 10000 1000000000 xfs                \
                      $lvmok{ }                         \
                       in_vg{ dom0 }                    \
                       lv_name{ root }                  \
                       method{ format }                 \
#                       device{ /dev/sda }              \
                       format{ }                        \
                       use-filesystem{ }                \
                       filesystem{ xfs }                \
                      mountpoint{ / } .                 \

lvdisplay shows /dev/sda2 is in vg dom0
pvdisplay shows /dev/dom0/root is created and the right size.

I would also like /boot to be on lvm as well but I cant even get this working.
I have tried various things and no expert recipes involving lvm have worked.
any help would be great appreciated as I am stuck.
TIA.

---

