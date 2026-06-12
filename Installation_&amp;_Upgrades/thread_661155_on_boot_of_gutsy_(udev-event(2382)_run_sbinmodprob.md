---
title: "on boot of gutsy (udev-event(2382) run /sbin/modprobe) still having issues"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by sgt_urankar on 2008-01-07
Well I did some grunt work this weekend with my box here is the issue again.  
Hardware spec's:  SLI 570 5.1 ECS main board (Nvidia chip sets) socket 775,  Intel Celeron 3.3 GHz cpu, BFG nVidia 6600 128 Mb video, 2 Western Digital 40 Gb hard drives with a 20 Gb Seagate (for ubuntu),  Took out a PCI rtl8185 wireless card and removed my encore usb wireless card,  Duel booting with Win xp Pro, My ether net is a 10/100/1000 integrated nic based on nVidia spec's, and 1 Gb of ram.

My issue is is this udev-event(2382).  After removeing the wireless card and adapter I rebooted with the live 7.10 cd.  After getting the boot menue I selected the first option for load/install.  After the load starts it errors out with this udev-event(2382) sbin deal.  I have not worked with linux enough to know where to start.  I did how ever removed the tings not really needed to boot and still have the same inssues.  I thought it was the wireless stuff, to my dismay it was not.  Fiesty Fawn loads fine and works fine untill I get the kernel update to the minor update (the last set of numbers) goes to 20.  Then my x server crashes at boot time and wants to be reconfigured after it was configured with nvididia-glx-new.

BTW  I can still boot the old kernel if i select it at the grub menu.

---

