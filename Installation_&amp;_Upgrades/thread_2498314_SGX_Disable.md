---
title: "SGX Disable"
date: 2024-06-08
forum: Installation &amp; Upgrades
---

### Post by cyberdevops23 on 2024-06-08
Hello
 I installed Ubuntu 18 and updated it to version 22, it worked for a few days, today I tried to turn it on again, it gets the SGX disable by BIOS error when booting, this option does not exist in the BIOS, and there is no update for the BIOS.  I also added the nosgx parameter to the grub file in the default line and then updated the grub, now it boots and doesn't get errors, but the cursor flashes &#128532;&#128532;&#128532;

 I would appreciate it if any of your friends have any information to guide me &#128591;&#127802;

---

### Post by grahammechanical on 2024-06-08
Are you saying that Ubuntu 22.04 stops loading and does not load to a login screen and desktop?

I am of the opinion that the message that you call an error is actually information put on screen by Linux. The Linux operating system has to keep up to date with improvements to the motherboard, especially security improvements required by Microsoft.

I used to get a message that said "TPM device found. No info provided." Some time between 22.10 and 24.04 Linux developers worked out how to deal with the existence of Security Guard Extensions and Trusted Platform Module support.

Some day we might find that Ubuntu is offering us the ability to use SGX and TPM to securely lock the motherboard from operating systems that we choose to block. I think that this will especially happen to server machines.

As to your problem, are you sure that there is not a setting in BIOS/UEFI utility? SGX has been around from 2015 on motherboards using Intel CPUs. I have been running my laptop that came with Ubuntu 20.4 without any problems even with both SGX and TPM enabled.

Regards

---

