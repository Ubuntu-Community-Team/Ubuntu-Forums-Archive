---
title: "Getting grub rescue&gt;prompt after upgrading from 10.4 to 10.10"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by kamalrajonnet on 2010-10-23
Hello Everyone,

I had ubuntu 10.4 (through wubi) in my windows 7 OS. Yesterday I tried to upgrade to ubuntu 10.10 and the installation was successful. But after the reboot it shows only grub rescue> prompt.

I have attached boot_info_script result also.

Please do the needful.

Thanks
Kamalraj

---

### Post by bcbc on 2010-10-23
You have grub installed to /dev/sdb 
With wubi installs you should have windows as the bootloader. Replace it from windows repair command line (bootrec.exe /fixmbr) or install lilo to /dev/sdb:

```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
Ignore errors regarding booting linux. Reboot. Should work properly after that.

---

### Post by kamalrajonnet on 2010-10-23
Hi,

Thank you very much. Using LILO solved my problem.

Going to start using ubuntu 10.10 :-).

Thanks
Kamalraj

---

