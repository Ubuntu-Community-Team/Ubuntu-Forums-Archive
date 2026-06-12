---
title: "unable to install 11.10,  &quot;no root file system is defined&quot;  [64 bit]"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by shivanayak@gmail.com on 2011-12-23
I was trying to feed the pressed to ubiquity while installing xubuntu 11.10 . 

Following is what I used in preseeding, and I used  debconf-set-selections to set the below preseed.

______________________________________________________________________________
ubiquity    localechooser/preferred-locale    select    en_US.UTF-8
ubiquity    debconf/language    string    en
ubiquity    localechooser/languagelist    select    en
ubiquity    debian-installer/language    string    en
ubiquity    partman-auto/init_automatically_partition    select    80custom__________custom
keyboard-configuration    keyboard-configuration/unsupported_options    boolean    false
ubiquity    partman/default_filesystem string ext4
ubiquity    partman-auto/choose_recipe select myboot-root
ubiquity    partman-auto/expert_recipe string             \
      myboot-root ::                                          \
              1 50 10240 ext4                                 \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                     \
              .                                               \
              64 512 8172 linux-swap                          \
                      method{ swap } format{ }                \
              .                                               \
              500 10000 30720 ext4                            \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /backup_fs }                \
              .                                               \
              500 10000 10000000 ext4                         \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /home }                     \
              .
ubiquity    partman/confirm_write_new_label boolean false
ubiquity    partman/choose_partition select finish
ubiquity    partman/confirm boolean true
ubiquity    partman-target/choose_method    select    25filesystem__________ext4

______________________________________________________________________________

And when I excute the ubiquity with --automatic option, it ends up with the error "[B]no root file system is defined".

Below is the information for debugging purpose. **Any help to solve this problem is appreciated. Thank you.**


[/B]______________________________________________________________________________
[diskinfo-beforepartition.txt]("http://ubuntuforums.org/attachment.php?attachmentid=209712&stc=1&d=1324888390")

---

### Post by shivanayak@gmail.com on 2011-12-23
Manually created the 4 partitions on the dev/sda so as to check if the ubiquity can make use of the existing partitions, but ubiquity fails with the same above ("no root file system is defined") error. 


Below is the system info after I created the partitions on the dev/sda . 

_____________________________________________________________________________________

[diskinfo-afterpartition.txt]("http://ubuntuforums.org/attachment.php?attachmentid=209711&stc=1&d=1324888230")

---

