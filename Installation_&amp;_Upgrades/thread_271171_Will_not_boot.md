---
title: "Will not boot"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by mcsix on 2006-10-04
I am trying to dual boot XP and ubuntu. I have three hard drives
ide   80g NTFS storage drive
SATA1 120g installed ubuntu
SATA2 320g C: drive with XP

The livecd works fine and it installs fine. 
After I install ubuntu, the computer reboots and boots directly into XP, grub never comes up. If I change bios to boot SATA1 first, nothing happens, just a blank screen. It never appears to even try and access the hard drive. 
I also tried another boot manager through XP. The boot screen comes up that allows me to choose either the XP drive or the ubuntu drive. I can boot to XP fine but just a blank black screen if I choose ubuntu. 

What am I missing? Do I need install on the ide or SATA2 instead?

I have done some searching through the forum to see if there was  already a solution but I did not find one. If I missed it I apologize. 
Thanks.
Brian

---

### Post by Kateikyoushi on 2006-10-04
There are a few ways to solve it.

Removing all other drives while installing will definitely solve it, then you can add the other drives and configure grub to be able to boot windows.

You could also add ubuntu to windows bootloader, but not recommended.
[Link]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why")

---

### Post by mcsix on 2006-10-04
Thank you so much. I will give that a try tonight when I get a chance.

---

