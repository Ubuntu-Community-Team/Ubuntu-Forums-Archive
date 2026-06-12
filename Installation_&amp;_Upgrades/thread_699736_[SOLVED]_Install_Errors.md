---
title: "[SOLVED] Install Errors"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by DrewMac on 2008-02-17
I am having problems installing Ubuntu 7.10 on a custom PC with these specs:

ECS 945GCT-M
Pentium 4 3.00GHz
1024MB DDR2 533 Single Channel RAM
LG Super Multi DVD Writer
320GB IDE Western Digital HDD
nVidia 8400GS 256MB 

_Installing From LiveCD_

When I use the LiveCD and select the option "Start or Install Ubuntu", I am given the error "Kernel panic - not syncing: Fatal exception in interrupt" 

On the LiveCD, if I select "Start Ubuntu in safe graphics mode", I am given this error: "Kernel panic - not syncing: Attempted to kill init!"

_Installing From Alternate CD_

When I select the option, "Install in text mode" I am given the following error: "Kernel panic - not syncing: Fatal exception in interrupt" 


Does anyone know the solution to these problems? Any help would be very greatly appreciated.

---

### Post by dstew on 2008-02-17
Something in the kernel is not working with your hardware. It could be any of your core hardware, from CPU to memory to video to disk drive. Memory is the usual culprit. Can you do a BIOS memory test? Do you have the correct memory for your motherboard?

---

### Post by DrewMac on 2008-02-17
*CPU:* Find it hard to be bad since it is brand new.

*Memory:* On the boot screen it allocates all of the memory and says it is OK, so would that mean the memory is fine?

*Video:* Can't be the card as I get the same errors if i use the onboard video.

*Hard Drive:* Also is brand new so I don't think it is bad.


EDIT: I inserted a Windows install disc (XP Home) to see what it would say and it says my BIOS is not fully ACPI compliant. Could this be the issue? If so, how can I go about fixing it?

---

### Post by dstew on 2008-02-17
Ah, that might be the answer. The Linux kernel uses ACPI during the boot process. Try the kernel parameter **acpi=off** which you enter by pressing F6 at the opening menu. Enter this parameter onto the end of the kernel line.

---

### Post by DrewMac on 2008-02-17
OK I added the **acpi=off** line. When I pressed Enter, it said the kernel was loading, please wait, but it just hung. So I reset the computer and I added the line again but it went back to the kernel panic error.


EDIT: Now if I enter the **acpi=off** line and press Enter, it will just hang on the next screen (plain black with gray dash flashing).


EDIT2: If I switch back to my standalone nVidia card though, I get the same kernel errors as in the first post in this thread.

---

### Post by dstew on 2008-02-18
Try to boot again, but remove** quiet nosplash** from the kernel line. Now you will see the kernel messages, and maybe get a clue as to where it is going astray. Another kernel parameter to try is **noapic nolapic** to turn off the advanced programmable interrupt controller. This also can cause hang-ups.

I don't know if you can use kernel parameters with the Alternate Install CD, but you might try that also.

When you get to the black screen (like the boot with apci=off) try ctrl-alt-F1 and see if you get a command line. If so, it might be the video display that is the problem.

---

### Post by DrewMac on 2008-02-18
_With nVidia Card_

Removing **quiet nosplash** - It moves too fast, I cant read much but it all leads to the same error. Right before the error it has a bunch on code (ff 00 00 00 ff 00 etc) and then it shows the EIP value. 

Adding **noapic nolapic** - I get "Kernel panic - not syncing: Fatal exception in interrupt"


_With Onboard Video_

Removing **quiet nosplash** - I see some messages about PnP BIOS. (Picture attached) However, if I try doing this again, I am landed with a kernel panic.

Adding **noapic nolapic** - I get "Kernel panic - not syncing: Fatal exception in interrupt"

Black screen with **acpi=off** - If I press Ctrl + Alt + F1, nothing happens.


*The Alternate CD gives the same errors.*

Note: I don't know if this helps, but I tried the Fedora 8 install CD and it also gives the same errors.

[ATTACH]60022[/ATTACH]


EDIT: I just ran a Memtest - it found 59 errors in the first test, then froze.

---

### Post by DrewMac on 2008-02-18
Bump. Am I right in assuming the memtest results mean the RAM is bad?

---

### Post by dstew on 2008-02-19
That is a reasonable assumption, since bad memory is one reason for kernel panic. Make sure you have the correct kind of memory installed, and that the DIMMs or SIMMs are seated properly. You really need to be sure that the memory speed is adequate for your motherboard.

---

### Post by DrewMac on 2008-02-19
I just realized that the memory in the system is 533Mhz but the socket speed is 667Mhz. Would this also be a cause for the errors?

---

### Post by dstew on 2008-02-19
Possibly. You have to look at the motherboard manual to see what is corrrect. Usually, the memory speed is much slower than the processor speed. The memory speed has to be matched to the *bus* speed, which in older computers is something like 100 MHz. Hence, "PC 100" memory for 100 MHz bus, PC 133 for 133 MHz bus etc. PC 133 will work in 100 MHz bus system, but PC 100 will not work in 133 MHz system. There is some "give" in the specs, so some PC 100 memory might be able to function in a 133 MHz bus environment, but give some errors. Also, I think the memory should all be the same speed in the same system.

EDIT: [Here]("http://www.oempcworld.com/support/Memory_Access_vs_CPU_Speed.htm") is a nice page that shows what I mean about bus speed.

---

### Post by DrewMac on 2008-02-19
Ok, well I just went back to the store and exchanged the ram stick for a new one and the new one works perfect. Thank you dstew for you generous help. I declare this thread solved.

---

