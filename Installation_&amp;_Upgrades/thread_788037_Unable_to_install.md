---
title: "Unable to install"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by MunterMan on 2008-05-09
A lot of people seem to be having this problem, but nobody seems to be coming up with a definitive answer.

Stick the cd in try and run the live version of 8.04 or install it and I get the same error: the orange progress bar for a couple of minutes then ata exception emask errors.

I have xp already installed, no floppy (disabled in bios), two hard drives, one sata and one ide.

I have had suse 10.2 and mandrake 9.2 on this system in the past (which both installed without a problem). Since then I have had to do a format and a reinstall of windoze. So I thought I would give ubuntu a go.

Same problem with version 7 as well by the way.

Has anybody cured this problem with out changing sata cables?

---

### Post by dstew on 2008-05-09
The problem may have to do with other systems, like the Advanced Configuration and Power Interface (ACPI) or the Advanced Programmable Interrupt Controller (APIC). The errors you get may be a side effect of these more fundamental issues.

You can try to boot the Live CD using kernel parameters to disable these systems using F6 at the first menu. The kernel parameters to try are **acpi=off noapic nolapic**.

If you still can't get the Live CD to boot, you can install using the Alternate Install CD, which uses a text-based interface. You can get it from the Ubuntu download page, just check the box below the Start Download button.

---

### Post by MunterMan on 2008-05-17
I'm afraid that did not help. Now I get a revalidation error, then it starts on the ata exception emask errors again.

Very annoying.

---

### Post by Pumalite on 2008-05-17
Try all_generic_ide

---

### Post by MunterMan on 2008-05-26
Tried it, didn't work, gave up. 
Ubuntu that is, not Linux.
Gone back to opensuse.

---

### Post by MachineBucket on 2008-05-26
I was having a similar problem with a Gateway MX7515 notebook. The option 'acpi=off' worked for me. Hope that helps someone. :)

---

