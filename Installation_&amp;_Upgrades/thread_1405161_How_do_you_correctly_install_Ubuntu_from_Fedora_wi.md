---
title: "How do you correctly install Ubuntu from Fedora with livecd tools"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by akvino on 2010-02-12
I tried and tried, but for some reason I can't get ubuntu iso file to correctly inhibit USB as bootable USB. 

I get the first screen, and if I chose to boot from the USB, it complaints that it can't find the kernel image.

I read online instructions on the ubuntu website, and I am familiar with livecd tool as I installed many times Fedora ISO, but for the love of good, is this known problem or am I screwing up somewhere?

---

### Post by darkod on 2010-02-12
> **akvino said:**
> I tried and tried, but for some reason I can't get ubuntu iso file to correctly inhibit USB as bootable USB. 

I get the first screen, and if I chose to boot from the USB, it complaints that it can't find the kernel image.

I read online instructions on the ubuntu website, and I am familiar with livecd tool as I installed many times Fedora ISO, but for the love of good, is this known problem or am I screwing up somewhere?

If you have only Fedora to work with, I'm not sure it can be done because it's different distro. Recently I tried on ubuntu to create live usb from openSUSE ISO, and I couldn't. After selecting the ISO you want to use, it wasn't even getting recognized. With ubuntu ISO, no problem.
If you can get hold of a windows computer it should be easy to create it with unetbootin. There are few things to do to enable the main ubuntu menu instead of unetbootin, so if you need instructions just ask.
I don't know of another way at the moment.

PS. There is unetbootin for linux too so it might work on Fedora but I haven't tried.

---

### Post by akvino on 2010-02-12
> **darkod said:**
> If you have only Fedora to work with, I'm not sure it can be done because it's different distro. Recently I tried on ubuntu to create live usb from openSUSE ISO, and I couldn't. After selecting the ISO you want to use, it wasn't even getting recognized. With ubuntu ISO, no problem.
If you can get hold of a windows computer it should be easy to create it with unetbootin. There are few things to do to enable the main ubuntu menu instead of unetbootin, so if you need instructions just ask.
I don't know of another way at the moment.

PS. There is unetbootin for linux too so it might work on Fedora but I haven't tried.

Thanks, so I wasn't loosing my mind, there really is a problem..

Does anyone know of a way to do this from Fedora (will try windows too, but for crying out loud I am Linux guy, and not BGates Windows 7 puppet.

---

### Post by darkod on 2010-02-12
As I added in the PS, you should be able to install and use unetbootin on fedora too. I know you can install it on ubuntu.

---

### Post by snowpine on 2010-02-12
My suggestions:

1. Burn a CD (the easy way!)
or
2. Use [Unetbootin]("http://unetbootin.sourceforge.net").

---

### Post by falconindy on 2010-02-12
An .iso file (intended for a cd) is not the same as an .img file (intended for a usb drive).

---

### Post by akvino on 2010-02-12
> **falconindy said:**
> An .iso file (intended for a cd) is not the same as an .img file (intended for a usb drive).

Thank you all for suggestions, I will try unetbootin...

As for .iso files, intended for a cd or not, they are the same, they are .iso (image files).

You do not need cd to view contents of the .iso file.

Just crate a mount point say /mountCDname, mount it with -o loop option and you will be able to browse the .iso file.

mount -o loop mycdfile.iso /mountCDname


:-\"

---

### Post by darkod on 2010-02-12
> **akvino said:**
> Thank you all for suggestions, I will try unetbootin...

As for .iso files, intended for a cd or not, they are the same, they are .iso (image files).

You do not need cd to view contents of the .iso file.

Just crate a mount point say /mountCDname, mount it with -o loop option and you will be able to browse the .iso file.

mount -o loop mycdfile.iso /mountCDname


:-\"

In linux you can also just right-click the file and open with Archive Manager. At least it works in ubuntu. I have been able to extract all files or just specific ones like that.

For IMG I agree they are specifically created for usb stick but karmic even for UNR comes as ISO even though it is logical you would use usb stick for installing on netbook (no optical drive).

---

### Post by falconindy on 2010-02-12
> **akvino said:**
> Thank you all for suggestions, I will try unetbootin...

As for .iso files, intended for a cd or not, they are the same, they are .iso (image files).

You do not need cd to view contents of the .iso file.

Just crate a mount point say /mountCDname, mount it with -o loop option and you will be able to browse the .iso file.

mount -o loop mycdfile.iso /mountCDname


:-\"
My point was that you were trying to load an .iso image on a USB drive and wondering why it didn't work. I gave you an explanation.

---

