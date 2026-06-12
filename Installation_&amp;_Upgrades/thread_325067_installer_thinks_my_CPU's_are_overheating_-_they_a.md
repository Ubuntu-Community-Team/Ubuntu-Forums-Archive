---
title: "installer thinks my CPU's are overheating - they are not"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by Unc0 on 2006-12-24
hi all, it's been a couple of years since i've had a play with linux. i decided to try ubuntu 6.06 LTS but during the initial boot up from the CD, it gets to a stage (after loading several files from the CD) where the installer thinks that my CPU's are overheating. 

it quotes some ridiculous temperature, like 305C (yes, three hundred, not 30.5) and it then proceeds to shut down the system (understandably)

the thing is, my CPU's are not overheating. this seems to be an issue only in the later releases of not just ubuntu, but fedora core too (version 6).

i'm guessing it has something to do with the current kernel version because i can install without any issues if i use an old ubuntu installation CD (version 4.10) and i have also installed successfully with Red Hat 9.0

the system is a Gigabyte GA-6BXD motherboard with dual Pentium 3 500MHz CPU's and 768MB of ECC RAM

my question is, is there an option i can use at boot up (before i press ENTER) that will ignore whatever temperature signal is being misinterpreted by the installer to allow me to continue with the installation? 

TIA

---

### Post by cilynx on 2006-12-25
did you try 'noacpi' or 'acpi=off'?

P3 had dabbling into acpi thermal control that generally didn't work right.

---

### Post by Unc0 on 2006-12-25
i just tried the "noacpi" option and it did the same thing. it shut down because it thinks the CPU's are overheating.

it's interesting you mentioned that option though, as i forgot to mention that i'm running the BIOS as MPS 1.4 (i also tried 1.1 but no luck there either). 

in order to run any Windows setup on this board, i have to press F5 during setup and tell setup that it's an MPS Multiprocessor system, otherwise the windows setup program also will shut down the PC. but because i set it to MPS Multiprocessor, i don't have any problems with the Win installs.

any other suggestions?

thanks heaps.

---

### Post by Unc0 on 2006-12-25
i just tried "acpi=off" and it did the trick

thanks a lot! 

:)

---

### Post by cilynx on 2006-12-25
Glad to hear it.  Have fun w/ the machine...

---

