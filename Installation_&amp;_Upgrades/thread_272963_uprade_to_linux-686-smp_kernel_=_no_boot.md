---
title: "uprade to linux-686-smp kernel = no boot"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by The_Borg on 2006-10-07
I have been using Dapper on my new Core2Duo for a month now. It only detected one core (2.6.15-27-386 kernel), so I decided to have a look at it. 

I followed instructions as they can be found in many topics and just installed the linux-686-smp package trough synaptic. All went well and after a reboot ... the 686-smp kernel just did not start and it now stops on the familiar "loading kernel" when booting, without an error message. I can still use my old 386 kernel to boot, but I would really like to use my second core. 

I started the 686-smp in restore mode, but it's a no-can-do as well. I don't have a clue on how to troubleshoot this, so any suggestions are welcome.

Thx in advance

---

### Post by dcstar on 2006-10-08
> **The_Borg said:**
> I have been using Dapper on my new Core2Duo for a month now. It only detected one core (2.6.15-27-386 kernel), so I decided to have a look at it. 

I followed instructions as they can be found in many topics and just installed the linux-686-smp package trough synaptic. All went well and after a reboot ... the 686-smp kernel just did not start and it now stops on the familiar "loading kernel" when booting, without an error message. I can still use my old 386 kernel to boot, but I would really like to use my second core. 

I started the 686-smp in restore mode, but it's a no-can-do as well. I don't have a clue on how to troubleshoot this, so any suggestions are welcome.

Thx in advance

Try installing a "standard" 686 kernel, if that loads it should work better than a 386 kernel anyway.

---

### Post by mherring0209 on 2006-10-21
install and make default boot the 2.6.15-23-686 kernel with -SMP

It works well my my dual core 750Mhz Intel desktop.  I just cannot like you use the -27-686 kernel

---

