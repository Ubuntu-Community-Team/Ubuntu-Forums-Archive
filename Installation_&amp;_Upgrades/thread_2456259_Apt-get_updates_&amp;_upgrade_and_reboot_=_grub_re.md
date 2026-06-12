---
title: "Apt-get updates &amp; upgrade and reboot = grub rescue menu"
date: 2021-01-07
forum: Installation &amp; Upgrades
---

### Post by dniven on 2021-01-07
Ubuntu 18.0.4 server up and running for nearly a year, so I ran apt-get update and apt-get upgrade, and rebooted.

Upon reboot I see the Grub rescue menu. Rebooting and choosing the hard drive from the BIOS menu leads to same Grub rescue place.

Other sites suggest using Boot-Repair tool, but booting from Live disk and using that didn't work. Specifically I was told to run the following:

```
> sudo chroot "/mnt/boot-sav/nvme1n1p3" dpkg --configure -a
chroot: failed to run command 'dpkg': no such file or directory
```

Below is the log from the Boot-Repair tool if anyone knows how to fix this, it'd be much appreciated.

[https://pastebin.com/U4g5eUaS](https://pastebin.com/U4g5eUaS)

---

### Post by CelticWarrior on 2021-01-07
Welcome.

Those were 2 commands.

---

### Post by dniven on 2021-01-07
Edited: command and resulting error

---

### Post by CelticWarrior on 2021-01-08
Again, those were 2 (two) different commands that you tried to run in the same line, reason why the error message very explicitly told you "[COLOR=#000000][FONT=&quot]'dpkg': no such file or directory".[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-01-08
I suggest you chroot in, then run the command separately.

---

### Post by deadflowr on 2021-01-08
Nothing in the suggested repairs for your boot repair summary suggests to run that chroot command.
Boot repair says you're in EFI mode but have no ESP partition.
It also says to try booting in legacy mode.
Either the ESP partition was corrupted, making it unidentifiable,
or you somehow reset the system to boot into EFI when it was set not to.

---

### Post by dniven on 2021-01-08
Yup, I overlooked that error message ([COLOR=#000000]Boot repair says you're in EFI mode but have no ESP partition)[/COLOR]. I'll explore how to reinstall EFI instead.

---

