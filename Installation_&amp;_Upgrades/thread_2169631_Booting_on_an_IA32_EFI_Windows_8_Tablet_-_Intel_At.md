---
title: "Booting on an IA32 EFI Windows 8 Tablet - Intel Atom Z2760 - NO LEGACY MODE"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by Wyatt_Ward on 2013-08-22
I did not decide to get this, but i am interested in knowing how i may boot linux on a Windows 8 Tablet with IA32 EFI, and NO LEGACY MODE.

The tablet is an Asus VivoTab tf810c.
Seven problems already:
1) UEFI
2) No legacy mode
3) Windows 8
4) No DVD Drive
5) Made by Asus
6) Tablet
7) 32 bit only Clover Trail Atom CPU

I can disable secureboot, but I can't find a 32 bit version of *any* distro with EFI support! The closest i came was a Debian wheezy test disc that froze after GRUB. I have no CD/DVD drive, but i have USB ports and an 8GB (not GiB) flash drive. I need to be able to find a 32bit way to boot both Windows 8 (not allowed to remove it, it's a work machine that I was given permission to put linux on) and Ubuntu or Linux Mint. This will have to be done via USB, due to it being a crappy tablet (again, i wanted a nice desktop PC).

It cannot be 64 bit, because 64 bit instructions are not in this processor (Intel Clover Trail. It WILL work with linux apparently, but not with powersaving features. Still, quite a nightmare, isn't it?)

I will do anything short of compiling the kernel to get this PoC to work like a PC is supposed to.

---

### Post by oldfred on 2013-08-23
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)

[h=3][/h] Don't ship 32-bit UEFI firmware on x86
    [http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

---

### Post by Wyatt_Ward on 2013-08-23
I was relatively certain these CPU's simply could not make use of the power management features under anything besides Windows 8. I have read both of these articles. Are you saying it is, as of now, impossible to do this? I have found that rEFInd has a 32-bit version.

Quoted from the first article:
"While Intel stated that Clover  Trail &#8220;cannot run Linux,&#8221; a better way to put it would have been to say  that users should not run Linux. "

I want to anyway.

The second is just begging people building the machines not to use 32-bit UEFI. I had no choice in the matter.


I had, again, no option to select a better one or to wait for intel ValleyView. This is a school device I was given permission to try to install linux on, and now I want to go through with it.

---

