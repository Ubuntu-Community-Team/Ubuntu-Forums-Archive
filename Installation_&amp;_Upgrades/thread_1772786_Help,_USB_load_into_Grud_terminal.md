---
title: "Help, USB load into Grud terminal"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by ppl on 2011-06-01
What I meant is after trying to load Ubuntu 11.04 Desktop from USB, my laptop directed loaded into a
Grub bash like interface. Seems like I could manual 
load Ubuntu by hand, but the Grub interface are so
different, I have no idea how to do that.

I tried 'boot', it ask me to load Kernel first, but
how can I found kernel in my USB drive?

BTW, what I am trying to do is install Ubuntu 11.04 though UEFI.

---

### Post by srs5694 on 2011-06-01
It sounds like your grub.cfg file may be missing or misplaced. It's possible to correct this problem, but you've got to know where that file is located first. You can use "ls" at the GRUB command line to view your partitions and files to find it, as in:

```

grub> **ls**
(hd0) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
grub> **ls (hd0,gpt5)/**
abi-2.6.31-22-generic grub/ initrd.img-2.6.31-22-generic
memtest86+.bin System.map-2.6.31-22-generic vmcoreinfo-2.6.31-22-generic
vmlinuz-2.6.31-22-generic

```

This example shows the disks and partitions followed by the contents of the (hd0,gpt5) partition, which includes a grub subdirectory, which is where grub.cfg normally lives. (Of course, you might need to search more partitions and even subdirectories -- in a default Ubuntu install, the grub directory is a subdirectory of boot on your main Linux partition, so you'd need to verify that /boot/grub is present; this example is from a computer with a separate /boot partition.) You could then tell it to use the location you find:

```

grub> **set prefix=(hd0,gpt5)/grub**
grub> **set root=(hd0,gpt5)**
grub> **insmod normal**
grub> **normal**

```

If you located a /boot/grub directory, you'd specify that, rather than just /boot, as part of the first command. Of course, if the grub.cfg file isn't present at all, this won't help.

IMHO, GRUB 2 is far from ready for normal use on UEFI systems. If you're using UEFI, you might want to install and use ELILO instead. I posted details of how to do so in [this thread;](http://ubuntuforums.org/showthread.php?t=1772310) however, what I posted was from memory, so it might contain errors.

Note that you can install as many boot loaders as you like on a UEFI system, and use the firmware controls to select which to use. Thus, if you install ELILO, you won't be further damaging your GRUB 2 installation.

---

### Post by ppl on 2011-06-01
Thank you Srs5694.

I think my Grub command doesn't working as Bash at all, 'ls' doesn't working, 'find' will freeze etc, but probably that is Fedora one I tried. I will try tonight to see if I can boot from Grub2 first.

Yeah, I've been spend a few days trying to install Linux on my UEFI laptop, none success, and I am even thing about there is something wrong with my UEFI firmware version or could be my hardware. Because google around, and event Ubuntu's wiki show that 
Ubunt 11.04 should working with my Laptop Dell E6410, but no, not even able to boot from UEFI boot loader, either freeze, blank screen or direct into Grub command line, only the last one seems there is possibility that I can do something about it to make it working.

Definitely will give ELILO a go if Grub command line doesn't working.

Again, thanks for the information.

---

### Post by srs5694 on 2011-06-01
Fedora uses GRUB Legacy, whereas Ubuntu uses GRUB 2. The two have somewhat different recovery capabilities and commands. My post assumed GRUB 2, so if you tried those commands from a Fedora GRUB Legacy installation, they probably wouldn't work.

If you've got a Fedora GRUB Legacy installed and working enough to boot Fedora, though, you could try adding your Ubuntu kernel to that boot loader and boot Ubuntu that way.

(FWIW, the mainstream GRUB Legacy doesn't support UEFI at all, but Fedora uses a forked version that provides UEFI support.)

I'm afraid that most Linux distributions are pretty flaky at the moment when it comes to UEFI. Between that and the fact that UEFI booting is just so different from BIOS booting (and so many users are unfamiliar with it), getting Linux to boot using UEFI can be a challenge. It can be done, though, and once you've figured it out, there are certain advantages to it. For instance, UEFI boot loaders install as files in filesystems, so you don't need to worry about code hidden away in the MBR or in post-MBR sectors, as is common with BIOS boot loaders. Copy the right files to the right places, and convince your firmware to see it, and you can boot. Once the tools are up to snuff and knowledge is more widespread, that should eliminate a lot of BIOS booting problems. In the meantime, though, we're suffering through teething pains....

---

