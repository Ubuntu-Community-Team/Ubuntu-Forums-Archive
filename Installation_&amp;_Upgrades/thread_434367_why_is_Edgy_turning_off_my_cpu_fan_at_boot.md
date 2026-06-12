---
title: "why is Edgy turning off my cpu fan at boot?"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by scradock on 2007-05-05
I have been puzzling over why it is so difficult to install and run Ubuntu Edgy on my wife's desktop machine. It's five years old, eMachines T1840. I have now identified one major problem which is probably the root cause of all the weird stuff I've been seeing.

In the first couple of seconds of the boot process (kernel 2.6.17-11-generic) the ACPI module reports "Transitioning device [FAN1] to D0" (ie the OFF state). Then there is a confirmation message: "ACPI: Fan [FAN1] (off)"

I had noticed the abrupt stopping of the sound of this fan several times, but now I have kernel log and dmesg and syslog confirmation - Edgy is turning it off deliberately. It never comes back on. After some time (10 ->50 minutes) the kernel issues a message "ACPI: Critical trip point" followed by "Critical temperature reached - shutting down", which it promptly does. 

Unfortunately, the BIOS is 5 years old, and the reported temperatures (acpi -t, acpitool -tv) don't make sense - acpi -t reports a temperature of 4294967040.0 degrees C, while acpitool reports -264 C. That's also what the kernel log messages say, and the trip-points are also reported by acpitool as "Critical (S5): -264 C; passive: -273 C and active[0]: -267 C.

In Windows XP SP2 the Everest report tool reports two temp sensors, with sensible temperatures: cpu 50 C; motherboard 45 C.

I've requested a BIOS update from Phoenix/Award; meanwhile, is there anyone who can tell me how to stop the kernel turning off the cpu fan as soon as the boot process starts? 

Is this a bug - should I report it? I have copies of dmesg, kern.log, syslog, and the thermal report from acpitool, if they will help anyone sort out what is happeneing..

Thanks in advance for any help - this is getting tiresome........

---

### Post by scradock on 2007-05-06
Found another thread about the same problem:- [http://ubuntuforums.org/showthread.php?t=364386](http://ubuntuforums.org/showthread.php?t=364386)

That contains a link to a conversation btw developers who were trying to fix it for kernels 2.6.18 and up; they seemed to think it was working correctly in 2.6.17 kernels. As thread 364386 shows it wasn't, at least for older machines that don't expect the OS to take control of fans.

It seems that the problem stems from incorrect behavior in the fan control module - if the OS tries to switch the fan ON it may go OFF instead. The OS then thinks it's ON, and never tries to turn it on again, even if the cpu overheats. There is a failure to co-ordinate messages if ACPI isn't implemented right in both BIOS and OS.

Suggested fixes:

1) boot with BOTH "noacpi" and "acpi=off" on the kernel line (works for me);

2) [if you dare!] take the driver file "fan.ko" out of the kernel/drivers/acpi/ directory so that the OS stops trying to control the fan at all. It should then be controlled by the BIOS. {I think I'll try just re-naming the file}.

scradock

Is there a way to

---

### Post by hessiess on 2007-05-06
as a absolute last atempt you could try conecting the fan directly to the psu or a separate transformer with the corect voltage. some computers wont boot without a fan pluged in. only do this if nothing else works.

---

### Post by scradock on 2007-05-07
BIOS update would cost $50!!!!! It would be cheaper tp buy a whole new motherboard....

I'll try Feisty and see if the 2.6.20 kernels were fixed......

scradock

---

### Post by scradock on 2007-05-08
Checked the Feisty LiveCD - kernel 2.6.20-15-generic does the same as 2.6.17-11-generic. The fan shuts down 2 seconds or so into the boot process and never comes on again.

Checked the suggestion to remove fan.ko from the drivers/scpi folder under 2.6.17-10-generic and then booting with that as the kernel - same behavior.

Only way for me is to boot 2.6.17-11-generic with "noacpi" and "acpi=off" on the kernel line.

I expect the same kludge would work for Feisty, but I haven't tried it....

scradock

---

### Post by Harkonnen on 2007-05-19
I also have an emachines T1840 and the CPU fan shuts off for me as well during boot. With 6.06(shuts off in 6.10 and 7.04) the fan stays on. That really is the least of my problems with ubuntu. 

I can't even get to the live CD desktop because I keep getting an x-server error. It is having problems with the Radeon 9200se PCI card and the integrated. Tried many different things to get it to work, but this is getting out of hand.

---

### Post by hessiess on 2007-05-20
from my understanding ati cards are alwase problamatic

---

### Post by Harkonnen on 2007-08-14
It's really frustrating that there hasn't been a solution to this problem yet.

Has it been resolved with gutsy?

---

### Post by kamalmostafa on 2007-11-26
This post explains how I fixed the negative-temperature (-270 degrees C) and CPU fan problems on my eMachines system:

[http://ubuntuforums.org/showthread.php?t=623633](http://ubuntuforums.org/showthread.php?t=623633)

It may be of value to some of you as well.

 -Kamal Mostafa

---

