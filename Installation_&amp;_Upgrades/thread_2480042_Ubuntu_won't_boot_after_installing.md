---
title: "Ubuntu won't boot after installing"
date: 2022-10-17
forum: Installation &amp; Upgrades
---

### Post by powlow3701 on 2022-10-17
hi, same problem here.

May you help me please ?

[https://paste.ubuntu.com/p/tBRMGRyDSt/](https://paste.ubuntu.com/p/tBRMGRyDSt/)

Thx a lot for your help :)

---

### Post by yancek on 2022-10-17
powlow371.  The moderators generally prefer you start your own thread but it is up to them to change it.

Look at line 70 of boot repair.  It shows you booted the usb with boot repair in Legacy mode.  You have both a bios_boot and efi partition.  The bios-boot partition is only needed if you do a Legacy install on a GPT drive.  You also have an EFI install.  Have you disabled Legacy in the BIOS firmware and tried to boot?  What results?  You don't need both a biod_boot and an EFI partition although that isn't necessarily a problem.

I don't see any obvious errors in boot repair so try booting Legacy as well as EFI by changing the BIOS and see what results.

---

### Post by coffeecat on 2022-10-17
Post and reply moved to its own thread.

@powlow3701, please start your own threads. Helping more than the OP on a thread becomes confusing. You can always link back to another thread if you think it is relevant.

---

### Post by powlow3701 on 2022-10-17
Thx @coffeecat to move my post in right place :)

And sorry for that, it's my first time question ^^, i'm a virgin xD.

@yancek thx for your quick answer :).

I'm a little bit lost. My laptop is hold and i don't found the [COLOR=#000000]disabled Legacy  option. 

[/COLOR]I switch my HD to MBR before installing ubuntu. is that a mistake ?

I think the BIOS on my laptop is Legacy and it only work with MBR partition. am i right ?

During the installation i didn't see any option to chose Legacy or UEFI parameters.

Sry for my approximate english (i try my best).

---

### Post by tea for one on 2022-10-17
> **powlow3701 said:**
> I think the BIOS on my laptop is Legacy and it only work with MBR partition. am i right ?
Line 70 - The firmware seems EFI-compatible

Have you had a good look at all the settings in your BIOS (or UEFI)?

---

### Post by tea for one on 2022-10-17
> **powlow3701 said:**
> During the installation i didn't see any option to chose Legacy or UEFI parameters.
You choose the mode (i.e. Legacy or UEFI) when you boot the installation USB.
Does this attached image help?

---

### Post by powlow3701 on 2022-10-17
Hi @tea for one,

I haven't this option in my bios (F2) and boot options (F12)

[https://i.postimg.cc/0yc4Qq9T/311064315-1159523324946052-8661286642861561087-n.jpg](https://i.postimg.cc/0yc4Qq9T/311064315-1159523324946052-8661286642861561087-n.jpg)

[https://i.postimg.cc/dVx9pQsV/311897225-5557332591009668-6465804174883773238-n.jpg](https://i.postimg.cc/dVx9pQsV/311897225-5557332591009668-6465804174883773238-n.jpg)

---

### Post by powlow3701 on 2022-10-17
If it help i send you my advanced parameters available in bios

[https://i.postimg.cc/RZ6t37mv/272667544-1317759775634007-856156841013789280-n.jpg](https://i.postimg.cc/RZ6t37mv/272667544-1317759775634007-856156841013789280-n.jpg)

---

### Post by tea for one on 2022-10-17
In post 4, you mentioned that your laptop is old.
In posts 7 and 8, there doesn't seem to be any sign of UEFI in your images.

If you are certain that your PC is not EFI compatible, then Ubuntu may not be suitable for your device.
Perhaps try a different member of the Ubuntu family, such as Lubuntu [https://lubuntu.me/](https://lubuntu.me/)

---

### Post by yancek on 2022-10-17
It would likely be under Boot Options, any reference to UEFI?

---

### Post by powlow3701 on 2022-10-18
hi, zero ref to UEFI under boot options. 

I'll try Lubuntu and coming back to give you my feedback :)

Again thx for helping

---

