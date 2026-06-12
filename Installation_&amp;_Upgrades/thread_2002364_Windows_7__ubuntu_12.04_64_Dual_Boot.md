---
title: "Windows 7 / ubuntu 12.04 64 Dual Boot"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by tristicles on 2012-06-12
Hi all. I know there's stacks of information about how to do this on the net. I've done it myself a fair few times. The problem is that they all seem to have an achilles heel somewhere. I'm building a PC for my parents  so want this to be as automatic and pain-free as possible. They're pretty easily spooked by all this IT stuff, so this really needs to be transparent. Also, they live about an hours drive away, so I can't just nip round there to fix issues that easily.

Drive is partitioned as follows:

/dev/sda1 swap
/dev/sda2 ubuntu
/dev/sda3 Windows7
/dev/sda4 data partition (ntfs)

The "standard" way of installing Windows first, then Ubuntu with grub in the MBR is OK. The problem is Windows gets shunted off the bottom of the Grub menu with subsequent kernel updates. Getting it to default to Windows and keep it there is a nightmare. I know this can be edited, but that's beyond my folks' expertise.

There's Burg. That seems like a better idea as there will be fewer menu items. However, I've read about burg not (always) updating with kernel updates. People have mentioned updating /etc/kernel-img.conf to update burg to solve the problem. However, I've also read that there's potential for that file to be re-set with a system update, so that's not really a safe option.

Another option seems to be to install grub into the Ubuntu partition, and use the Windows bootloader in /dev/sda. However, that seems to be reasonably fiddly, although the result should be pretty robust!

If I install grub into /dev/sda2 for ubuntu, then install Burg into /dev/sda, giving my folks a simple (and pretty) menu, would any new kernel updates go into grub in /dev/sda2, leaving burg safely untouched in the MBR?

Any thoughts greatly appreciated.

Cheers,
Tris

---

### Post by darkod on 2012-06-12
With 12.04 there is not much movement in the boot menu after new kernel installs. In fact, it only happens the first time where an entry called Previous Versions is created (and windows goes one place down), and after that all older kernels are inside this entry.

But anyway, you can easily make windows be first, and then leave the default OS to be number 0 or which ever you want. I usually do this on dual boot.

I make a copy of 30_os-prober into 06_os-prober. Then I make the original not executable. Because 06 is lower then 10_linux, all OSs found by os-prober (in this case windows) will be ABOVE linux (ubuntu).

```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

PS. I am typing from memory, double check if the folder where the files are is really /etc/grub.d

Does that help you? Like this windows will never move from the top spot (I don't mean in any OS ranking :) ).

---

### Post by tristicles on 2012-06-13
Cheers matey. That's really solved all my problems. Those scripts are indeed in /etc/grub.d/. Don't have to worry about multiple bootloaders or hacking the Windows one now.

Thanks again.

---

