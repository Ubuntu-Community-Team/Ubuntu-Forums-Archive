---
title: "Error Installing Kernel"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by job2600 on 2005-10-18
Hi,

I'm installing Ubuntu Breezy Badger 5.10 from the amd64 DVD iso. (MD5 verified!)

I get the following error message:
```
[!!] Install the base system
Unable to install the selected kernel
An error was returned while trying to install the kernel into the target system.

Kernel package: 'linux-amd64-k8'.

Check /target/var/log/bootstrap.log for the details.
```

Details:

```
Unpacking linux-amd64-k8 (from .../linux-amd64-k8_2.6.12.16_amd64.deb)...
Errors were encountered while processing:
/cdrom/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-9-amd64-k8_2.6.12-9.23_amd64.deb
E: Sub-process /usr/bin/dpkg returned and error code(1)
```

Any ideas?

---

### Post by filemanager on 2005-10-20
I have the same problem.

---

### Post by job2600 on 2005-10-20
[QUOTE=filemanager]I have the same problem.[/QUOTE]

I also tried downloading just the 64 bit cd installer iso but I get the same error. I also tried selecting different 64 bit kernel options (e.g. smp, general etc.) but they all return the same error.

---

### Post by filemanager on 2005-10-20
[QUOTE=job2600]I also tried downloading just the 64 bit cd installer iso but I get the same error. I also tried selecting different 64 bit kernel options (e.g. smp, general etc.) but they all return the same error.[/QUOTE]
I did the same thing. I thought maybe the CD I burnt the image to was bad or something, but haven't burnt another one yet to test that theory.

---

### Post by filemanager on 2005-10-21
Well I burned the same image to another CD and it installed fine! Now I'm running Breezy, yay :)

---

