---
title: "New Ubuntu install, first boot, Grub&gt; Directory encrypted"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by gene14 on 2020-05-15
Just installed vers 20.04, found the following using a known good DVD:

1) Installer crashes if ZFS is selected. It gets to the screen asking for user name and crashes when one begins to type the computer name. tried several times.
      Then installed without any advanced option. No ZFS, no LVM. Removed DVD for reboot and ...

2) Grub:  "Directory encrypted. Entering recovery mode".
     Me:    "Wha-a-a-a ! I didn't select encryption ! What the devil is going on here !"

3) Tried again with ZFS but installed on sdb instead of sda. Same. 

4)Finally, the heck with it. Deleted all disk partitions and re-installed 18.04. Removed DVD, booted and got "file '/boot/grub/i386-pc/normal.mod' not found. Entering rescue mode."
   (The machine has an AMD 64 bit cpu, don't know why grub's looking for an i386 file)

So we're going to do some memory checks, but it was running 18.04 flawlessly this morning.


Any guesses what's happening ?

Thanks for any suggestions,

Gene

Update:  Install attempt on sdb failed as well. Note that this dvd was used to successfully install on another system WITH ZFS.

---

