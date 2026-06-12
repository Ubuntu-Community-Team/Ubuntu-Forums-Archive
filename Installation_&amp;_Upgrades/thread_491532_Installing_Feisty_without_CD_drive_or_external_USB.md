---
title: "Installing Feisty without CD drive or external USB CD drive?"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by hamdodger on 2007-07-03
Is there a way to boot Ubuntu from the Internet, without a CD drive?  

I'm assuming there's a way to create an Ubuntu install loader on a USB stick and then having that install loader point to an URL that has the installation binaries for Feisty.

Any recommendations?

---

### Post by zek725 on 2007-07-03
```
mount -o loop -t iso9660 <isofilename> <mountpoint>
```

detailed syntax from [UbuntuGuide.Org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning")

still looking for the exact thread I've used as reference in my Edgy-Feisty upgrade using mounted ISO.

---

### Post by logos34 on 2007-07-03
[https://help.ubuntu.com/community/Installation/WithFloppies?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/WithFloppies?highlight=%28installation%29)
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28installation%29)

---

### Post by zek725 on 2007-07-03
Here are some clues on how to do that: (from Sidux) [http://manual.sidux.com/en/hd-install-opts-en.htm#fromiso](http://manual.sidux.com/en/hd-install-opts-en.htm#fromiso)

---

