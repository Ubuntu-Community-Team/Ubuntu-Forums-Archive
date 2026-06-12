---
title: "[SOLVED] Hardy and SATA issues"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by anars on 2008-05-10
I think I'm suffering from this too. The error is periodical.

The progress bar when booting up just moves from side to side. It hangs just after loading ata_piix, and then this keeps repeating:

```
ata1.00: qc timeout (cmd 0x27)
ata1.00: failed to read native max address (err_mask=0x4)
ata1.00: revalidation failed (errno=5)
```

And then later:

```
ata3.00: status: {DRDY}
ata3: soft resetting link
ata3.00: configured for UDMA/66 (shifts to "UDMA/33" later on")
```

Any ideas, people?

---

### Post by anars on 2008-05-10
I fixed it!

Seems like my desktop has a faulty IRQ routing table (shitty firmwares, I guess). So adding "irqpoll" as a kernel parameter in /boot/grub/menu.lst fixed it.

I hope to find a BIOS update and/or firmware updates for my other hardware soon, so I can boot up without the "irqpoll" parameter. Although it shouldn't have a measurable performance hit on desktop systems, I'd still love for my system to run as ideally, with a minimum of "hacks", as possible. At the moment it's enough that it boots every time :-)

Check this [link]("http://ubuntuforums.org/showthread.php?t=468228") and [this]("http://readlist.com/lists/vger.kernel.org/linux-kernel/55/275545.html") for performance clarification regarding the "irqpoll" parameter.

---

### Post by Rocket2DMn on 2008-05-10
I fixed this problem on my 64 bit install by using the "acpi=off" and "noapic" kernel boot options.  When I did a 32 bit install, I had to also use "nolapic".  I haven't done much research on these, so I'm not sure if there is any degradation in performance.
In any case, it could be worth a try.

---

### Post by anars on 2008-05-11
Cool. I'll give those a try instead of irqpoll, then. I'm only experiencing the above problem on my desktop, so I don't mind having ACPI disabled :-)

Thanks for the hint!

---

### Post by anars on 2008-05-11
> **Rocket2DMn said:**
> I fixed this problem on my 64 bit install by using the "acpi=off" and "noapic" kernel boot options.  When I did a 32 bit install, I had to also use "nolapic".  I haven't done much research on these, so I'm not sure if there is any degradation in performance.
In any case, it could be worth a try.

No, it didn't work for me :-( But "irqpoll" doesn't have any measurable effect on desktop environments anyway.

---

### Post by Rocket2DMn on 2008-05-11
Very well, at least it works :)

---

### Post by bford16 on 2008-05-30
When I use irqpoll, I have problems with my DVD drives.  Also, irqpoll does not solve the SATA problem for me. What works for me (SATA DVD on Asus A8V-VM), is "pci=nomsi." With that option, everything works.

---

### Post by mfernand on 2008-05-30
I've tried all options mentioned above. I can boot 50% of time with kernel version 2.6.22-14 with default kernel commands (no command options above used). But with kernel version 2.6.24-16 or 17 I get problems seeing my sata drives. None of the options above work. I have a Dell Vostro 400 with a core 2 duo E6550. Again, nothing works except for kernel version 2.6.22-14.

---

### Post by dburgan on 2008-06-11
> **mfernand said:**
> I've tried all options mentioned above. I can boot 50% of time with kernel version 2.6.22-14 with default kernel commands (no command options above used). But with kernel version 2.6.24-16 or 17 I get problems seeing my sata drives. None of the options above work. I have a Dell Vostro 400 with a core 2 duo E6550. Again, nothing works except for kernel version 2.6.22-14.

I also have a Vostro 400 and experience the same exact problem. It usually takes me about 10-20 attempts in the morning to get my Vostro to boot Ubuntu 8.04 (32 bit), and when I boot in recovery mode I get the exact same error messages as in the first post in this thread.

I don't want to blindly try kernel parameters unless someone knows for sure what this problem actually is.  Help!

---

### Post by Rocket2DMn on 2008-06-11
> **dburgan said:**
> I also have a Vostro 400 and experience the same exact problem. It usually takes me about 10-20 attempts in the morning to get my Vostro to boot Ubuntu 8.04 (32 bit), and when I boot in recovery mode I get the exact same error messages as in the first post in this thread.

I don't want to blindly try kernel parameters unless someone knows for sure what this problem actually is.  Help!

You may have to, there is no excuse for having to try and boot that many times.  It's worth the time, it will only take 5 or 10 minutes to try out.  Here are some options, in the order I would try them:
```
acpi=off noapic nolapic
irqpoll
noirqpoll
all_generic_ide
pci=nomsi
```
You can even start by combining all of them, then removing some until you have only the ones you need to successfully boot.  Sorry it's such a tedious process.

---

