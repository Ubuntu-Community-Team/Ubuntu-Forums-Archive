---
title: "Need help - dual boot"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by Ubuntu_User on 2005-04-14
Hi,

I would like to install Hoary Hedgehog but I'm a little hesitant since I don't want to destroy the Windows installation that resides on the same drive. The drive is divided into two ntfs partitions, one to boot Windows and one with documents, one ext3 partition where I have an old Debian install plus a Linux swap partition. 

I'm currently using Lilo as boot loader, but I really don't have a clue how it works - it was installed when I installed the Debian system. So, can I safely install Hoary and replace my Debian install with it? Should I change from Lilo to Grub or keep Lilo? If I choose to use Grub will it automagically remove all traces of Lilo and still enable me to boot Windows if I wish?

---

### Post by alainhenry on 2005-04-14
I installed windows XP and then Hoary a few days ago on a new PC.  Before, I had a triple boot Win98/Mandrake9.2/Warty.  From my experience, installing Hoary to replace Debian should be straightforward.  Repace GRUB with Lilo, or install  in expert mode to install lilo.  I would say both choices are OK.  The Hoary installation should detect Windows and allow you to double boot without a glitch (at least, that's what happened with my installation with GRUB).  
You know that Hoary can read but not write to NTFS partitions, I assume.  

Alain

---

