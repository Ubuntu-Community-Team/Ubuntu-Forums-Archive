---
title: "Grub problem after upgrade to 15.04"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by evandyk on 2015-08-02
I recently upgraded from 14.10 to 15.04. When I upgrade I always do a clean installation. I don't dual boot. I have always had a grub menu, though, offering me two ubuntu to boot. I don't recall what the two options were, but the default would boot 14.10. 

After the upgrade, I get a message saying something about limited BASH scripts, and a grub command prompt. If I just type "exit" at the prompt I proceed to the grub menu and can boot. 

Any thoughts on how to solve this problem?

Thanks in advance.

---

### Post by evandyk on 2015-08-02
Here is the actual text: 

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

---

### Post by oldfred on 2015-08-03
Grub may not have correctly installed so it looking in wrong place.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by evandyk on 2015-08-04
Thanks. I will try this out tonight.

---

