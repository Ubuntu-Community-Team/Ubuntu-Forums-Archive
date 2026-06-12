---
title: "Physical KASLR disabled: no suitable memory region"
date: 2019-12-01
forum: Installation &amp; Upgrades
---

### Post by 7erom on 2019-12-01
[LEFT][COLOR=#242729][FONT=Arial]HI to all, 

I built and installed the latest Kernel (v5.4) from source (downloaded from Linux repo). I followed the steps explained here:

[/FONT][/COLOR][COLOR=#242729][FONT=Arial][URL="https://www.cyberciti.biz/tips/compiling-linux-kernel-26.html"]https://www.cyberciti.biz/tips/compiling-linux-kernel-26.html

[/URL][/FONT][/COLOR][COLOR=#242729][FONT=Arial]I used _**make menuconfig**_ but did not make any change to default values. After doing all steps, I rebooted but got this error on a black screen in boot time:

[/FONT][/COLOR][/LEFT]
> [FONT=inherit]
Physical KASLR disabled: no suitable memory region![/FONT]


[LEFT][COLOR=#242729][FONT=Arial]I`m using ubuntu 19.10 with deafult Kernel 5.3.0-23-generic.[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Here is some info and sth I did to solve thie problem:

[/FONT][/COLOR]
[/LEFT]
> 
cat /boot/config-5.3.0-23-generic | grep CONFIG_RANDOMIZE_BASE=y
CONFIG_RANDOMIZE_BASE=y


> 
cat /boot/config-5.4.0+ | grep CONFIG_RANDOMIZE_BASE=y
CONFIG_RANDOMIZE_BASE=y



[LEFT][COLOR=#242729][FONT=Arial]I changed the Grub according to [https://askubuntu.com/questions/1000525/kaslr-disabled-could-not-find-suitable-e820-region](https://askubuntu.com/questions/1000525/kaslr-disabled-could-not-find-suitable-e820-region) but nothing happened.[/FONT][/COLOR][COLOR=#242729][FONT=Arial]

Here is my first experience in building the kernel. I`d really appreciate it if you could help me.
[/FONT][/COLOR][/LEFT]

---

### Post by DuckHook on 2019-12-02
Welcome to the forums, 7erom;

I do not have the knowledge help you with technical answers. However, as a general observation, if you are trying to build your first kernel, my strong advice is to build it within a VM so that you do not risk your base system. It is best to have all of the advantages of a VM (including falling back to good snapshots) when experimenting with fundamental system components such as the kernel.

---

### Post by 7erom on 2019-12-02
> **DuckHook said:**
> Welcome to the forums, 7erom;

I do not have the knowledge help you with technical answers. However, as a general observation, if you are trying to build your first kernel, my strong advice is to build it within a VM so that you do not risk your base system. It is best to have all of the advantages of a VM (including falling back to good snapshots) when experimenting with fundamental system components such as the kernel.

Dear DuckHook, many thanks to you for your guidance.
Yes, I use VM because of its snapshot capability.

---

