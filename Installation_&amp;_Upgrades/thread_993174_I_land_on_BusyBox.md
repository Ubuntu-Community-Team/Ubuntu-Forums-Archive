---
title: "I land on BusyBox"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by kmhosny on 2008-11-25
Hi everyone,
I installed Ubuntu 8.10 on my laptop using Wubi, so i installed Wubi and then asked for reboot to complete the installation.
When i choose Ubuntu from boot menu i landed on BusyBox with reaaaaally limited commands to use, and the installation isn't completed yet.
so if anyone could help me with my issue to begin a new life with Ubuntu :)
Thanks

---

### Post by manishtech on 2008-11-25
This is known as the most dreaded problem one can face. By dreaded I mean that it doesn't do any harm to the hardware, but hardly anyone I know was able to fix it without a reinstall

Maybe these threads would be appropriate:
[What is Busy Box]("http://ubuntuforums.org/showthread.php?t=536850")

[Fixing Busy Box Problem, an example on Feisty]("http://ubuntuforums.org/showthread.php?t=558614")

[Lastly this is for Gutsy, but this is too long]("http://ubuntuforums.org/showthread.php?t=579493&page=3")

---

### Post by kmhosny on 2008-11-25
i tried  the "all_generic_ide" thing but it didnt work, i should point that the linux isn't completley installed it needs to complete the installation here are the 3 commands that i found in the GRUB menu:
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/local=en_US-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync

initrd /ubuntu/install/boot/initrd.gz

when i type kinit command it diplays something like :
root=dev(0,0)
unable to mount root
or something like that

---

### Post by manishtech on 2008-11-26
My best suggestion is to do a clean reinstall. Busybox is a minimal shell which is used in time of emergency.

---

### Post by kmhosny on 2008-11-26
each time i re-install it does this again and again and ...

---

