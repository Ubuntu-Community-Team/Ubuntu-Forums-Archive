---
title: "Nvidia driver failure after update"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by canvas0 on 2024-02-24
Hello all.

After upgrading my os to Ubuntu 22.04.4 my system was working fine until I tried updating software (through software updates) and my graphics card driver. Now The driver keeps failing and reverting back to X.Org x server, even after reverting to the previous one.

At boot console returns this:

```

idevisdcz: clean, 870460/8003584 files, 27005868/32000000 blocks
[DEPEND] Dependency failed for SSSD NSS seryice responder socket
[DEPEND] Dependency failed for SSSD.itoFS Service responder socket
[DEPEND] Dependency failed for SSSD PAC Service responder socket
[DEPEND] Dependency failed for SSSD.vice responder private socket
[DEPEND] Dependency failed for SSSD PAN Service responder socket
[DEPEND] Dependency failed for SSSD SSH Service responder socket
[DEPEND] Dependency failed for SSSD Sudo Service responder socket
```

Not sure it's related, but while trying to install amd pro drivers the installer script returned this error:

```

E: Package 'linux-headers-5.13.0-37-generic' has no installation candidate

```

and when I run ```
ls -l /usr/src/linux-headers-$(uname -r)
``` I get a "No such file or directory" error.

Did I mess up?


My system:

  Kernel: 5.13.0-37-generic x86_64 bits: 64 compiler: gcc v: 9.4.0
    Desktop: Cinnamon 5.2.7 tk: GTK 3.24.33 vt: 2 dm: GDM3 42.0
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
  Device-1: NVIDIA GM200 [GeForce GTX 980 Ti] vendor: Micro-Star MSI

---

### Post by ubfan1 on 2024-02-24
Where did you get the 5.13 kernel?  Ubuntu 22.04 shipped with the 5.15 kernel, updated to 5.19, 6.2, and now 6.5.

---

### Post by canvas0 on 2024-02-24
> **ubfan1 said:**
> Where did you get the 5.13 kernel?  Ubuntu 22.04 shipped with the 5.15 kernel, updated to 5.19, 6.2, and now 6.5.

Upgraded from Ubuntu 20.04 using Canonical's instructions.

[https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start](https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start)

---

### Post by ubfan1 on 2024-02-24
Have you restarted the system after the upgrade?  I'd expect the default would be the 6.5 kernel, you can check in /boot to see which kernels you have. /boot/grub/grub.cfg should have the 6.5 kernel as the default boot item.

---

### Post by canvas0 on 2024-02-24
> **ubfan1 said:**
> Have you restarted the system after the upgrade?  I'd expect the default would be the 6.5 kernel, you can check in /boot to see which kernels you have. /boot/grub/grub.cfg should have the 6.5 kernel as the default boot item.

Thank you. That was the problem.

After running `sudo update-grub` system booted with the new kernel.

---

