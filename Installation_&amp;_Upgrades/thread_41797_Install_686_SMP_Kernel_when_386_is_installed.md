---
title: "Install 686 SMP Kernel when 386 is installed"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by cyberdog on 2005-06-14
Chello to all, I can't quite get the answer I am looking for. I currently am running the 386 kernel on my P4 2.66GHz HT Laptop. I want to install the 386 SMP Kernel. I know I can go into Apt and choose to install the 686 SMP Kernel. 

Once that is done what do I need to do to use this kernel? I previously hosed my system by choosing the 686 SMP Kernel and un-installing the 386. It presented me with some messages about my system would not boot, blah, blah. Sure enough it would not start.

So now I'm back with a fresh system. I want to install the 686 SMP. What do I need to do to install and use this kernel?

Thanks

John

---

### Post by netrattler on 2005-06-14
The 686 SMP kernel is for dual processor support only. You needed to install the linux-image-686 kernel. Here are the instructions on how to install the kernel at the terminal. I will have you install the linux-restricted-modules-686 and it will automatically install the correct kernel for you.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-686
Reboot
When the grub boot loader starts press Esc and it will allow you to select which kernel you want to use, the new 686 kernel will now be the default. It will also allow you to boot from the old 386 kernel if trouble occurs in the 686.

Hope this answers your question,
Joe

---

### Post by bigcletus on 2005-06-20
[QUOTE=netrattler]The 686 SMP kernel is for dual processor support only. You needed to install the linux-image-686 kernel. Here are the instructions on how to install the kernel at the terminal. I will have you install the linux-restricted-modules-686 and it will automatically install the correct kernel for you.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-686
Reboot
When the grub boot loader starts press Esc and it will allow you to select which kernel you want to use, the new 686 kernel will now be the default. It will also allow you to boot from the old 386 kernel if trouble occurs in the 686.

Hope this answers your question,
Joe[/QUOTE]

I have a AMD Athlon XP...will those instructions work in my case too?  So I can upgrade the default kernel?  Thanks :)

---

### Post by netrattler on 2005-06-21
The AMD Athalon XP processor you will want to use linux-image-k7. So here are the instructions for the AMD processor.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-k7
Reboot

Joe

---

