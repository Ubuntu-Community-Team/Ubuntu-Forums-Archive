---
title: "New Kernel Issues"
date: 2022-12-25
forum: Installation &amp; Upgrades
---

### Post by clcrawl on 2022-12-25
First off, I apologize if this isn't the correct forums, I really didn't see one directly related, given this is probably a niche thing. I'm attempting to configure and compile a new kernel from source. I pulled the source directly from kernel.org. The problem is when I boot the new kernel via GRUB it displays "Loading Linux" and then essentially locks up. I never get to the point where it is loading the initial RAM disk. Typically after sitting for a bit, the entire machine will shut off. This happens with 6.1.1 and 5.15.85 so I am obviously missing something. The major challenge is I get next to no indication as to what might be wrong to even know where to start looking, eg there isn't any output other than "Loading Linux" and then it is dead, there is no output on the console beyond that.

The following is some key details about my environment.

**_Ubuntu Version_**: 22.04.1 LTS (Jammy Jellyfish)
**_Workstation Type_**: ASUS - ROG Zephyrus G14 
**_Processor_**: AMD Ryzen 9 4900HS with Radeon Graphics
**_RAM_**: 16GB
**_Filesystem for /_**: btrfs

I've tried the following.

[LIST]
[*]I optimized the config for only what I feel I would need. 
[*]I compiled 6.1.1 essentially with a default config. 
[*]I compiled 5.5.85 with a default config. 
[/LIST]

I am signing the kernels, and I verified this is functional via not getting an error about the shim signature being invalid. One caveat is I did disable module support from the kernel. I am fairly new to signing the kernel etc and it seemed like a pain to have to do this for all the modules. It was more straight forward to simply sign the kernel, and I've typically always compiled a kernel this way anyway. I guess my big question is there anyway to get more information about what is happening when the new kernel attempts to load? I appreciate anyone's insight. Thank you very much!

**_Edit 0935 CST_** - As a test I copied the configuration for the kernel Ubuntu uses, /boot/config-5.15.0-56-generic, and compiled it as is. The initrd and modules were ridiculously large but I'm sure they all got built with debugging symbols. Anyway, leaving the kernel capable of loading modules resulted in my box booting as expected, although incredibly slow in comparison to the stock kernel(s), again I'm sure because of the debugging.

I then disabled modules (CONFIG_MODULES) and recompiled the kernel. On reboot GRUB does get to where it is loading the initrd and locks up. I don't get any other information, it simply hangs on loading the initrd. I'm really interested in why this wouldn't function given the config was the same, unless previous modules aren't "converted" to being compiled statically inside of the kernel and are instead ignored all together.

**_Edit 12-26-2022 0903_**- I was able to get this functional. I can't say exactly what the issue was, but using the default config from Ubuntu's native kernel did work as the jumping off spot. I did ultimately compile with modules, I made the signing of the modules a bit scarier than I needed to since it does it automatically it appears as you build / do the modules_install.

---

