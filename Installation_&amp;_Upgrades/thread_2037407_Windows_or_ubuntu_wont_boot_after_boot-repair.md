---
title: "Windows or ubuntu wont boot after boot-repair"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by packt on 2012-08-04
Pre-installed windows 7 then installed ubuntu 120.04 using live CD

Ubuntu did not boot so used boot-repair to fix this problem but it did not work Now it directly boots to BIOS

Here is the summary [http://paste.ubuntu.com/1128869/](http://paste.ubuntu.com/1128869/)

ANY help would be appreciated!

---

### Post by oldfred on 2012-08-04
You have a new UEFI system but have grub installed both as BIOS/mbr and efi. Not sure which way you are trying to boot. 

Script does not show windows files in efi partition but since Boot-repair added the new corrected entries, they must be there. The first boot entry in your grub menu is the BIOS/MBR type Windows entry which does not work with efi, but boot repair added correct Windows  entries at the bottom of the menu. One of those should work.

Are you trying to boot with BIOS mode or UEFI? Do you get grub menu from UEFI boot?

If you get grub menu try  last Windows entries not first. And then issue with Ubuntu may be video related.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by packt on 2012-08-04
the problem is i am not able to boot at all!
as soon as the system starts it goes into the BIOS screen and nothing to do from there
i keep trying different methods by booting from the live cd and running boot-repair but still no luck

i am in a real pickle here!

---

### Post by darkod on 2012-08-04
Yeah, but even if the system doesn't boot right now you need to know whether you have UEFI boot or not. In fact, if you are using UEFI boot you need to boot the install media in UEFI mode when installing the OS.

Does it open the BIOS so you can add or create or modify something in the UEFI boot menu? I don't work with UEFI but it seems you create boot entries in some UEFI manager that might be part of the BIOS (or it looks like that).

---

### Post by packt on 2012-08-04
I dont work much with UEFI either but am really getting annoyed because all i wanted to do was dual boot! Haha
I have a option in the BIOS showing me weather i want to enable UEFI boot or not , but then what? :|

When i completed the repair-boot in ubuntu
it asked me to "add boot entry sda1the grub*.efi in sda1

But i am clueless on what to do.

I CANNOT in anyway reformat.

PS - i have Asus U47VC running the 3rd generation processor.

I am really eager to get my dual boot working and am really glad for all your help.
need to fix it asap!

---

### Post by oldfred on 2012-08-04
With UEFI boot enabled, are you able to boot?

Someone posted this on how to rename an efi entry, but it was the way to show from UEFI what entries you have. But each vendor does UEFI different.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 



---

### Post by packt on 2012-08-04
I am not able to boot with UEFI enabled or disabled i tried both.

And i am allowed to add boot entries but i wont know where to start.

As far as i can tell my UEFI boot options are very limited.

Usually UEFI interfaces are not in anyway similar to the BIOS.
But it's different here.

---

### Post by oldfred on 2012-08-04
Do you have the latest UEFI/BIOS version installed?

I could only find one screen from your manual on line and it looks like you have a lot of settings. Some that do not necessary seem important may be but I do not know your system. 

With the c version you will also have video issues and need to one use one.
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

These are different model Asus but may have some similarities. 

Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.

efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

---

### Post by packt on 2012-08-05
Even if i do update it to the latest UEFI , how will that help me?

i get NO EFI boot options when i go into gparted , lol.

---

### Post by oldfred on 2012-08-05
How are you getting to gparted, that is long after you boot. Do you mean grub2? 

And are you getting the grub menu then? If so and Ubuntu does not boot it is the video issue.

---

