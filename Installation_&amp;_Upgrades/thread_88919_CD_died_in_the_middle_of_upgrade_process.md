---
title: "CD died in the middle of upgrade process"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by qwert231 on 2005-11-11
I followed the directions to go into Package Manager w/ the new CD and Mark All Upgrades. I did the Smart option. In the middle of the process, my CD died. Nothing would work. I tried rebooting, and get:
Kernel Panic - Not Syncing: Attempted to kill init!

What's up with this? I have my whole website on that system? What can I do? I burnt a copy of the 5.10 install CD

---

### Post by Kyral on 2005-11-11
So...you had it installed, and the CD was in...

Oy....First thing you should do upon installing is disable the CD Repo. That way you'd only be able to update from the net.

Try rebooting into Recovery Mode and finishing the update from the terminal *Instructions on how to work Apt in the link below*

---

### Post by qwert231 on 2005-11-11
K, just to clarify, I had 5.04 installed. Then today made the 5.10 disk.
I stuck the disk in, and it said "Want to upgrade? Run the Package Manager" and thus Synaptic was started, and I tried to upgrade according to this: [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

How can I reboot into Recovery Mode?

---

### Post by Kyral on 2005-11-11
Whoa, never saw that method. Usually upgrading from Hoary to Breezy is done via a dist-upgrade WITHOUT the CD...

Anyway to get to Recovery mode, hit ESC when it says "GRUB Loading press ESC to access Menu" and then the GRUB menu should appear and allow you to choose Recovery Mode

---

### Post by qwert231 on 2005-11-11
Nope, still don't work. I get:
exec: 428 chroot: not found
Kernel Panic - Not Syncing: Attempted to kill init!

As I said, my website is on there. Any way I could save this? Maybe install again without wiping the drive?

---

### Post by qwert231 on 2005-11-12
Help, still no resolution. Help?! Please? Any ideas on what I can do?

---

