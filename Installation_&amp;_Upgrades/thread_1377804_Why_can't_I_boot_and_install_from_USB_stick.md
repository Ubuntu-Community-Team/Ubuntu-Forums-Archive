---
title: "Why can't I boot and install from USB stick?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by mozilla2004 on 2010-01-10
I'm trying to install Ubuntu 9.10 from USB stick.  I used System>Admin>USB Start up Disk Creator and a 9.10 .ISO version to create the bootable USB stick.  

When I plug my USB key into my computer, my computer doesn't boot from it.   I tried on several other computers and none of them boot from my USB key.   The bios settings on all my computers boot from removable media first.

I repeated the above steps with a different USB key and I still can't boot from the USB key.  When I browse the USB key directories, I can see all the necessary files to install ubuntu.

Last year, I didn't have trouble installing ubuntu 9.04 from USB key.  Not sure what I'm doing wrong this time.

Can anyone tell me how to trouble shoot this problem?

---

### Post by phillw on 2010-01-10
Hi & welcome,

a couple of possibilities - in the boot from removable media, are there any other options, such as boot from usb hard drive, boot from usb memory stick etc ?

Before you bash your brains in - try carrying out this test --> [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)   

When you have a setting that boots from the memory stick, you should find the install goes smoothly.

Regards,

Phill.

---

### Post by mozilla2004 on 2010-01-10
> **phillw said:**
> Hi & welcome,

a couple of possibilities - in the boot from removable media, are there any other options, such as boot from usb hard drive, boot from usb memory stick etc ?

Before you bash your brains in - try carrying out this test --> [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)   

When you have a setting that boots from the memory stick, you should find the install goes smoothly.

Regards,

Phill.

In the BIOS boot from removable media, i don't see any other options such as boot from USB HD or USB Memory stick.   The only options I see are enable and disable, i set it to enable.

I don't have windows installed on any of my computers....so I can't run the boot compatibility test on pendrivelinux.com unless I get wine or install vmware for windows.  Is there a different way to do the boot compatibility test from linux?

---

### Post by C.S.Cameron on 2010-01-10
In bios do you see your USB stick listed under hard drives? If so select it as first.

---

### Post by darkod on 2010-01-10
> **mozilla2004 said:**
> In the BIOS boot from removable media, i don't see any other options such as boot from USB HD or USB Memory stick.   The only options I see are enable and disable, i set it to enable.

I don't have windows installed on any of my computers....so I can't run the boot compatibility test on pendrivelinux.com unless I get wine or install vmware for windows.  Is there a different way to do the boot compatibility test from linux?

You may need to have the option enabled to be able to boot from usb stick but you will probably still need to find the boot device order (usually in Advanced BIOS settings) and make the USB HDD (or similar device) to be before the internal HDD.
Even though usb hdd and usb stick is not the same, on both my netbook and desktop the correct option in BIOS is called USB HDD.

---

### Post by mozilla2004 on 2010-01-10
> **darkod said:**
> You may need to have the option enabled to be able to boot from usb stick but you will probably still need to find the boot device order (usually in Advanced BIOS settings) and make the USB HDD (or similar device) to be before the internal HDD.
Even though usb hdd and usb stick is not the same, on both my netbook and desktop the correct option in BIOS is called USB HDD.

thanks darkod, cameron and philw,  it worked!  you guys so smart!

---

