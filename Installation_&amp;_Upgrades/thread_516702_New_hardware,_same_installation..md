---
title: "New hardware, same installation."
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by mattixtech on 2007-08-03
I just switched my ubuntu server over to new hardware. I moved the hard drive with the installation on it to a new pc. Now it is hanging on 

"Loading, please wait..."

At first it gave this error

"usb 2-2: device descriptor read/all, error -62"

The old machine was a sempron 3200+ , the new one is an athlon x2 3600+, it's also using an asus board now rather then a gigabyte, both were AM2.

Is there a command I need to add to the boot menu to make it auto detect all the new hardware or something?

Any help is appreciated.. thanks.

---

### Post by Pumalite on 2007-08-03
New hardware requires new install. Kernel and modules are setup for your old hardware.

---

### Post by mattixtech on 2007-08-03
> **Pumalite said:**
> New hardware requires new install. Kernel and modules are setup for your old hardware.

Is there a way to do a new install but keep all the old settings and files?

---

### Post by Pumalite on 2007-08-03
Backup /home to CD's or DVD's or external drive. You can also do a new install saving /home partition. Just choose 'no format'

---

### Post by Steve1961 on 2007-08-03
> **Pumalite said:**
> New hardware requires new install. Kernel and modules are setup for your old hardware.

I didn't think that was necessary with Linux - it should detect the new hardware and install necessary modules when booting.  I've just upgraded my processor and had no problems.  I've even changed a motherboard on another ubuntu PC and then booted without issue and detected everything correctly.

---

### Post by HeavyAl on 2007-08-03
This is one of the really cool things about Linux. On windows your settings are scattered all over the machine but on Linux you can simply backup your home directory and reinstall and then put your home directory back where it was and you will retain all the settings you had before.

One way of making this procedure easier on yourself is to actually setup your install to use a separate hard drive for your home partition, that way you never have to back anything up (well, except for sanity purposes, things do occasionally go wrong) just set your new install up so that it points to the old drive.

---

### Post by mattixtech on 2007-08-03
> **Steve1961 said:**
> I didn't think that was necessary with Linux - it should detect the new hardware and install necessary modules when booting.  I've just upgraded my processor and had no problems.  I've even changed a motherboard on another ubuntu PC and then booted without issue and detected everything correctly.

Yeah... I thought that is how it worked too... I tried booting into recovery mode and it hangs when it discovers the keyboard. It looked like it was detecting all the new stuff though..

---

### Post by mattixtech on 2007-08-03
> **HeavyAl said:**
> This is one of the really cool things about Linux. On windows your settings are scattered all over the machine but on Linux you can simply backup your home directory and reinstall and then put your home directory back where it was and you will retain all the settings you had before.

One way of making this procedure easier on yourself is to actually setup your install to use a separate hard drive for your home partition, that way you never have to back anything up (well, except for sanity purposes, things do occasionally go wrong) just set your new install up so that it points to the old drive.

My home directory is several hundred GB. I was using this machine as a file server and webmin server. All of the shared files were in the /home dir. There's no way to just give it a boot option to configure all the new hardware? I always thought you could just swap out hardware and linux would auto detect it on boot.

---

