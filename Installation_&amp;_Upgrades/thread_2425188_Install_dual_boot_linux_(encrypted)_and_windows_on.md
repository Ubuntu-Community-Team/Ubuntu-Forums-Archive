---
title: "Install dual boot linux (encrypted) and windows on one usb memory?"
date: 2019-08-21
forum: Installation &amp; Upgrades
---

### Post by sean-1985 on 2019-08-21
Hi, this is a personal project: I am building dual boot linux (encrypted) and windows on a single usb memory stick, in order to have kind of a personal OS-to-go.
There are some limitations:
1. I prefer windows boot to be in charge instead of grub, or else windows updates frequently fails.
2. Both OS have to be encrypted in case the memory stick is lost.

The problem is: where to install the grub for linux? it can not be in the disk mbr because windows boot is there. it cannot be in the partition A where linux is, because A is encrypted. I am thinking of creating an extented partition B to include A, and let windows boot to link to B, but no luck with that. Any ideas?

---

### Post by TheFu on 2019-08-21
You are seeking much pain, Sean-san.

Buy 2 USB sticks. Much, much, much, easier.

---

### Post by yancek on 2019-08-22
Which version of windows are you planning to use?  The windows installer is designed to "NOT" install to a usb device so you will need to use some specific software such as woeusb which may or may not work.  Is this going to be a Legacy/CSM boot or UEFI?  If you manage to get windows on in EFI mode, it won't boot Ubuntu or any LInux, by design.

I'd tend to agree that if you want to try something like this using to usb sticks would be much easier.

---

### Post by C.S.Cameron on 2019-08-23
You can install Windows XP to USB stick, my experience is that it is too slow to use.
I have seen apps that say they will run later versions of Windows off USB but they are expensive and look like scams.

---

