---
title: "Changing main hard drive"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2011-05-13
Hello all,
say I want to change hard drive, keeping everything, from a largish HD to a smaller SSD (but everything should fit).

There are so many backup solutions that I'm a bit lost, particularly regarding the partition resizing.
Say I connect both HD and SSD and boot with a LiveCD. I see /dev/sda1/2/5 and /dev/sdb. Now what?

Is it better/easier/faster to proceed:
- at the partition level (resize and dd)
- at the content level (format /dev/sdb* as ext4/swap/ext2 and then rsync the content)
- at the user level (install a clean Ubuntu and simply copy /home)

I usually do #1 if the disks are the same, #2 if it's not a system disk and #3 if I don't mind wasting time on a clean slate install, reconfiguring everything.

---

