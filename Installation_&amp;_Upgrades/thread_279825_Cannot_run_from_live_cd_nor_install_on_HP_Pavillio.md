---
title: "Cannot run from live cd nor install on HP Pavillion"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by lfloyd on 2006-10-18
I have a HP Pavillion 2.9GHZ machine that has windows xp sp2 as my main operating system.  PClinuxOs will boot in safe mode, but can't can't view windows properly.  With Ubuntu it does not boot at all it tries but returns back to Ubuntu menu.  I tried  the noapic, nolapic settings.  I'm like the other guy if Ubuntu is for humans what am I?  Iso is burned correctly or else it would not even attempt to boot.  Windows will boot, windows business server will boot, PCLinuxOs will boot, but not ubuntu, it tries but dies.  I was able to create a ext2, ext3, and linux swap file with PCLinuxOS.  So linux partitions are already on the drive.  Even if Ubuntu can't boot the live cd it should see the native live partition already there.  I would appreciate any help.  Apparently there seems to be problems with HP installation


Loretta Floyd

---

### Post by Kateikyoushi on 2006-10-18
Which notebook is it exactly ? Maybe someone already went through installation here in the forums. Did you try to install it in safe video mode ?
You can try the alternate install cd maybe you have more luck with it.

---

### Post by jsrealty2 on 2006-10-18
Your not the only one that has this problem. I have friend that has an HP Pavillion a705w that runs at the same speed yours does. His machine does the very same thing that yours does. Does your machine have a CELERON Microprocessor in it, because his does. I keep wondering if thats what the problem is. I hope we or someone out there can help us find the solution to this frustrating problem. If you do find the solution to this problem please let us know and I will do the same.

Thanks,

JaDan Sudderth

---

### Post by Kateikyoushi on 2006-10-18
I seriously doubt the processor has something to do with it, chipset ide controller etc can be somewhat exotic which might cause problems but Intel makes millions of those Cpus and they are used very widely.

---

### Post by lfloyd on 2006-10-18
it's a desktop A007 something like that

---

### Post by lfloyd on 2006-10-18
where is the altcd I've been looking for perhaps its under some other title

---

### Post by lfloyd on 2006-10-18
mine is probably in the same series as his I get my numbers mixed up but it has an hp bios as his undoubtedly does, and mine is the latest because I had to upgrade to accommodate hard drives over 137 gb

---

### Post by lfloyd on 2006-10-18
live acpi=off under special boot parameters (F3) seems to work its configuring now I'll keep you posted

Loretta

---

