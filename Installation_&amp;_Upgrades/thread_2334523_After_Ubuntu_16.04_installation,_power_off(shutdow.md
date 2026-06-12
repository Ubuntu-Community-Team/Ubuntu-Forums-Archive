---
title: "After Ubuntu 16.04 installation, power off(shutdown process) neverending"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by romanux2 on 2016-08-20
Good day to everybody. Im new to Linux, after 20 years on Windows. Please for help. Ive installed Ubuntu 16.04 on my Lenovo Z570 laptop. I changed Windows 7. Everything working fine, just when shutting down, it cannot Power off. It is still running with Ubuntu logo. Ive seen many advices with grub or usb 3.0 legacy in Bios, but nothing worked for me. Please, can u help? I want to stay with Ubuntu, but this seems very big issue for me. Any help appreciated:popcorn:

---

### Post by sudodus on 2016-08-20
Welcome to the Ubuntu Forums :-)

There are problems with some hardware, and there are some work-arounds.

When you have 'shut down' and it continues with the Ubuntu logo (I guess you mean the text 'Ubuntu', and five dots), you can use a soft shutdown or soft reboot according to the following link. It can be used in many situations, when normal commands do not work, and it is much better than a hard poweroff (pressing the power button for several seconds).

[Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

SysRq is often, but not always, on the PrintScreen key - so press ***alt + PrintScreen***

Check which hotkey combination, that invokes SysRq in your computer.

[SIZE=3]***SysRq***[/SIZE], keep the keys pressed down all the time, and at the same time slowly maybe one key per second, one after another press [SIZE=3]***r e i s u o***[/SIZE] to shut down or

[SIZE=3]***SysRq***[/SIZE], keep the keys pressed down all the time, and at the same time slowly maybe one key per second, one after another press [SIZE=3]***r e i s u b***[/SIZE] to reboot.

Edit: Later on, an update might solve the problem, or someone might have a solution for you, but you may get along with this work-around for a while. You can keep the key combinations on a paper (until you know it by heart).

---

### Post by romanux2 on 2016-08-30
Hello sudocus. 

Thanx for your help. Unfortunatelly Reboot works, just Shutdown doesnt work with r e i s u o. Probably is it the same poweroff problem. I hope somebody will solve it in some Ubuntu update, cause  I like it and dont want to go back to Windows.

Romanux2

---

### Post by sudodus on 2016-08-30
After performing ***SysRq r e i s u o*** the computer is [probably] 'halted' but the power is not turned off, and it should be possible to ***turn off the computer with a short press on the power button***. Halted means that data in the memory is flushed to the file systems and the partitions are unmounted. So it is safe to turn it off with a short press on the power button.

This is much better than the case, when you need a long press, around 4 seconds, 'hard poweroff'.

---

