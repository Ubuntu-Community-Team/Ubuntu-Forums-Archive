---
title: "Booting LILO problem after Pingolin installation from the internet (no cd-drive)"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by JuanPTY on 2013-03-20
Hello
I have a computer that had Hardy Heron installed, I wanted to erase everything and install Ubuntu 12.04.2 LTS (Precise Pangolin).
the computer has no cd-drive, I tried making a bootable usb with UNetbootin but the computer would not boot from usb.
I ended up installing it following these instructions: [https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet).
It was going fine until the GRUB installation, it gave me "GRUB cannot install" error so I choose to install LILO instead and finished the installation.
when it booted it showed this

```

VFS: Cannot open root device "sdb1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block (0,0)
Pid: 1, comm:swapper/0 Not tainted 3.2.0-39-generic-pac #62-Ubuntu

```

I searched the forums but most solutions required a live cd and the computer has no cd-drive.
Do I need to buy a new cd-drive or is there any other way to solve the issue?

I am a beginner to linux in general.

Thanks

---

### Post by mörgæs on 2013-03-20
Hi, welcome to the fora.

Please begin with a complete hardware description.

---

### Post by JuanPTY on 2013-03-20
Hi 
I choose to use Ubuntu 12.04.2 LTS because of the Long Time Support and because the computer already had Hardy so I assumed regular ubuntu would worked, I didnt upgrade from ubuntu because I wanted a clean install and I wanted to erase everything.

The computer is a desktop pc, I dont have the hardware specifications at hand, is there a way to look them up without a live cd?

cheers

---

### Post by mörgæs on 2013-03-20
Just post everything you know and let's use Google from there.

---

