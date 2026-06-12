---
title: "When Reinstalling Windows On A Dual Partition With Ubuntu"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by 3246251196 on 2012-08-21
Given a dual partition of Ubuntu 12.04 and Windows 7 - both 64 bit operating systems and a working version of GRUB: I need to be reminded of what will happen upon reinstallation of Windows 7 on the Windows partition in terms of GRUB.

Will GRUB be wiped?

I am concerned about this. I know that GRUB is installed on SDA currently, and the only way I could get it to be installed on SDA was through the process of firstly installing 10.10 selecting SDA from the Bootloader drop down. For someone reason I could not select SDA when using 12.04;

In summary:

1- Will GRUB be wiped?
2- If so, can I FORCE grub to be installed to SDA /boot no matter what?

---

### Post by darkod on 2012-08-21
Yes, installing windows will install its bootloader on the MBR of the disk wiping grub2.

But your ubuntu is still there and reinstalling grub2 to the MBR is very easy using the ubuntu cd in live mode.

Basically, right now, before reinstalling windows, make sure to note down your / partition. You can see them mounted with:
```
df -h
```

In the list that shows, lets assume your / is /dev/sda5.

After windows is installed and grub2 is gone, all you need to do is boot with the same version of ubuntu cd into live mode, open terminal and run:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If your / is not /dev/sda5 (partition #5), just modify the first command and that's it. In the second command it stays '/dev/sda' without any number because that's the destination where you want grub2 installed which is the MBR of the disk.

---

### Post by 3246251196 on 2012-08-21
> **darkod said:**
> Yes, installing windows will install its bootloader on the MBR of the disk wiping grub2.

But your ubuntu is still there and reinstalling grub2 to the MBR is very easy using the ubuntu cd in live mode.

Basically, right now, before reinstalling windows, make sure to note down your / partition. You can see them mounted with:
```
df -h
```In the list that shows, lets assume your / is /dev/sda5.

After windows is installed and grub2 is gone, all you need to do is boot with the same version of ubuntu cd into live mode, open terminal and run:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```If your / is not /dev/sda5 (partition #5), just modify the first command and that's it. In the second command it stays '/dev/sda' without any number because that's the destination where you want grub2 installed which is the MBR of the disk.

Thanks.

---

