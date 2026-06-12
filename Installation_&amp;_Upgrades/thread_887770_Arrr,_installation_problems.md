---
title: "Arrr, installation problems"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by bill.hardy on 2008-08-12
I'm a long time user of Linux but a first time installer and the experience is leaving me pining for my days of sysadmins. My system is a Dell Inspiron 530 with a Q6600 processor (that's a Core 2 Quad), SATA harddrive, and a basic integrated Intel 3100 integrated GMA. It seemed like this set-up should be just fine for Ubuntu so I had Vista (which I need to keep) free up a chunk of my harddrive, popped in the Ubuntu 8.04 Server (AMD64 version) install CD and installed away (manually choosing the freed space and auto-partitioning it into scratch and EXT3).

The installation seemed to go just fine but when I restarted and selected Ubuntu at the GRUB menu, things started to go very wrong. The first error messages I saw were things like

> ata1.00: qc timeout (cmd 0x27)
ata1.00: failed to read native max address (err_mask=0x4)
ata1.00: revalidation failed (errno = -5)

It kept going though and this was followed a while later by something like:

> Machine Check Exception:                   5 bank 5: <....>
RIP !INEXACT! 10:<....> {apic_timer_interrupt+0x0/0x70}
TSC 4db4dd4658
Kernel panic - not syncing: Machine check


At which point things ground to a halt. Restarting and booting into Vista, I discovered that my machine would no longer sleep properly. In fact, once told to sleep, it would take *two* hard restarts to get it operational again. Luckily, after deleting the Ubuntu partition and rewriting the Vista MBR, that seems to have been fixed.

I still need to get some flavour of Linux installed on this thing though and I'm hoping I can get Ubuntu to cooperate. I've googled around and people seem to be saying the "machine check exception" messages mean that my hardware is defective. But Vista seems to be running perfectly fine so that's hard for me to believe. I'm pondering installing a second harddrive I have laying around and installing Ubuntu on that and using the BIOS bootloader instead of GRUB, which it seems to me should eliminate any kind of Vista vs. Ubuntu problems that might be going on. I'm hoping to figure out what my problems are though before I leap into that whole procedure. Does anyone have any idea what is going on with my machine? Any help would be greatly appreciated.

---

### Post by musicman12 on 2008-08-12
After reading your situation I also Googled the machine check I am with the line of thought you are that it is more than likely not a hardware issue or it would have been apparent in your Vista boot process or while you were using Vista. Here is something that I found that seems to me maybe similar to your issue at hand :

Normal causes for MCE errors include overheating and/or incorrect hardware installation. Overheating can cause electrons to become more animated and thus escape from the silicon tracks, resulting in corrupted data. Some specific manually induced causes could include:

    * Overclocking (naturally increases heat output)
    * Poorly fitted heatsink/computer fans (the same problem can happen with excessive dust in the CPU fan)

Computer software can also cause errors in this way (normally by corrupting data they are reading or writing). For example:
[B][U]
    * Software performing read or write operations to non-existent memory regions which leads to confusion for the processor and/or the system bus.[/U][/B]


You may want to check out some of the references on the bottom of this page as well. [http://en.wikipedia.org/wiki/Machine_Check_Exception]("http://en.wikipedia.org/wiki/Machine_Check_Exception") 

I run into that problem when I first installed Ubuntu about a year ago on laptop. Mine was corrected by just formatting the Linux Partition and doing a fresh install it seemed at the time something just didn't jive right with my install. So hopefully that will help your scenario out.

Good Luck

---

### Post by bill.hardy on 2008-08-12
> **musicman12 said:**
> I run into that problem when I first installed Ubuntu about a year ago on laptop. Mine was corrected by just formatting the Linux Partition and doing a fresh install it seemed at the time something just didn't jive right with my install. So hopefully that will help your scenario out.

Good Luck

Hmm, it's heartening to know that this doesn't mean all hope is lost for getting Ubuntu onto my machine. I guess it seems like maybe the best plan of action is my second harddrive plan, since that should allow an almost fresh install while keeping Vista around.

---

