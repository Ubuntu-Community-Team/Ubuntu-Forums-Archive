---
title: "Want to Boot Multiple Distros With GRUB"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by LeapingLlama on 2011-06-21
Hello all!

I currently am in an adventurous phase and want to try other distros while still having a reliable, stable Ubuntu installation to fall back on. I'm currently in the process of partitioning my disks, and I realized that I might have trouble booting them, as the most recently installed would control GRUB and clobber any previous GRUB  setup. So what I want to know is how to go about managing everything so that only one distro, preferably Ubuntu, has control of the GRUB menu at boot up, and will still recognize the other distros on other partitions.

I plan to have three 15GB root partitions, one swap, and one home partition for each distro.

Would I create a /boot for each distro? Or create one /boot with files from each distro copied there? Or should I do something else entirely?
I just don't want the distros to interfere with each other. Also, I don't want to use VMs for this, because I want to see what a real full-performance install is like for each distro.

Any help is appreciated!

---

### Post by geoff07 on 2011-06-21
Why not install Virtualbox under your stable Ubuntu, and inside VB install any number of virtual machines with whatever you need on each? No messing with GRUB and no risk to your main setup. And you can use them concurrently as well. And it's all free.

---

### Post by YesWeCan on 2011-06-21
> **LeapingLlama said:**
> Hello all!

I currently am in an adventurous phase and want to try other distros while still having a reliable, stable Ubuntu installation to fall back on. I'm currently in the process of partitioning my disks, and I realized that I might have trouble booting them, as the most recently installed would control GRUB and clobber any previous GRUB  setup. So what I want to know is how to go about managing everything so that only one distro, preferably Ubuntu, has control of the GRUB menu at boot up, and will still recognize the other distros on other partitions.

I plan to have three 15GB root partitions, one swap, and one home partition for each distro.

Would I create a /boot for each distro? Or create one /boot with files from each distro copied there? Or should I do something else entirely?
I just don't want the distros to interfere with each other. Also, I don't want to use VMs for this, because I want to see what a real full-performance install is like for each distro.

Any help is appreciated!
Not a problem. Each time you install a new linux distro tell it not to install Grub/bootloader at all (even if it complains). Then you boot back into your main Ubuntu and run sudo update-grub to add the new OS to Grub's boot menu. Grub may not be able to boot every linux OS type without some tweaking.

You don't need separate swaps for each OS, you just need 1 swap partition on your drive that they can all share.
You don't need to do anything with /boot

---

### Post by beew on 2011-06-21
> **geoff07 said:**
> Why not install Virtualbox under your stable Ubuntu, and inside VB install any number of virtual machines with whatever you need on each? No messing with GRUB and no risk to your main setup. And you can use them concurrently as well. And it's all free.

Because unless your machine is powerful enough VB may not run and it can be slow.

---

### Post by beew on 2011-06-21
> **YesWeCan said:**
> Not a problem. Each time you install a new distro tell it not to install Grub/bootloader at all (even if it complains). Then you boot back into your main Ubuntu and run sudo update-grub to add the new OS to Grub's boot menu.

You don't need separate swaps for each OS, you just need 1 swap partition on your drive that they can all share.
You don't need to do anything with /boot

Exactly, except if you want to install multiple versions of Ubuntu  (maybe one for testing one for production) or different flavour of Ubuntus (Kbuntu, Xubuntu etc) then the option of not installing bootloader is not available. In that case install it in the partition where the OS is would solve the problem.

 For example, you have Ubuntu 11.04 in sda1 which controls grub, you want to install Kubuntu 11.04 or another copy of Ubuntu 11.04 in sda2, then you should install the bootloader in sda2 (instead of sda) during installation.

---

### Post by LeapingLlama on 2011-06-21
> **YesWeCan said:**
> Not a problem. Each time you install a new linux distro tell it not to install Grub/bootloader at all (even if it complains). Then you boot back into your main Ubuntu and run sudo update-grub to add the new OS to Grub's boot menu. Grub may not be able to boot every linux OS type without some tweaking.

You don't need separate swaps for each OS, you just need 1 swap partition on your drive that they can all share.
You don't need to do anything with /boot

Do all distros give you the option of not installing a bootloader? I know for Gentoo it would be as simple as not emerging it, but for other distros with more automated installs, are there some that don't ask and simply install the bootloader anyway?

---

### Post by YesWeCan on 2011-06-21
I really don't know. I forgot that Ubuiquity doesn't have a "no bootloader" option. Why not! I would hope the installer on the *alternate* CD does. I know the standard OpenSUSE installer does.

@beew: thanks for pointing this out and I agree one can install to the partition if necessary.

---

