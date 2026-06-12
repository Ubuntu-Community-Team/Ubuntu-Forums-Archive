---
title: "Sudden Booting problems"
date: 2021-06-12
forum: Installation &amp; Upgrades
---

### Post by aban7 on 2021-06-12
Hi all,

I enjoy my overall experience of this distro once its working but when its not it can be quite frustrating. this one is probably my fault.
I came back from my vacation of a week and turned my computer on. It went straight to the screen where is left off ( i didnt close off my Computer properly, i suspended it and didn't turn it off, i don't know if this has anything to do with my problem)
When i restarted the computer because it was acting strangly (i did not change anything) i came upon a so called Clean files error. (described here: [https://askubuntu.com/questions/882385/dev-sda1-clean-this-message-appears-after-i-startup-my-laptop-then-it-w](https://askubuntu.com/questions/882385/dev-sda1-clean-this-message-appears-after-i-startup-my-laptop-then-it-w) )
I tried fixing it but I can't enter the grub setting or such or do any maintaince from within it just freezes up. I tried using a boot-repair repository when running ubuntu on the same desktop from USB. This couldn't resolve my problem and gave the following output: [https://paste.ubuntu.com/p/37MPnDSryw/](https://paste.ubuntu.com/p/37MPnDSryw/). Any help would be much appreciated as my notes from school are on this OS and i have a test in 3 days, Goodbye :)

---

### Post by mikewhatever on 2021-06-12
What you call "a so called Clean files error" isn't an error at all. It says the partition is clean, nothing to see here. The "booting problem" might be related to /dev/sdb, which seems to have an ext4 file system, but no partition.

---

### Post by grahammechanical on 2021-06-12
First, the so-called clean files message is not an error. It is the result of a system file check of the partition that you are loading Linux from. What did you do to try to fix it? Apart for the clean files message did the OS load to a working desktop? If it did then what was the problem?

Do you get a Grub boot menu? If Ubuntu is the only OS on the machine then we will not see the Grub boot menu. But we can call it up. Your machine has a UEFI motherboard. As the machine starts to load and do its Power On Self-Test (POST) press the Escape (ESC) key. Perhaps several times.

If that brings up the Grub boot menu select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. If that brings up the recovery menu select Resume (normal boot). It may load to a desktop with a low resolution video mode. If that works get access to your files and back them up. Even making hand written copies if necessary.

After doing that open Software & Updates>Additional Drivers tab and either de-activate or activate (whichever the case may be) the proprietary video driver and reboot.

Regards

---

### Post by aban7 on 2021-06-13
I love you with all my heart, i got into my system following your steps, my pc still has problems i guess but i can work on the fix now ty.

---

### Post by grahammechanical on 2021-06-13
That recovery menu is very useful. If the desktop is not working well we can use recovery mode (Network - Root shell) to update/upgrade and run other commands that might fix things. I have made use of its features a few times.

Glad to help - Regards

---

