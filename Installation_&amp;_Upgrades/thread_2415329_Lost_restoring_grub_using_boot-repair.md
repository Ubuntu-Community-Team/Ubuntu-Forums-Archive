---
title: "Lost restoring grub using boot-repair"
date: 2019-03-24
forum: Installation &amp; Upgrades
---

### Post by jeffbarish on 2019-03-24
I have a computer on which a Lubuntu installation was working. Now I get "Reboot and select proper boot device" when I try to boot. I assume that the boot partition got corrupted, so I am trying to use boot-repair to fix the problem. When I click "Recommended repair" I get "Please use this software in a live session". I am using the software in a live session of Knoppix running on a flash drive. I also tried "Separate /boot/efi partition" under "GRUB location" in "Advanced options" because fstab says that is how it was mounted, but I get the same demand about using the software in a live session.

boot-info is here:

[http://paste.ubuntu.com/p/sbqP5XcpjH/]("http://paste.ubuntu.com/p/sbqP5XcpjH/")

I have pretty much no idea what I am doing, so any suggestions would be greatly appreciated.

---

### Post by oldfred on 2019-03-24
Usually better to use Ubuntu live installer to run Boot-Repair to repair Ubuntu.

It looks like you had swap on a flash drive and that entry now in fstab is invalid, not shown in list of UUIDs.
It used to be it would time out and then you could continue boot, but often now it just does not work with bad fstab entries.

With very large drives, I prefer to include an ESP (which may not be used by default) and a small install just for emergency boot.

---

### Post by Dennis N on 2019-03-24
If you have 14.04.5 as the boot repair output says, you are running out of support time on the shared Ubuntu packages. Lubuntu team support is already gone. Your big benefit is that Lubuntu 18.04 LTS is a lot better release than 14.04.x. A new install is the best bet.

---

