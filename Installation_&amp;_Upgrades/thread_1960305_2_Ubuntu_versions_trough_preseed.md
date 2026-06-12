---
title: "2 Ubuntu versions trough preseed"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by PedroGomes on 2012-04-17
Hi 

I currently have a small cluster where I use Foreman to manage and until now I'm happy with it. But a few days, my colleagues asked me if it would be possible to have 2 Linux distros in the same disk on different partitions so they can easily change share the machines. 

So, I started looking to preseed and partman and for the first installation I use the following setup. 

```


d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular

#boot, so1, so2 (not mounted), swap, and two data partitions (images and data)
d-i partman-auto/expert_recipe string                         \
  boot-root ::                                            \
    200 200 200 ext3                                \
      $primary{ } $bootable{ }                \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext3 }    \
      mountpoint{ /boot }                     \
      .                                               \
    10000 20000 11000 ext4                          \
      $primary{ }               \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ / }                         \
      .                                               \
    10000 20000 11000 ext4                    \
      $primary{ }                                         \
      use_filesystem{ } filesystem{ ext4 }    \
      .                                                           \
    1500 8000 200% linux-swap                       \
       $primary{ }                             \
      method{ swap } format{ }                \
      .                                               \
    8000 50000 9000 ext4                             \
      $primary{ }                             \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /images }                     \
      .                                               \
    30000 60000 -1 ext4                             \
      $primary{ }                       \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /data }                     \
      .                                               \
d-i partman-md/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true


```And for grub 

```

d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
#install in sda1 aka /boot
d-i grub-installer/bootdev string (hd0,msdos1)

```Now the problem is in the second installation... I haven't found any examples of people trying to achieve this in partman or if it is even possible. 

[LIST]
[*]I tried to make partman use the option of using partition 3 from the menu but no success there (and I ended up with 2 swap partitions if I did it manually)
[*]I have tried to use the same partman schema but taking the format options and changing root to partition3. This I found just recreates the partitions and so1 is not able to mount them...
[*]I dunno if I can use the output of *debconf*-*get*-*selections* --*installer | grep partman, *but besides being unreadable, it seems hardcoded with partition ids and such.
[/LIST]

Is this possible? Is there another way? :confused:
Thanks in advance.

---

### Post by PedroGomes on 2012-04-17
Solved!
I was missing the  "*method{ keep }" *line. FFS there is 0 good references to learn how to fully use partman.
The boot partition was also a problem, and so in the end the solution was:

First installation: 

```

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular

d-i partman-auto/expert_recipe string                         \
    10000 20000 11000 ext4                          \
      $primary{ }      $bootable{ }             \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ / }                         \
      .                                               \
    10000 20000 11000 ext4                    \
      $primary{ }                                         \
      use_filesystem{ } filesystem{ ext4 }    \
      .                                                           \
    1500 8000 200% linux-swap                       \
       $primary{ }                             \
      method{ swap } format{ }                \
      .                                               \
    8000 50000 9000 ext4                             \
      $primary{ }                             \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /images }                     \
      .                                               \
    30000 60000 -1 ext4                             \
      $primary{ }                       \
      method{ format } format{ }              \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /data }                     \
      .                                               \
d-i partman-md/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

``````

d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
#install on /dev/sda
d-i grub-installer/bootdev string (hd0)

```
Second installation:

```

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular

d-i partman-auto/expert_recipe string                         \
  boot-root ::                                            \
    10000 20000 11000 ext4                          \
      $primary{ }               \
      use_filesystem{ } filesystem{ ext4 }    \
      .                                               \
    10000 20000 11000 ext4                    \
      $primary{ }                                         \
      method{ format } format{ }                 \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ / }                         \
      .                                                           \
    1500 8000 200% linux-swap                       \
       $primary{ }                             \
      method{ swap } format{ }                \
      .                                               \
    8000 50000 9000 ext4                             \
      $primary{ }                             \
      method{ keep }                        \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /images }                     \
      .                                               \
    30000 60000 -1 ext4                             \
      $primary{ }                       \
      method{ keep }                   \
      use_filesystem{ } filesystem{ ext4 }    \
      mountpoint{ /data }                     \
      .                                               \
d-i partman-md/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

``````

d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean false
d-i grub-installer/bootdev string (hd0)

```

---

