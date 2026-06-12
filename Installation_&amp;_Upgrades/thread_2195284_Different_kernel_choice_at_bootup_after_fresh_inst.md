---
title: "Different kernel choice at bootup after fresh install"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by Gnomjkl on 2013-12-23
I just installed Ubuntu 13.10. My config is maybe a bit special, I'm on a Mac, so booting in EFI mode using rEFInd as a boot manager, which directly boots a Linux kernel without a boot loader (Linux kernel auto-boots itself). As for as I can tell, this setup worked flawlessly with 13.04. However, it offers me a choice between three kernels versions, namely:
vmlinuz-3.11.0-12-genericvmlinuz-3.11.0-14-generic.efi.signed
vmlinuz-3.11.0-14-generic
I tried vmlinuz-3.11.0-14-generic since it seems like the latest and I don't know what the signed one is used for. It seemed like it worked. So, easy question: which one should I use (if any difference)? And, if somebody has a bit more time to spare, is it possible to remove the ones not in use? Just to avoid any mistake. I could do it by configuring the boot manager if it can't be done on the Ubuntu side or is too complicated, but as much as possible I'd like to keep it in auto-conf mode.

Thanks :)

---

### Post by NoahR on 2014-01-02
I'm in the same boat with the same question having done a fresh 13.10 install on my MacBook Pro this week.

I am booting from an external USB storage which also has rEFInd installed on a partition of that USB storage.  When I did the Ubuntu installation, I started the installer with this command from a "Try Ubuntu" terminal session: 
[FONT=courier new]ubiquity -b[/FONT]
As I understand it, this prevents GRUB from installing.

I can say I have booted both the [FONT=courier new]vmlinuz-3.11.0-14-generic.efi.signed [/FONT](my chosen default) and [FONT=courier new]vmlinuz-3.11.0-14-generic[/FONT] kernel executables.  I don't experience any difference between the two.  Both boot my computer in EFI mode -- not BIOS emulation.
As long as I'm correct about this, it seems like the later should be named [FONT=courier new]vmlinuz-3.11.0-14-generic.efi[/FONT] for consistency.   The corresponding files in /boot are different though.   If anyone could explain the difference, I'd find it informative.

I don't know for sure there would be a difference in the kernel executable for a BIOS machine vs an EFI machine, but I think so.

I'm digging into these issues now, because I really need the NVIDIA proprietary display drivers to work for use with CUDA and they don't in my current config.  After installation the display goes black upon transition to the Ubuntu Desktop Environment.
I'm finding a small selection of posts around the web suggests the NVIDIA drivers will only work in BIOS (emulation).

---

