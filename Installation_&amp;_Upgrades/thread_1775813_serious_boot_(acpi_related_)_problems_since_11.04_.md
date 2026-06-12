---
title: "serious boot (acpi related ?) problems since 11.04 upgrade"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by fr4nko on 2011-06-05
Hi all,

it is now quite some times since I've made the upgrade to 11.04 but I've still some serious booting problems. At the beginning I was going to think that these was going to be fixed really fast but I'm very surprised to see that nothing seems to be done for this serious problem.

What I'm doing is to use un older kernel from lucid lynx (to be precise 2.6.32-30). The kernel provided with 11.04, that is 2.6.38-9, just doesn't boot. For information, I had no problem with the previous ubuntu version.

To say everything I really regret to have done this upgrade to 11.04 because nothing good was introduced, only new exciting bugs but here I'm off topic... :-)

So, my problem is during boot, very early. I have no logs because the system really does not boot but I've noted some of the messages (I cannot see a lot because the screen cannot be scrolled). The message is a kernel panic and here some of the messages:

...
power_suppy_changed
acpi_battery_notify
acpi_device_notify
acpi_ev_notify_dispatch
acpi_os_execute_deferred
...

I'm on a Sony VAIO laptop, VGN-CR31Z. The problem seems to be related to ACPI but I'm not sure. I've made some research on internet and I didn't find anything useful or pertinent. I've found some infos about a NVIDIA related problem but it is not the same problem of me, I don't have a NVIDIA card anyway.

I've tried the boot option acpi=off but what happens is that the system does not boot at all (nothing happens, I don't have any message at all).

I hope someone can help. I'm quite sad because of this problem, it seems that the quality of our beloved linux distribution is getting worse. It seems that they are more interested to the catchy new netbook-like fancy interfaces and they doesn't care about correcting bugs and improve usability in many area where linux need to improve.

In past I was proud to propose ubuntu to my friends but now, with this kind of problems, I'm not so sure about ubuntu.

I'm also considering changing linux distribution for something more reliable.

Thanks in advance for any help and sorry for the whining... :-)

Francesco

---

### Post by mörgæs on 2011-06-05
I agree with you that 11.04 is not the most stable of the Ubuntus, but to be fair we don't know if the problem is due to 11.04 or the double upgrade. Have you tried a live boot of 11.04?

---

### Post by Quackers on 2011-06-05
I have a similar laptop with the same MoBo chipset and I have had no problems at all with the newer kernels.
I'm wondering if there has been some sort of problem with the upgrade procedure.
Can you backup everything that you need and try a fresh install of 11.04?

---

### Post by fr4nko on 2011-06-05
> **Quackers said:**
> I have a similar laptop with the same MoBo chipset and I have had no problems at all with the newer kernels.
I'm wondering if there has been some sort of problem with the upgrade procedure.
Can you backup everything that you need and try a fresh install of 11.04?

Hmmm... unfortunately I don't have the time to redo another install but I'm wondering what this can change. After all the problem cames very early during the boot and only GRUB and the kernel get involved...

I would try anyway to redo the install but unfortunately I don't have the time.

Thank anyways for the help... I will stick with the custom boot with 2.6.32.

Francesco

---

### Post by Quackers on 2011-06-05
Fresh installs inherently have fewer issues than upgrades.

---

### Post by Quackers on 2011-06-05
There are also other acpi/apic boot options you could try, like
acpi=force
noapic
nolapic
(the second and third options are not spelling mistakes, they are correct).
Combinations of all can be required, on occasions.

---

### Post by fr4nko on 2011-06-05
> **Quackers said:**
> There are also other acpi/apic boot options you could try, like
acpi=force
noapic
nolapic
(the second and third options are not spelling mistakes, they are correct).
Combinations of all can be required, on occasions.

Wow, it works, Thank you very much, sir! :-)

So, may be that a complete reinstall was not really needed, I've saved a lot of time :-)

Now I'm wondering if I really need all the three options,

acpi=force noapic nolapic

I would like also to understand why now it works and what was the problem, if I'm not asking too much :-)

Francesco

---

### Post by Quackers on 2011-06-05
Try booting with just one at a time and see if that works. Then you will know which one(s) are actually needed. When youfind that out the necessary item can be added to the /etc/default/grub file so that youdon't need to put that in on every boot.
As for specifics on what is done with each option, I'm afrad I'm not the one to ask ther :-)

---

