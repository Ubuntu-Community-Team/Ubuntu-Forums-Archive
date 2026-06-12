---
title: "dual booting Windows 10 and Ubuntu 15.04"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by Christian_Battagli on 2015-08-02
I've successfully installed both but I'm having problems getting Grub2 to load on startup.

Here are the results from boot repair: [http://paste.ubuntu.com/11984370/](http://paste.ubuntu.com/11984370/).

I'm getting no errors and everything has been successful so far. The only thing that makes me semi worried is that when I tried to mount the Ubuntu partition and run grub-install on it I'm getting the following error:

```

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

```

When I go to chroot in and try and run grub update I'm getting network errors but I think the solution is somewhere other than having to "chroot" in.

Thanks in advance for all your help!

---

### Post by oldfred on 2015-08-03
You are trying to install a BIOS boot loader version of grub to a UEFI system?
Ubuntu will boot in BIOS mode from a gpt partitioned drive, but needs a tiny 1 or 2MB unformatted partition with the bios_grub flag if you use gparted.

But I think you really want UEFI boot. How you boot installer & Boot-Repair for fixes is how system works. Windows only boots in UEFI mode from gpt and since drive is gpt, you must have Windows in UEFI mode. Boot-Repairs' report did not show the efi files in the ESP - efi system partition.

It also looks like you left Windows fast startup on. That is always on hibernation and does not work with dual boot. Best to boot in Windows from UEFI first and turn that off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

What brand/model system.
Some modify UEFI to only boot Windows by description. That is not per UEFI standard. And we have to do a work around to copy grub or shim's efi files into /EFI/Boot to make it work.

---

