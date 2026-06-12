---
title: "Ubuntu Install Error"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by nautilussoftware on 2007-07-27
Hi;
I am trying to install 

7.04 
on an older machine the machine specs are

dual Penuim IIs, 523meg ram,
A network card
SCSI cards with 2 SCSI drives as foppy and CD Rom.
AMI BIO 1996


I am getting the following error on install from the CD ROM

[0.000000] ACPI: Unable to load RSDP


then the install hangs.

The machine was a gift and has a version of Windows 2000 server running fine on it but I can not get in to the machine due to not having admin rights. 

So WIPE time. 

Ubuntu was my first choice. I also tried Xubuntu and that did not install either and gave me the same error.

Does anyone know what kind of error it is. it's the first thing on the screen after the install is selected.

Any comments on how to fixr or get around this?  ](*,)

thanks
-peter

---

### Post by loserboy on 2007-07-27
you could try to boot with APCI=off parameter, I can't remember how to do it though

---

### Post by merlinus on 2007-07-27
> **loserboy said:**
> you could try to boot with APCI=off parameter, I can't remember how to do it though

Press F6 at the startup menu and add apci=off to the end of the boot parameter line.

-merlin

---

### Post by loserboy on 2007-07-27
will that make it so he will always boot with apci=off or just the one time

---

### Post by merlinus on 2007-07-27
> **loserboy said:**
> will that make it so he will always boot with apci=off or just the one time

If it works, then apci=off can be added to the end of the kernel line in /boot/grub/menu.lst so it will be loaded every time.

-merlin

---

### Post by nautilussoftware on 2007-07-27
thanks guys. I will give it a try tonight or this weekend.

hopefully I can set up an ftp server. I hope that is not too hard to do.
thanks
-pete

---

### Post by nautilussoftware on 2007-07-31
it still will not install and seems to hang after Identifying the first pentium II CPU 

:(


](*,)

---

### Post by openprivacy on 2007-07-31
try "acpi=force"

---

### Post by nautilussoftware on 2007-08-13
Ok;
I had not checked this in a while I will give it a shot this week.
thanks

I'm not a linux expert so things like this are hard. 

I also have a

HP Vectra line Computer. I used to write System BIOS for Phoenix and this is one of the actuall machines I wrote a bios for. I was very surprised to see the screen when I tried to boot it.

However it is a vey old machine and has a 200 mhz CPU and 98 megs of ram. Is there a version of Ubuntu I can use on it. I tried XUbuntu and it would not load on it. So I go too machines that are oddballs but could be used. I hope someone has an answer for this one, thanks :)

-peter

---

