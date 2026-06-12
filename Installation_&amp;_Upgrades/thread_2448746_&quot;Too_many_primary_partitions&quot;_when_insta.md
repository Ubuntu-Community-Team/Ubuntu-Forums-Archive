---
title: "&quot;Too many primary partitions&quot; when installing with pre-seed - 18.04 desktop"
date: 2020-08-13
forum: Installation &amp; Upgrades
---

### Post by andreasdavour on 2020-08-13
Hi

I am trying to build a set of desktops with a pre-seed from an ISO image and it works fine until I try to be fancy and slicy up my disk. I get the message:
"Failed to partition the selected disk", and suggests that maybe I have too many (primary) partitions. I thought I was well under the limit. I can click through and it installs, but it will only create some of my partitions and lvm volumes. 

This is how my pre-seed recipe looks like:
```
ubiquity partman-auto/expert_recipe string                    \
      custom-lvm ::                                           \
              1000 1000 1000 ext4                             \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              1000 2000 100% linux-swap                       \
                      $lvmok{ } lv_name{ swap }               \
                      method{ swap } format{ }                \
              .                                               \
              6000 10000 60000 ext4                           \
                      $lvmok{ } lv_name{ root }               \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
              .                                               \
              2000 2000 4000 ext4                             \
                      $lvmok{ } lv_name{ var }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /var }                      \
              .                                               \
              2000 2000 4000 ext4                             \
                      $lvmok{ } lv_name{ var_log }            \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /var/log }                  \
              .                                               \
              2000 2000 4000 ext4                             \
                      $lvmok{ } lv_name{ var_log }            \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /var/log/audit }            \
              .                                               \
              256 10000 1000000000 ext4                       \
                      $lvmok{ } lv_name{ home }               \
                      method{ format } format{ }              \
                      options/nodev{ nodev }                  \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /home }                     \
              .                                               \
              1024 1 1024 ext4 $lvmok{ }                      \
                      mountpoint{ /tmp }                      \
                      $lvmok{ } lv_name{ lv_tmp }             \
                      method{ format } format{ }              \
                      options/nodev{ nodev }                  \
                      options/nosuid{ nosuid }                \
                      options/noexec{ noexec }                \
                      use_filesystem{ } filesystem{ ext4 }    \
              .                                               \
```

And this is what I get:

```
$ lsblk 
NAME                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                    7:0    0  89,1M  1 loop /snap/core/8268
loop1                    7:1    0  54,7M  1 loop /snap/core18/1668
loop2                    7:2    0  44,9M  1 loop /snap/gtk-common-themes/1440
loop3                    7:3    0 160,2M  1 loop /snap/gnome-3-28-1804/116
loop4                    7:4    0   4,2M  1 loop /snap/gnome-calculator/544
loop5                    7:5    0  14,8M  1 loop /snap/gnome-characters/399
loop6                    7:6    0   956K  1 loop /snap/gnome-logs/81
loop7                    7:7    0   3,7M  1 loop /snap/gnome-system-monitor/127
sda                      8:0    0    20G  0 disk 
&#9500;&#9472;sda1                   8:1    0   953M  0 part /boot
&#9500;&#9472;sda2                   8:2    0     1K  0 part 
&#9492;&#9472;sda5                   8:5    0  19,1G  0 part 
  &#9500;&#9472;ubuntu--vg-swap    253:0    0   976M  0 lvm  [SWAP]
  &#9500;&#9472;ubuntu--vg-root    253:1    0   7,3G  0 lvm  /
  &#9500;&#9472;ubuntu--vg-var     253:2    0   1,9G  0 lvm  /var
  &#9492;&#9472;ubuntu--vg-var_log 253:3    0   1,9G  0 lvm  /var/log
sr0                     11:0    1  1024M  0 rom
```

From what I see, this is three partitions, one logical, and I only want to create additional logical volumes within that logical volume, which should not hit any partition limits, AFAIK.

Someone knows what I'm doing wrong, and even better, know how to to what I want?

Any help appreciated.

---

### Post by TheFu on 2020-08-13
Use GPT partition table, not MSDOS.  GPT supports at least 100 primary partitions and none of that extended-primary + logical partition crap.

---

### Post by andreasdavour on 2020-08-13
Hmm. Maybe I should. How do you force usage of GPT? Is it just adding "$gptonly{ }" on each mount point?

---

### Post by TheFu on 2020-08-13
> **andreasdavour said:**
> Hmm. Maybe I should. How do you force usage of GPT? Is it just adding "$gptonly{ }" on each mount point?

I just know that MBR/MSDOS partitions have limitation that are a hassle and that GPT doesn't. I've never done partman anything stuff. You have me thinking, if it is easy for partitioning, it would be worth doing.

[https://gist.github.com/robertstarmer/7332658](https://gist.github.com/robertstarmer/7332658) seems to have examples.

The pre-seed stuff seems overly complex for my needs.  Generally, I use all the available storage for LVM, then lvreduce "root" to 25G and lvcreate /home and swap and /var/lib/libvirt LVs to be mounted for extra stuff while leaving most of the VG unallocated.  On some systems, I don't bother with a separate /home/ at all - if there aren't any users, for admin stuff, I might need 50MB for scripts and notes.
Reducing the "root" LV early post install is important. Of course, having all the LVs setup as I like before any reboot would be very nice.

---

### Post by andreasdavour on 2020-08-13
Thanks. I will try it a bit and see if it might be what I wanted. 

I  am building a bunch of machines, so I have to do all the fancy disk  slicing automatically. It would have been nice if the GUI could save out  a partman recipe.

---

### Post by TheFu on 2020-08-13
> **andreasdavour said:**
> Thanks. I will try it a bit and see if it might be what I wanted. 

I  am building a bunch of machines, so I have to do all the fancy disk  slicing automatically. It would have been nice if the GUI could save out  a partman recipe.

Heck, until 20.04, I found setting up LVM during installation too much hassle. The 20.04 installer is 100x better - I almost cried. Perhaps in another 10 yrs, it will get to the level that CentOS had in 2012?

Canonical is all about easy defaults. They'd dumbed down so many things in the attempt to be more inviting for new users as to have gone way too far for some needs.  The "Do something else" in the desktop installers was a nice way to say - "Advanced Partitioning", but still too limited for many needs.  On a server install, I need much more control.

---

### Post by andreasdavour on 2020-08-13
Yeah, I wish I could use CentOS...

It looks like maybe gpt is the way to go, but just slap on $gptonly{ } did not work. :(

It might be that example only works on 20.04.

---

### Post by TheFu on 2020-08-13
Or it could be the 15 other commands at the top which setup the base for partitioning?
As you say, partman may not support it for auto-partitioning, but GPT has been supported since at least 2012, perhaps longer on the OS. I know there was a time when fdisk didn't support gpt.  

There is a tool that will convert MSDOS partitioning into GPT. Maybe after the partitions are setup, then running that would work?  You can keep legacy boot with GPT.  I've been doing that since at least 2012. Early BIOSes had an issue, but if you aren't doing HP stuff, I'd be surprised if it didn't work today.

---

### Post by andreasdavour on 2020-08-13
Yeah, I tried to include all the bits above setting it up. These things are subtle, and no docs at all... :(

---

### Post by andreasdavour on 2020-08-14
Anyone else have any hints, I'm all ears. I have tried to make this work with gpt, but it just fails.

---

