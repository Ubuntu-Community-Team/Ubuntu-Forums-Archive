---
title: "Broken booting files."
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by Bengal Cat on 2013-03-03
Hello,
I have Samsung N150 with Win7 and Ubuntu installed on it. Some time ago I installed Android x86 along with Win7. I wanted to delete Android but back then there was no information how to do it. Yesterday I installed Ubuntu. All of this loaded like this: first Android's grub with 2 options: Android or Win7, then I picked Win7 it loaded standard Windows system selection (Win7 or Ubuntu). Today I've found how to delete Android. It said just delete Android's system and grub folders. I thought that it will just load second part. But it broke. Now when i try to just boot eny system there's error 15. When I try to boot LiveCD: bootmgr is missing.
Please help me. I know that what I did was really dumb, but I'm new at using any other system than Windows.

---

### Post by darkod on 2013-03-03
Standard windows system selection with win7 and ubuntu? Are you using wubi installed inside windows or proper ubuntu on its own partition?

The windows bootloader can't boot ubuntu by default, so you can't have the standard windows bootloader showing ubuntu unless you have wubi, or you used something like EasyBCD.

It's important to know what you have and how you installed ubuntu.

---

### Post by Bengal Cat on 2013-03-03
Yes, I just used wubi, so I guess everything is on one partition.
EDIT:
I'm really sorry for wasting your time on fixing problems, caused by my lack of knowledge, but I really want to fix this and learn somthing important about linux systems.

---

### Post by darkod on 2013-03-03
First rule, never be lazy. If you are lazy don't even start installing any OS, especially one you haven't used before.

Wubi is only like virtual inside windows, it's not the same as proper ubuntu on its own linux partition. You need to fix the windows bootloader, this is not ubuntu or grub issue. With wubi you don't have grub on the MBR of the disk.

You might get better help on the windows forums how to fix the bootloader. Your win7 DVD or a rescue CD whould be able to help you do the Repair This Computer option.

---

### Post by Bengal Cat on 2013-03-03
Thanks, I was just sick of my very slow Windows and wanted to get new system really fast. Next time I'll install Ubuntu with LiveCD :)

---

