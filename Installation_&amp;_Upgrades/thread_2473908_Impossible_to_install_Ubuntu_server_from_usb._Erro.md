---
title: "Impossible to install Ubuntu server from usb. Error hardware cpu0 machine check"
date: 2022-04-18
forum: Installation &amp; Upgrades
---

### Post by xeno279 on 2022-04-18
Hello everyone. I have a problem when i try to freshly install ubuntu server 20.04.4
After i start the installation i got this message:

0.132294 mce: hardware error: cpu 0: machine check: 0 Bank 6: ee20000000 and more of them. 3 hardware failure, 1 bios failure and 1 acpi error AE_already exist.

It all seems to be harware problem to me but i know than everything is normally running because it was running just 10hours ago and since i tried to install Ubuntu desktop and other OS with absolutly no problems everything is running except Ubuntu server.

Please help me

Thank you very much in advance

---

### Post by TheFu on 2022-04-18
Just because something worked before, doesn't mean it should work now.  If that were the situation, no cars would ever need to be replaced from overuse.  Computers have moving parts.  Fans move dust around inside.  PSU, GPU, fans, HDDs, all fail.  Sometimes those failures are only seen at boot time, when the stress is just a little higher.

But ... it could be a kernel incompatibility.  I'd try booting from a different kernel. There should be 2 or 3 on a previously installed system.  Or use a flash USB with any number of other Linux distros to check how far they get.  This is part of the process of elimination.  If every distro fails and you use different flash drives, then it is most likely the computer hardware with the fault.  

The old rule of _simplify and test, repeat_ applies.  When it is simplified to the point that nothing else can be removed, then it is time to start swapping hardware.  Bad CPUs happen.  If the thermal paste wasn't properly applied, overheating can happen. Have you removed all but 1 memory stick? If that fails, try the others.  Be certain the single, correct, DDR slot is used.

Does the system beep? How many?  The motherboard manual has a troubleshooting table which says what the number of beeps means.  Some motherboards will have an LED with a code displayed.

But for now, try different distros and different kernels.  Also, clean out the dust from inside the case.  Dust can cause short circuits.

---

### Post by xeno279 on 2022-04-19
And just because you think you know something doen't mean you are right and doesn't mean you can be condescending. And before answer to people to be completly useless please learn how to read a question. I said than i tried more and differents os after i have the problem with ubuntu server with " NO PROBLEM" . What means that every compnent is working perfectly.

---

### Post by TheFu on 2022-04-19
I apologize. I was multitasking and forgot about the 
> It all seems to be harware problem to me but i know than everything is normally running because it was running just 10hours ago and since i tried to install Ubuntu desktop and other OS with absolutly no problems everything is running except Ubuntu server.
paragraph.  Sorry that I'm human.

In these forums, we run against all sorts of skill levels and sometimes the other person isn't as versed and needs things that you think are obvious spelled out.  All I know about you is that you have few posts here, joined the forums this month and claimed the HW was fine ... when a machine check error is shown.  All that I could have known is in the OP. You may be an expert with 45 yrs of hardware skill that are current.

Anyway, Ubuntu server doesn't provide the same wide range of drivers that ubuntu desktop provides and if the kernel is the same as in the desktop version (it should be), that's where a software issue would likely be.

A little overview of the hardware from **inxi -Fxxz** would be helpful.  Boot into a desktop release. Install inxi, run it and please post the results.

I threw the error into google and one result is [https://bbs.archlinux.org/viewtopic.php?id=266210](https://bbs.archlinux.org/viewtopic.php?id=266210).  It is full of troubleshooting ideas and information which would be helpful to know. Do you see dmesg errors when booted into the desktop?  I've been told that the exact same kernel is used for server and desktop versions of Ubuntu, so that would remove another variable.

> This error is typically going to be a bad memory controller/cache on your cpu 75% of the time, bad chipset on your motherboard, bent pins on your cpu socket, or a bad trace on your motherboard.. although on rare occasions other hardware that shorts out the motherboard such as a bad power supply, pci card, or bad caps on the motherboard can cause it also, however unless it's directly linked to the CPU it's extremely rare.). 
I don't know how valid that statement is from the Arch forums, since you've run other Linux and it works with them. It does seem to be the worst case.

Of course, feel free to ignore the questions.

---

