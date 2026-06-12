---
title: "I need to run an older version of the Linux kernel when I start up Ubuntu 12.04"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by roffisserver on 2012-05-04
I just upgraded from 11.10 to 12.04 and I have to use an older version of the kernel when I start my computer. When I restarted my computer for the first time it wouldn't bring me to the login screen. Then I restarted it and tried an older version of the kernel and it worked! Does anyone know what the problem would be?

---

### Post by Lenny212 on 2012-05-05
I get the error message "This kernel requires the following features not present on the CPU: pae; Unable to boot - please use a kernel appropriate for your CPU."
How do I use a different kernel? Please keep answer simple, I am not very technical. Thanks

---

### Post by plucky on 2012-05-05
> **Lenny212 said:**
> I get the error message "This kernel requires the following features not present on the CPU: pae; Unable to boot - please use a kernel appropriate for your CPU."
How do I use a different kernel? Please keep answer simple, I am not very technical. Thanks

Download the [Xubuntu ISO](http://cdimage.ubuntu.com/xubuntu/releases/precise/release/) as that uses the non-pae kernel.

Good Luck

---

### Post by plucky on 2012-05-05
> **roffisserver said:**
> I just upgraded from 11.10 to 12.04 and I have to use an older version of the kernel when I start my computer. When I restarted my computer for the first time it wouldn't bring me to the login screen. Then I restarted it and tried an older version of the kernel and it worked! Does anyone know what the problem would be?

Try adding "nomodeset" to the Grub command line.

Install [Grub Customizer](http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer+drs305) and add the nomodeset next to the "quiet splash" in the Grub kernel boot line.

Good Luck

---

### Post by Lenny212 on 2012-05-06
Thanks plucky, worked great. I found out I can also run "sudo apt-get install ubuntu-desktop" in terminal after installing Xubuntu to end up with standard Ubuntu 12.04.

---

