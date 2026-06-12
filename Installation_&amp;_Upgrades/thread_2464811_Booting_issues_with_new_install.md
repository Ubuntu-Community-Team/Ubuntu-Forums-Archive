---
title: "Booting issues with new install"
date: 2021-07-12
forum: Installation &amp; Upgrades
---

### Post by sambrien on 2021-07-12
Greetings everyone,

I am having some issues booting my new Kubuntu install. I installed a first time successfully. Then, I reinstalled to change some partition settings and error messages appeared at boot. Now, even after I did a secure erase of my hard drive and reinstalled Kubuntu with default settings it doesn't boot when I turn the computer on.

I can access grub by pressing esc and boot in recovery mode, but I would like to be able to boot normally. In case it is useful, I have run the boot-repair tool and got the following log: [https://paste.ubuntu.com/p/B9mfKm59M6/](https://paste.ubuntu.com/p/B9mfKm59M6/)

I have installed Kubuntu 21.04, have a MSI B450I motherboard and an Nvidia graphic card, in case it matters.

Thank you for any help and suggestions!

---

### Post by ubfan1 on 2021-07-13
With Nvidia, secure boot should be disabled.  Then first boot after install (assuming the Nvidia drivers were not installed), use the "nomodeset" option where the "splash quiet" words are on the linux boot line.  Then you can install the Nvidia proprietary drivers.  Since Recovery mode works, I assume you are using the nouveau driver successfully.  Also check that the firrmware is up to date for the motherboard.

---

### Post by sambrien on 2021-07-15
Hi Ubfan1,

I disabled secure boot, removed Nvidia drivers and reinstalled them and I can now boot normally. Thank you for your suggestions!

To reinstall the Nvidia drivers, I used the following code from [this thread]("https://askubuntu.com/questions/1305871/why-am-i-only-able-to-boot-ubuntu-from-recovery-mode"):

```

sudo apt-get install linux-headers-generic
sudo dkms remove nvidia
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot 
```

---

