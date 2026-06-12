---
title: "Positivo BGH T201X Problem EFI - Ubuntu no Boot"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by yoeloco on 2016-08-05
before I apologize for the poor quality of my English.
about 8 years ago I'm using ubuntu, and about 2've done the final migration. and I also think I have a relatively good management Ubuntu but what has happened to me I can not solve.

[http://fs5.directupload.net/images/160318/3ywa8umh.jpg](http://fs5.directupload.net/images/160318/3ywa8umh.jpg)

A few days ago I bought a tablet 2 in 1 postive BGH t201x that comes with Windows 10.

Then I did the following.

1- Ubunutu downloaded and created with Unetbootin
2- disable Secure Boot and put as first boot from USB
3- removed from the database effi operating systems bloqueados-
4- I looked for any other option on the start and found nothing.
5- Save the changes and restart
6- For safety press F11 and select Boot from USB
7- black screen and within seconds begins windows-

I replaced pendrive, look for alternative configurations, I tried with  Rufus, I tried to install windows xp but nothing makes the tablet boot  from an external medium.

I do not know what else I can do. linux and I need to work ...

Thank you

---

### Post by wildmanne39 on 2016-08-06
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by Pumba! on 2016-08-06
Does the BIOS allow you to de-select your internal drive so that it only can boot from the pendrive? What's the output?

----
Te permite deshabilitar como opción de booteo en el BIOS al disco interno? De esa manera es posible que veas el error por el que no bootea el pendrive.

---

### Post by oldfred on 2016-08-07
In #3 did you say you erased UEFI keys? You do not want to do that. If Secure boot, Ubuntu uses the default Microsoft keys. You should have a restore defaults somewhere.

Is this one of the lightweight systems that uses 32 bit UEFI even though 64 bit? 
They created those to restrict system to Windows only as back when they first did it, Linux did not have nor want to create a 32 bit UEFI (as it just is not a good idea).
But there is a 32 bit Linux UEFI and it does require some effort to configure, but now easier also.

Or is this have an Intel Atom or Bay-Trail chip? Those have the 32 bit UEFI.
Or an AMD system which may have video issues?

---

### Post by yoeloco on 2016-08-07
Thanks for the replies! I'm still trying install ubuntu.

Ok, next time I'll upload image as [COLOR=#000000]thumbnails , [/COLOR]

Bios doesn't allow disable Drives, no configure boot drives, Bios set boot Images... And HD is SSD integrated to motherboard

Yesterday I installed Grub on Efi partition using Grub2Win but I can not boot from iso in SD.
The tablet is a intell and EFI is a American Megatrend and hasn't much options for configure.
I restored default Keys and mounted EFI partition to Copy Efi folder from Ubuntu but didn't boot.
I was reading about this and I believe wich is the problem, but I dont Know Fix.
The problem is:
In efi partition there is /microsoft/Boot/BOOTX64 and /Grub2Win/Boot/BootX64.EFI
if I can copy boot files from ubunutu USB in this partition and set files locantions... maybe boot from USB...?

Become I'll take a few pictures to show the proces....

---

### Post by oldfred on 2016-08-07
The grub is hard coded. So the version on the installer is a very limited version just with whatever is required to boot installer.

The installer also uses /EFI/Boot/bootx64.efi which is the default UEFI boot for all external devices. That is really just a copy of grub. I do not think you can copy to internal ESP and use it to boot.

The copy of /EFI/Boot/bootx64.efi on your system is probably just a copy of Windows .efi boot file. And some systems use that UEFI boot entry to boot, even Windows.

Some systems require you to add a supervisory password in UEFI to open more options. Never lose that password or you may brick system(make unusable).

Some also require in UEFI that you specifically turn on a setting that is allow external device/USB port boot. Many with Secure boot on have that setting, but you may have to turn that on anyway.

---

### Post by yoeloco on 2016-08-07
Hi friends, i go to resign to install ubuntu in this device. 
Here is a link to youtube where show my tablet booting.
[https://www.youtube.com/watch?v=HAfLFYWW0o8](https://www.youtube.com/watch?v=HAfLFYWW0o8)
Become send this post I go to restore the system. Maybe in some time I find the way... wait! :(
Anyway ubuntu is running in my laptop...
Thank Really...

---

