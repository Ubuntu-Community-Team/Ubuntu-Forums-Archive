---
title: "acpi problems"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Jkt610 on 2008-05-26
Hi, for some reason, every time I try to start up ubuntu, I get an acpi error. I used wubi to install ubuntu. In the boot menu, it gives me two options, Vista or Ubuntu. After choosing ubuntu, I get an ACPI error after a few seconds. I then proceeded to start up ubuntu without ACPI and I receive another error... I'm not too familiar with what ACPI is but is there a way to fix this problem so there I don't get an error every time?

---

### Post by ibutho on 2008-05-26
ACPI = advanced configuration and power interface. Linux sometimes does not play along nicely with ACPI on some hardware configurations. You could  edit /boot/grub/menu.lst and look for an entry like the one below
```
title           Ubuntu 8.04, kernel 2.6.24-17-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-server root=UUID=5ce40ddb-bbb4-4b21-9c4e-4b9003ad52d6 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-server

```
Edit the kernel line and add the part **acpi=off** at the end e.g.
```
title           Ubuntu 8.04, kernel 2.6.24-17-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-server root=UUID=5ce40ddb-bbb4-4b21-9c4e-4b9003ad52d6 ro quiet splash acpi=off
initrd          /boot/initrd.img-2.6.24-17-server
```

---

### Post by Jkt610 on 2008-05-26
Ok I will try that but how do I get to that?

---

### Post by ibutho on 2008-05-26
There are several ways e.g. Applications -> Terminal -> sudo gedit /boot/grub/menu.lst.

---

### Post by Jkt610 on 2008-05-26
**But I can't even get to the desktop. Ubuntu doesn't load up for me. Applications -> Terminal is accessed through the desktop is it not? As soon as I try loading Ubuntu, all I get is...**

[  xx.xxxxxx]ACPI:EC:acpi_ec_wait timeout, status=0,expect_event=1
[  xx.xxxxxx]ACPI:EC:read timeout,command=128

**and it then locks up in this screen...**


**When I try booting with ACPI off, I get this...**

[  0.000000]Buffer I/O error on device sda2, logical black 471605xx
[B]
It repeats this about 15 times and then gives me this...[/B]

BusyBox v1.1.1 (Debian 1:1.1.3-5ubuntu12) Built-in shell(ash)
Enter 'help' for a list of built in commands.
(initramfs)

---

### Post by ibutho on 2008-05-27
In that case, at the GRUB boot screen, enter E, navigate to the kernel line and press E again. After that add **acpi=off** to the end of the line, then ENTER and B to boot.

---

### Post by Handssolow on 2008-05-27
I have been having a problem with acpi probably first in February with 2.6.22-14-generic which wouldn't boot, instead I had to drop back to use 2.6.20-16-generic until Hardy came along. After the Hardy upgrade I was unable to boot again until I discovered that it was an acpi issue. Adding pci=noacpi to the kernel line worked.

With today's update linux-generic (2.6.24.16.18 ) to 2.6.24.17.19 I was unable to boot again until I added pci=noacpi as shown here-

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro quiet splash pci=noacpi
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

I've an Asrock 939 Dual-Vsta desktop mobo, dual cpu processors an AMD Athlon 64 x2 4200+ and booting with one IDE drive with only the Hardy 8.04 OS.

Connecting instead my Sata with 64 bit Heron, I need not add pci=noacpi for it to boot neither is there any problem with shut down. Running 32 bit Heron I have to manually turn off the power. So adding pci=noacpi solves the problem with 32 bit not booting but then my PC wont power down automatically.

---

