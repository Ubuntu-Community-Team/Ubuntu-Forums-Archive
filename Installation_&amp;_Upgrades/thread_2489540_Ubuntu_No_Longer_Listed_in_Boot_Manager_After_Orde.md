---
title: "Ubuntu No Longer Listed in Boot Manager After Order Change"
date: 2023-08-02
forum: Installation &amp; Upgrades
---

### Post by triggerhz on 2023-08-02
I broke it again :|


Following fully reinstalling, and choosing the third party option which lead me through applying a MOK key, it started defaulting to Ubuntu which I wanted to be Windows (sorry I feel naughty saying that in an Ubuntu forum). I went into the OS Boot Manager options within my UEFI set up, swapped them around and then POOF, Ubuntu option disappeared from my boot manager.


I can get back into it if I once again disable secure boot which makes me think something with the MOK is the issue, maybe unsigned or broken trust, or I could be totally barking up the wrong tree.

Tried disabling and reenabling validation but no effect on that. Also tried to apply the key by choosing Apply from disk option but I can't get into any folders deeper than those in Root (IE I can go into VAR but not the folders within there). Also tried reinstalling GRUB but it didn't help.

I assume I need to resign it or something to the effect there of, but I cannot find any way to do that?

I knew I should have left well enough alone and am completely blaming HP's not so cracking firmware rather than myself.

Once more all help appreciated!

---

### Post by tea for one on 2023-08-02
Even Microsoft web pages consider disabling Secure Boot.
> If you're running certain PC graphics cards, hardware, or operating systems such as Linux or previous version of Windows you may need to disable Secure Boot.
Extracted from [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11)

For PCs in a commercial environment, Secure Boot may be essential, but for home users, it has little value.

---

### Post by triggerhz on 2023-08-02
> **tea for one said:**
> Even Microsoft web pages consider disabling Secure Boot.

Extracted from [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11)

For PCs in a commercial environment, Secure Boot may be essential, but for home users, it has little value.

I guess I'll go down that route then if I carry on. Thanks for pointing that one out.

---

