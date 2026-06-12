---
title: "Should boot configuration be automatically updated?"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by tawsi on 2006-03-09
Due to the setup I had at the time I had to leave installation of grub when I installed. 

Should Ubuntu be able to automatically manage updating the grub configuration for new kernels etc? 

If so is there an easy way to set it up to manage my /boot partition (currently running grub from a previous linux setup) post install?

---

### Post by bonzodog on 2006-03-09
try running $sudo update-grub from whichever distro has grub installed.

---

### Post by az on 2006-03-09
It's the installer that detects the other OSes on your box, not grub.  I don't know if you can run the OS prober outside of the installation.

If your grub.conf in the ubuntu /boot directory was created, installing grub from the ubuntu partitoin will handle all the oses if had installed at the time.  Threre is no way that it can handle a kernel upgrade from another install on another partition, though, since the package install scripts for the ubuntu kernel only write to the grub configuration on the current system, and not any other grub on other partitions.  As well, it does not probe the other partitions when you run update-grub.

---

### Post by tawsi on 2006-03-09
[QUOTE=bonzodog]try running $sudo update-grub from whichever distro has grub installed.[/QUOTE]

Thanks, that seems to have done the trick. When apt adds a new kernel is that command automatically run?

I only have Ubuntu installed now so I'm not looking for it to manage another linux install.

---

### Post by az on 2006-03-09
[QUOTE=tawsi]When apt adds a new kernel is that command automatically run?

I only have Ubuntu installed now so I'm not looking for it to manage another linux install.[/QUOTE]

Yes, the kernel package will automatically run update-grub (or any other bootloader you use).  If everything is working, then you won't have to do anything else to keep it working.

---

