---
title: "Installing SMP kernel Image"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by palepaul5 on 2005-05-03
Hi,
   can anyone help with a little problem I seem to be having trying to install one of the SMP kernels. All seems to install well, both 2.6.10-5-686-smp and 2.6.11-1-686-smp kernels seem to install fine, but the minute they try to load the desktop the whole system just freezes up. Using the 2.6.10-2 kernel works brilliantly, but I really would like to have both processors up and running. Any pointers and help very much needed and appreciated,

(Y) PJF };-)

---

### Post by valnar on 2005-05-19
Bump... because I have a dual Xeon too and would like to know how to do this in ubuntu.

Robert

---

### Post by kvidell on 2005-05-19
Can you explain the process through which you obtain and install the kernel(s)?

My suggestion is to use Apt-Get to obtain them, but if that's what you're doing then I suppose other options have to be looked at.
- Kev

---

### Post by Rob2687 on 2005-05-22
I've got the same problem here, except with P4 hyperthreading. I installed it through the Synaptic package manager.
The system just locks up completely.

Everything runs perfectly fine with the regular kernels though...

---

### Post by mrbass on 2005-05-22
Well I tried to install the non smp kernel 686?  Why? Simple the default 386 one only sees 885MB.  Also enemy territory works for about 10 seconds the disappears.  I'm guessing it's related to memory I think.

Mem: 906664k total, 412840k used, 493824k free, 69980k buffers
Swap: 1510068k total, 0k used, 1510068k free, 148168k cached

Ok so I installed it and the linux headers too (cuz I figured I've have to reinstall vmare). So I reboot and and it's constantly using 56% CPU.  It does see my 1GB of memory though...thank goodness.  However, my wireless module doesn't exist acx100 so it's a no go.

I tried installing nvidia driver again which I had saved locally and it took literally 4 or 5 mins to install.  Should take less than 30 seconds or so.  Oh well these kernels are whacked bigtime.

---

### Post by valnar on 2005-05-22
I've got a dual Xeon SMP system with 1Gb of RAM on an Intel chipset.  If anyone can point me in the direction of the optimized kernel for me, I'd appreciate it.   :) 

Robert

---

### Post by Bob D. on 2005-05-22
I have 2.6.10-5-686-smp installed and working fine. My P4 2.4Ghz is set for hyperthreading. The System Monitor shows both my processors, seem to bounce between 0-3% usage when idle. I just installed the kernel image from the Ubuntu repos.

Odd so many are having problems. ](*,)

Bob

---

### Post by Rob2687 on 2005-05-22
Yeah...I don't even know where to being to try to fix it. 
For me, it seems to freeze randomly. Sometimes right after boot, some times after an hour or so.

The only thing I can come up with in google is this
[http://www.togaware.com/linux/survivor/ACPI_Kernel.shtml](http://www.togaware.com/linux/survivor/ACPI_Kernel.shtml)

Though it says the  kernel-image-2.6.11-1-686-smp works for him/her, while when upgrading to a lower version it doesn't  :-? It's worth a try i guess...is ACPI that important?

---

### Post by Blues- on 2005-05-23
Had Similuar problems on my dual processor box ..
After i added "noapic" in the kernel boot options 
all my problems went away :)

---

### Post by jcooper on 2005-05-23
I have a HT enabled P4. If I install the i686 / SMP kernels using apt, how do I ensure the 386 kernel is removed? Is this part of the process, unlike warty?

---

### Post by Rob2687 on 2005-05-23
[QUOTE=jcooper]I have a HT enabled P4. If I install the i686 / SMP kernels using apt, how do I ensure the 386 kernel is removed? Is this part of the process, unlike warty?[/QUOTE]
 I just uninstalled the 386 kernel in Synaptic

---

### Post by Rob2687 on 2005-05-23
with acpi=off , it only detects one CPU
and i tried noapic, but it still freezes.

---

### Post by valnar on 2005-05-24
Before I do it, is it simply typing in "apt-get install kernel-image-2.6.11-686-smp" to get the new kernel?

Robert

---

### Post by Rob2687 on 2005-05-24
[QUOTE=valnar]Before I do it, is it simply typing in "apt-get install kernel-image-2.6.11-686-smp" to get the new kernel?

Robert[/QUOTE]
 Yeah that should work...or you could just do it from Synaptic.

I've found that if I run Folding @home it won't freeze but if I close it, everything locks up again. I think it's a power  management issue or something....

Edit: For the record, it was an SATA issue. The problem seems to have disappeared after playing around with the sata modules that were being loaded.

---

### Post by pierroux on 2005-06-04
I have got the same pb with 2 Xeon processors and I use the kernel 2.6.10-...-686-smp. Options acpi=off and noacpi doesn't impact on the problem...

I don't have a solution, but I notice that the system freeze only when gnome is running

---

### Post by muhkuh on 2005-06-04
Hi there,

I've got a BX Board with a Coppermine Celeron and tried the kernel-image-2.6.11-386 and -686. Same thing. The System locks after Gnome is started right after the panel is fully loaded. If you switch to tty1 after X started but before Gnome is fully loaded you can see a lot of kernel warning messages followed by a kernel panic.

Markus

---

### Post by muhkuh on 2005-06-05
I analyzed the kernel messages and the process causing the dump on my system was gam_server that is part of the gamin package. Googling revealed that there were problems with gamin in connection to the inotify kernel feature. Adding the kernel boot option "noinotify" solved the problem for me. May be you should give it a try.

---

### Post by pierroux on 2005-06-06
It seems that the best kernel to use with a xeon is : ...amd64-xeon

Did anyone tried it ? Does the freeze pb go away ?
I didn't find some kernel ending by ...amd64-xeon-smp, so if I install the kernel that end with amd
64-xeon, do you think that the system is going to use my 2 processors?

---

