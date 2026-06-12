---
title: "Kernel 2.6.38.11 - Kernel 2.6.38.10 / crashed (2.6.35-30 works )"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by ritchie-w on 2011-08-19
Hi,

i just updated my mainboard, because of a failure in the grafic chip.

Now I have a icore 7-2600K CPU with 16GB memory.

The system will not boot with the latest kernel version Kernel 2.6.38.11 - Kernel 2.6.38.10 . It crashed and resets the system.

But when I am using Kernel 2.6.35.30, then it works, as you can see.

As well the kubuntu 64bit CDROM does not work. Crashed as well.

Any idea ?

R.

---

### Post by jimmy.lu.drl on 2011-08-19
which video card r u using?
since u have i7 2600k, im assuming ur using the intel hd3000?
did you happen to have the ppa xorg edger enabled? disable it, its known for causing quite some problems for intel graphics;i  had my system crash on me due to that thing enabled.
Altho your problem does not seem graphic card related as u said the older kernel works fine, but just give it a try i guess if u have that ppa enabled.

---

### Post by ritchie-w on 2011-08-20
Hi,

I am using a gigabyte "GA-H67MA-USB3-B3" mainboard and the onboard
grafic chip, which is a sandybridge chip set.

The kubuntu 10.04 64bit LTU live CDROM starts as well. The actual 11.04 crashed as well during startup.

R.

---

### Post by ritchie-w on 2011-08-22
Hi,

how can I check, that  ppa enabled ?

Even, how can I check, at which point the system get a "kernel panic", because it does not store this log file. When I reboot with an older kernel, the last log is gone.

Settings known so far
- Chipset: Intel H67 Express
- Audio: Realtek ALC889
- Network: Realtek RTL8111E
- Grafic: 32-nm-Sandy-Bridge-Prozessor

Thanks for help
R.

---

### Post by ritchie-w on 2011-08-29
Hello,

I still have the problem, that I can not use the actual kernel.

The system will reboot during start up of the system.

Any help to get out of the problem.

I will have the problem on the 32bit and 64bit kernel during start up.

Edit:
- Add a picture of the infocenter (grafic info)
- I am using a HDMI Screen
- System will have 16 GB RAM 
- System will have USB 3 Controller (but not used)
- System will have sata-3 Controller (but only sata 2 used)
- Add kernel log of running 2.6.35


Thanks for help
R.

---

### Post by ritchie-w on 2011-08-30
Hi,

i just installed the kernel 2.6.38.11 kernel and 2.6.38.10 again.

kernel 2.6.38.10 crash during the first boot sequence

kernel 2.6.38.11 shows the login screen, but crashed by entering the
first char for the password. Mouse move does not crash the system.
 (crash mean reset of the CPU)
I disabled USB 3 mode in the bios, but it doesn't help

Rescue mode: Does not start the fail save grafic.

Hope this help to find the problem.
If I have to support more info, please tell me what, i will try to get it.

R.

---

### Post by ritchie-w on 2011-09-22
Hello,

does somebody have news about this problem.

I still can not use the actual kernel and did not know how to fix it. ](*,)

Best regard
R.

---

### Post by Frogs Hair on 2011-09-22
One possible solution may be to remove the proprietary driver if you have one installed .  After removing the driver try to boot with the desired kernel . If you're  able to boot , reinstall the driver if you need it  and reboot again . You would know if the  xorg edger  PPA was installed  because you would have had to install it via the terminal  .

---

### Post by ritchie-w on 2011-10-06
Hi,

I just fixed my problem by installing a Nvidia card.

Both kubuntu installations are running now with the new kernel.

R.

---

