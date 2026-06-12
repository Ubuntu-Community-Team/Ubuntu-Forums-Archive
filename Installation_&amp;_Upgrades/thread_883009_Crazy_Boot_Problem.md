---
title: "Crazy Boot Problem"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by requ1em3 on 2008-08-07
Okay, I have 2 SATA HDs, one with Vista on it, the other I installed Ubuntu on a while ago. I wanted to get rid of Ubuntu so in the Windows disk manager I formatted that drive to NTFS and in "my computer" it was recognized and i put some files on it. When I rebooted next I get the "Grub 17" error, and I can't boot into either. When the 2nd drive is disconnected I can boot just fine. I've tried fixboot and fixmbr, any other suggestions?

---

### Post by Herman on 2008-08-07
:) Yes, try checking the [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in your PC's BIOS.
It could be that your BIOS is booting the MBR of the other hard disk instead of the one with Windows boot loader in it.
Another way to do the same thing would be to unplug your SATA cables and plug them back into the opposite SATA ports on your motherboard. (Switch them around so number 1 is number 2 and vice-versa).
For most people, switching the hard disk priority in the BIOS is easier.

---

