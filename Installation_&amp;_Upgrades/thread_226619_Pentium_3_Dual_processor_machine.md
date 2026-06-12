---
title: "Pentium 3 Dual processor machine"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by tracyapotter on 2006-07-31
I have recently come upon a HP Visualize workstation with dual 600mhz processors.  Will (U,K,X-Ubuntu) take any advantage of both processors or is one just burning electricity?

I am going to use the machine regardless, it has 768M RAM and is 200Mhz faster than the HP Kayak I am using now.

Thanks for the input.

TA

---

### Post by az on 2006-07-31
The installer will install a generic 386 kernel that will only use your first cpu.  Install ubuntu and run

sudo apt-get install linux-686-smp 

and then reboot.  That kernel will use both your CPUs as well as be optimised for pentium.  You are good to go.

---

### Post by tracyapotter on 2006-07-31
Thank you sir,

Noticeable difference in speed.  I think I can now go back to Kubuntu from Xubuntu and not sacrifice the speed difference.

TA

---

### Post by HackMaster on 2006-07-31
Do you need to do this to take advantage of a hyperthreaded processor?

---

