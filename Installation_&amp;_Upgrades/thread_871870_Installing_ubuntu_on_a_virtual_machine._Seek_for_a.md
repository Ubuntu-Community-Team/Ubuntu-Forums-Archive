---
title: "Installing ubuntu on a virtual machine. Seek for advice. Please help!!"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by csh on 2008-07-27
My old laptop have 512mb ram, and the integrated Intel video card had shared 64mb onboard ram.

I have Ubuntu 8 live cd. I want to install Ubuntu 8 on VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)), which is installed in my laptop.

I don't know how much memory I should allocate for installation of Ubuntu with VirtualBox. According to the System Requirement for Ubuntu ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)), the RAM requirement is very high.

Any advices or comments?

**I accept any advices or comments EXCEPT upgrading my RAM or buy a new laptop.**

---

### Post by Shazaam on 2008-07-27
A normal rule of thumb is to allocate a minimum of half of your physical ram to a virtual machine. Some have had success with less. So you would allocate 256mb to the vm. Since you also share with the video this would drop to 192mb. What this might do is slow the whole pc down (not just the vm) and MAY cause crashes/lockups. If you do experience these problems a better solution would be to try Xubuntu or a lighter linux distribution as a vm.
What is your host os? If it is Windows you could temporarily disable a few services to lessen the memory load and then run the vm.

---

### Post by csh on 2008-07-27
> **Shazaam said:**
> A normal rule of thumb is to allocate a minimum of half of your physical ram to a virtual machine. Some have had success with less. So you would allocate 256mb to the vm. Since you also share with the video this would drop to 192mb. What this might do is slow the whole pc down (not just the vm) and MAY cause crashes/lockups. If you do experience these problems a better solution would be to try Xubuntu or a lighter linux distribution as a vm.
What is your host os? If it is Windows you could temporarily disable a few services to lessen the memory load and then run the vm.

Thanks for your advices. The host OS is Windows XP Home Edition with Service Pack 2.

---

### Post by snowpine on 2008-07-27
A huge +1 to Xubuntu instead of Ubuntu; Xubuntu should be fine with 192mb of virtual ram. Personally, I like to run Fluxbuntu in my virtual machine with 96mb of virtual ram, leaving plenty of ram free for the host os. Not everybody likes Fluxbuntu though--but it sure is light! :) If your host machine is an old laptop, just think of your virtual machine as a really, really old laptop and you'll be fine.

---

### Post by rukshankb on 2008-07-28
If you have XP SP2 on the machin you can use Virtual box. I think 512MB is enough to do your task.

---

