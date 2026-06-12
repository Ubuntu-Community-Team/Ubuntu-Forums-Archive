---
title: "Grub2 and apic = off noapic nolapic"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by senectus on 2010-01-09
To boot into my desktop I have to edit the boot menu option to include apic = off noapic nolapic as the Asus mainboard I have is a bit ugly in that area...

In old GRUB I could do this permanently pretty easily, but I can't figure out how to do it in Grub2..

Can someone help?

---

### Post by Elfy on 2010-01-09
Run 

```
gksudo gedit /etc/default/grub
```

add it to the GRUB_CMDLINE_LINUX_DEFAULT line

you can see I added hpet=force

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force"

save the file then run 

```
sudo update-grub
```

---

### Post by senectus on 2010-01-09
worked perfectly, thank you very much

---

### Post by oldfred on 2010-01-09
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[/LIST]
You may want to move it to grub_cmdline_linux so it is also added to the recovery modes also.

[LIST]
[*]**GRUB_CMDLINE_LINUX**
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
[*]**GRUB_CMDLINE_LINUX_DEFAULT**="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.
[/LIST]

---

### Post by tonytraductor on 2010-07-17
Okay.
I keep seeing various different versions of this.
noapic nolapic
apci=off
apic=off

Which is correct?

Why do I see both apci an apic?

I'm finding this confusing.
I was told that adding this option might resolve some system freezes I'm experiencing.

Also, after editing /etc/default/grub 
(sudo nano /etc/default/grub)
I did 
sudo update-grub
and got
command not found
(the changes were saved, anyway, after editing in nano...does this matter?)
??

thanks
tony

---

### Post by dlynes on 2010-09-23
I don't know about other kernel versions, but in the kernel version shipped with Jaunty (9.04), you need to use noapic, not apic=off.

There's no such option as apci.  It's acpi (Advanced Configuration and Power Interface) and apic (Advanced Programmable Interrupt Controller).  lapic is 'local' APIC.

> **tonytraductor said:**
> Okay.
I keep seeing various different versions of this.
noapic nolapic
apci=off
apic=off

Which is correct?

Why do I see both apci an apic?

I'm finding this confusing.
I was told that adding this option might resolve some system freezes I'm experiencing.

Also, after editing /etc/default/grub 
(sudo nano /etc/default/grub)
I did 
sudo update-grub
and got
command not found
(the changes were saved, anyway, after editing in nano...does this matter?)
??

thanks
tony

---

