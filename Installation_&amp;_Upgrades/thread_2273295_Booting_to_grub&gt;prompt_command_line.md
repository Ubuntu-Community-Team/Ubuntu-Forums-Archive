---
title: "Booting to grub&gt;prompt command line"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by chandra5 on 2015-04-12
Hi everyone 
 I am a new user to Ubuntu. I am having a Lenovo Y50. I recently dual booted windows 8.1 with xubuntu 14.04. My problem is the laptop upon starting is going into grub>prompt rather than going into the grub menu. I am being required to type normal in the grub>prompt and then it shows me the grub menu to boot into windows or linux. I am not sure what has to be done. Please help me out.

The command sudo-update grub gives output as follows:

```
chandra@RamaKrishna-PC:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
chandra@RamaKrishna-PC:~$
```

Chandra

---

### Post by yancek on 2015-04-12
You have windows installed in UEFI mode.  Did you also install Ubuntu UEFI?  If you could boot Ubuntu and go to the site below, download boot repair and run it selecting the option to "Create Bootinfo Summary", post the output here.  Someone familiar with UEFI should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

