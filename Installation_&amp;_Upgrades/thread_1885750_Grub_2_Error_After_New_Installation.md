---
title: "Grub 2 Error After New Installation"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by The_Fool on 2011-11-23
I recently upgraded my CPU to the Intel i7 2600k and did a fresh install of Ubuntu 10.04 LTS.  This included Grub 2.  I installed this along side Windows 7.

When my CPU settings are set to default everything goes fine with Grub.  However, once I overclock my CPU, increase voltage the proper amount for the CPU to be completely stable (I tested this in Windows 7 before the installation of Ubuntu), then restart, I get the same error from Grub every time:

error: no such device: 74389867-a2e3-457e-966b-a10943a5369b

It then drops me to the Grub Rescue prompt, which I have no idea how to use at the moment.  I have no idea what that device is, either.

This error occurs only when I apply my overclock settings.  I know the CPU is stable.  Besides, if it weren't, it wouldn't give the exact same error every time at the same point.  As it is right now, I can no longer overclock this CPU as long as Grub 2 is in the MBR.  What is going on here and how can it be fixed?

---

### Post by drs305 on 2011-11-23
If you can use an Ubuntu LiveCD, please download and run the Boot Info Script and post the contents of RESULTS.txt

This file will show us the status of your boot files and probably show us what is happening. Also, have you ever successfully run Ubuntu with the system overclocked?


If you prefer troubleshooting/solving this on your own, you could also try the Boot Repair tool.

Both links are in my signature line: "BIS" and "Boot Repair"

---

### Post by The_Fool on 2011-11-23
> **drs305 said:**
> If you can use an Ubuntu LiveCD, please download and run the Boot Info Script and post the contents of RESULTS.txt

This file will show us the status of your boot files and probably show us what is happening. Also, have you ever successfully run Ubuntu with the system overclocked?


If you prefer troubleshooting/solving this on your own, you could also try the Boot Repair tool.

Both links are in my signature line: "BIS" and "Boot Repair"
Did you want me to run that script while overclocked or at default settings?  I have not run Ubuntu on this new CPU when overclocked, yet.  It works normally at default settings.

---

### Post by drs305 on 2011-11-23
> **The_Fool said:**
> Did you want me to run that script while overclocked or at default settings?  I have not run Ubuntu on this new CPU when overclocked, yet.  It works normally at default settings.

We can start by looking at a RESULTS.txt from a normally running system; that way we can at least see how it is set up and what partition is causing at one of the problems.

I do not overclock and thus probably don't have the necessary background to offer a lot of advice about what overclocking may do to a Linux system. 

The Grub rescue prompt normally indicates that the MBR instructions aren't finding the Grub files in the specified location. I don't know the interrelationships between the overclocking and partition recognition, but if you haven't ever had it run successfully while overclocked it would appear there is obviously something preventing Grub from identifying the boot files.

Hopefully we'll get some overclockers reading this that can shed some light on doing so in Ubuntu.

With your permission, I'd like to edit the title of the thread and add "Overclocking" to the end, which may draw in users with more knowledge in this area.

---

### Post by The_Fool on 2011-11-23
I reviewed the results of the script and I discovered why this was happening.  My overclock profile in the BIOS had a different disk drive chosen for the startup drive.  That drive used to be in an old computer and I decided to put it in this new computer as a storage disk drive.  I have a new, bigger, and better hard drive for the operating systems, now.  The old MBR on that old drive was loaded instead of the correct one.

I have fixed this problem by switching the drives around in the priority list, and overclocking works perfectly once again.  Thanks for the recommendation of the boot info script as it assisted in discovering this.

You may change the title if you wish.  I have marked it as solved.

---

### Post by drs305 on 2011-11-24
Good job troubleshooting your issue. The script is an excellent tool for analyzing boot issues. I suppose there is no need to change the title now - thanks for marking the thread solved.

Happy Ubuntu-ing !

---

