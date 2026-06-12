---
title: "Disabling IRQ #9 - Old Laptop Issues"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by Corey_Eacret on 2014-09-03
So I have had Linux Mint on my laptop for a while, and it never ran fast (this is an old hand-me-down Sony Vaio with 1gb ram, and an Intel Pentium M cpu), so I decided to try out Xubuntu as an alternative. Sadly the full DVD wouldn't work, as the disc drive in this computer is wonky from something my sister had done to it back when it was hers. So I used the minimal install CD, as I have a good network and figured that would work well. It did, and the install went fine as far as I could tell. But I cannot get the damn thing to start. Each time I start the computer, it goes to GRUB, and then I pick Ubuntu, and then I get the "Disabling IRQ #9" message, and it just sits there.

I found the help article, so I added acpi=off to the end of the boot line, and the damn thing finally started. But I did get the [COLOR=#333333][FONT=Ubuntu]"irqXX: nobody cared . . ." error, and was curious if anybody would have any idea what might have caused this, and how I might go about diagnosing the problem. [/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-09-04
I have no first hand experience with this, but found

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

