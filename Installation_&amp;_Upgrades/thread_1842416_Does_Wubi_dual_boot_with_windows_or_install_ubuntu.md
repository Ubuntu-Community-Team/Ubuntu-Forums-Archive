---
title: "Does Wubi dual boot with windows or install ubuntu as a program"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by rorkimaru on 2011-09-11
I'm looking to dual boot my PC again. In the past I have done this through the live CD but I was looking at the Wubi installer and its description has me a bit puzzled. It claims you can install/uninstall like any other program but I was wondering does this mean that ubuntu is installed in such a way that you run it through windows or does it dual boot normally so you choose the OS when you boot the computer and boot into either windows or Ubuntu or do you run Ubuntu through windows?

If it dual boots it seems like the best option so I'd like to use it if it gives the results I'm looking for.

Thanks in advance for answering my noob question

---

### Post by nighthawk1 on 2011-09-11
It dual boots using the Windows bootloader, and you can easily remove it from your computer as if it was a windows program.

---

### Post by Mark Phelps on 2011-09-11
> **rorkimaru said:**
> If it dual boots it seems like the best option so I'd like to use it if it gives the results I'm looking for.

It actually boots using a version of GRUB written to run in Windows, known as GRUB4DOS.  It is installed like any other Windows program -- and removed the same way.

But, it doesn't actually run INSIDE Windows; it runs just like other Ubuntu installs.

---

