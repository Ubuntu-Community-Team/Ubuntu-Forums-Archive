---
title: "Error installing Ubuntu on Acer Aspire 5040"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by tidemann on 2006-08-31
I finally recieved my new Acer Aspire 5040 laptop! Although I got very frustrated when I inserted the Ubuntu CD, said goodbye to Windows, and booted from the CD-ROM.

The Ubuntu installation menu greeted me and I selected "Start or install Ubuntu." Then I was presented with this:
```

Uncompressing Linux ... Ok, booting the Kernel.
MP-BIOS Bug 8254: Timer not connected to IO-APIC
```

Then the screen went black, and nothing happend afterward. Is this an hardware error? I really hope not. I was looking forward to both the laptop and Ubuntu. If there is anything I can go other than returning the laptop I would really appreciate it.

Until then I'm stuck with Windows, which boots perfectly!

---

### Post by GMFTatsujin on 2006-09-07
I had the same issue.  When booting from the CD, you'll first be presented with a screen that allows you to specify the boot options before it loads the kernel.  It's the one you probably just hit ENTER to get past.

The function keys will give you help on the various options you can pass to the kernel while it boots.  You want to give it the

[INDENT]noapic[/INDENT]

option.  You can see the instructions how by pressing F2 or F3 ... one of those F-keys, anyway.

Lots of laptops use buggy interrupt controllers that confuse Linux.  It's a drag, but the solution is easy once you know what's happening. :)

---

### Post by tidemann on 2006-09-08
Many thanks! That solved my problem!! :)

---

### Post by Razor81 on 2006-10-02
For anyone else experiencing this problem, I have found a solution that works on my 5040 without disabling apic.  Using the enable_8254_timer option instead of the noapic option allows the computer to boot without disabling apic.

---

### Post by Sicnalbtif on 2008-03-10
Sorry to bump this thread back, but I have an aspire 5040 also, and am having trouble. It's the same problem, in fact, I just don't know *where* to do the noapic change...

---

### Post by G33 on 2008-03-10
I have the same error on my Aspire 2010.
All i do is hit the F2 key. How do you enable the 8254t timer?

---

### Post by Pumalite on 2008-03-10
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Sicnalbtif on 2008-03-10
> **Pumalite said:**
> [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Reading that, it sounds like I need linux already installed.

The screen I get has these options:

Start or Install Ubuntu
Start Ubuntu in safe graphics mode
Check CD for defects
Memory test
Boot from first hard disk

it also has F-keys options on the bottom, F1 getting to a help menu. What am I doing from here (or before here?)

---

### Post by Sicnalbtif on 2008-03-11
bump

---

