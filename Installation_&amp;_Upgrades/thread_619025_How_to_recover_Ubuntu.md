---
title: "How to recover Ubuntu"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by nirmal.santhosh on 2007-11-21
Hi all,

                  I am having dual boot Windows xp and Ubuntu.Unfortunately my xp get corrupted and i installed Xp from boot cd and i last My Ubuntu in booting screen but its still there in the partition . How to recover my Ubuntu without reinstalling it. Please Help in this. Advance thanx.....:KS

---

### Post by banewman on 2007-11-21
You can reinstall grub using your live(install) ubuntu cd.
Boot your comp from the live cd.
Open a terminal and type -
sudo grub
then type -
find /boot/grub/stage1
take a note of where grub is found - e.g. (hd0,2)
then type -
root (hd0,2) - where 2 is the number where grub was found
then type -
setup (hd0)
then type -
quit
and close the live cd and reboot
That should reinstall grub and get you back to dual booting.
It is important that you type the address from "find /boot/grub" properly when you type the "root" line. :)

---

### Post by Buickman on 2007-11-22
Just wanted to say thanks for posting that. I had a problem last night with grub. I'd boot up, and the screen just said GRUB on the top, and that was it. Your little procedure there fixed it.

Thanks again.

---

