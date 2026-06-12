---
title: "Ubuntu not opening. Emergency mode"
date: 2024-08-16
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2024-08-16
I have dual install Windows 10 Ubuntu 22.04 on a HP Probook 6560b.
For a while Chrome had refused to open and I was using chromium which is fine but do not allow me to sync my bookmarrks and passwords so I decided to give another go at trying to get it going.
I rooted around the forums and tried a few things (can't remember what now) I then decided to remove chrome and reinstall and one of those steps included using the command auto remove. I also removed the citrix ica using the same. after this chromium refused to open too. so I rebooted the computer and ran into the problem of Ubuntu not booting.
I got to the grub menu, but clicking to either ubuntu or safe mode got me nowhere. the windows side open though so following more online advice I created a USB boot with Ubuntu 24.04 and tried to boot from there.
Initially my system didn't find the usb. so did more reading and started mucking around in grub tried ```
grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot
```
from [Here]("https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux") But could not find which numbers to put after vmlinuz for my distro and tab wasn't doing anything so stopped in the middle of it.
Exit rebooted and miracle my usb was detected... so I ran boot repair
[Pre repair]("https://paste.ubuntu.com/p/KhGjvf5gZh/") report, reinstalled grub following the instructions, [Post repair report]("https://paste.ubuntu.com/p/K4mMBpmyxk/") rebooted and still got to the emergency screen again and Ubuntu not booting.
Also the report seem to find 2  partitions with windows, I was only aware of one....
I'm currently copying my home folder to and external hard drive just in case, 
SO...

Question 1 I had done some backup of my system (none too recently) via the Ubuntu backup utility, is there anyway I can use this from my USB boot to go back to a time when my system wasn't broken?

Q 2 Should I just cut my losses and reinstall Ubuntu? and if so better to go back to 22 or jump to 24? 

Q3 Should I do something about my partitions given the comment about Sda5 being far away from beginning, but has been there several years now and that have never been an issue...

Any help very welcome

:confused::confused:

---

