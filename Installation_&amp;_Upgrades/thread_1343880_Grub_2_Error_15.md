---
title: "Grub 2 Error 15"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by pearldrums on 2009-12-02
hey, can anyone point me in the direction for more info on Error 15 when upgrading to grub2. I've installed grub 2, and successfully chainloaded ubuntu and windows from it. But after I run upgrade-from-grub-legacy and reboot it gives me error 15: file not found. Then I flop in my ubuntu CD and re-install grub and do it all over again.

Heres the output when I re-install grub:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdb
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ 

```

---

### Post by darkod on 2009-12-02
You say you installed grub2 and after that you say you are running upgrade-from-grub-legacy. That command is used for upgrade from grub1 to grub2. If you already had/have grub2 installed no need to run anything like that.

---

### Post by Ilalmi on 2009-12-02
Are you sure that your bios uses the second harddisk (sdb) to boot? Have you tried to install grub to sda?

---

### Post by phillw on 2009-12-02
Been there got the t-shirt - lol

[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29](https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29)

Has the answer

Regards,

Phill.

---

### Post by pearldrums on 2009-12-02
> **Ilalmi said:**
> Are you sure that your bios uses the second harddisk (sdb) to boot? Have you tried to install grub to sda?

Absolutely not, I thought I was supposed to list the HD that I was installing grub on. I think this should remedy the problem.

---

