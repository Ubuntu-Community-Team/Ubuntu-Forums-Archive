---
title: "Can't install 18.04, hangs on ethernet?"
date: 2019-01-31
forum: Installation &amp; Upgrades
---

### Post by aplatypus2 on 2019-01-31
Hi all, 

I've been trying to install Ubuntu for the past couple days, but so far no joy. After a lot of research, and a lot of various attempts and tweaking, I'm at a bit of a loss. 

It looks like for some reason the installer hangs here:

[5.870986] e1000e 0000:00:1f.6 (uninitialized) : registered PHC clock

There is a bug on launchpad somewhat matching: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1785171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1785171) 
But this seems to be affecting users actually using 18.04, I can't even get through the installer. 

So far here's what I've tried:

BIOS/UEFI: 
- Currently booting on UEFI/Legacy 
- Secure boot is disabled
- Fast boot is disabled 

Boot options:
- Removed quiet flag 
- nomodeset*
- acpi=off*

*To avoid a couple errors that came up early on/black screen with a cursor. 

This is a freshly built machine with no other glaring issues and will be only booting Linux, so it's never had and will never have Windows. 
 
Does anyone have any ideas that could help get this going? It's very clear this is getting caught up with the Intel Ethernet driver (mobo has a I219-V Ethernet connection), but can't install to actually see if there's any debugging to be done. I've also tried installing using the alternative installer, but that just gets stuck on 'detecting network hardware', which is clearly the same problem, just a little less verbose. 

Thanks!

---

### Post by kc1di on 2019-02-01
first does the live session boot ok can you get to the Desktop with the live disk?  If you can please give us the output of this terminal command:```
lshw
```
and if you can get a internet connection install inxi ```
sudo apt install inxi
``` and give us the output of ```
inxi -Fxz
``` Thanks.

---

### Post by davidmmichaelson on 2019-07-29
Hey, I am having *exactly* the same thing happen for me and I cannot get into a live session boot. It's failing in the immediate steps past choosing kernel in GRUB.

EDIT: I've tried all of the solutions that OP has tried too and been unsuccessfully trying to troubleshoot this for like 6 hours. I've even flashed my BIOS.

---

### Post by rsteinmetz70112 on 2019-07-31
Can you boot from an USB drive into a live(demo) session?

---

