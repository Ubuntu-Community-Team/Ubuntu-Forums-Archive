---
title: "Lost Dual Boot"
date: 2019-02-23
forum: Installation &amp; Upgrades
---

### Post by Frantic_Earthling on 2019-02-23
I have just done something very stupid: erasing Windows by mistake.
Please do not ask me the whys and wherefores. I already feel stupid enough.
I have (had!) a laptop with dual boot Win 10/Ubuntu 18.04 LTS.

I have just re-installed Windows and loo and behold, I lost my dual boot, which I sort of expected :(
My computer starts directly in Windows, however, my Ubuntu 18.04 LTS and its partitions are still there, untouched.

I am sure the question has been asked a thousand times, but I mostly find the opposite :(  People booting with Ubuntu who have lost the ability to boot into Windows.

How can I repair the dual boot procedure ?

Can anyone point me in the right direction?

Would Boot Repair do the trick?

---

### Post by oldfred on 2019-02-23
Are both systems in UEFI boot mode? Or both old BIOS boot mode?
If UEFI, you should be able to use UEFI boot menu to choose the ubuntu entry. And then use efibootmgr or your UEFI to change boot order to make Ubuntu first.
If new install of Windows it will have fast start up on, and you need that off for grub to find the new install, but if ESP not reformatted, grub may just work, but fast start still has to be off.  Grub only boots working Windows.

If ESP - efi system partition reformatted (it should not have been) then you would need Boot-Repair's advanced mode the total reinstall of grub.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Frantic_Earthling on 2019-02-23
Sounds so simple when you know! 
Both systems are in UEFI mode. ESP was not reformatted.
Thanks to you, I got my Bionic back, along with Windoze.

Many thanks! :D

---

