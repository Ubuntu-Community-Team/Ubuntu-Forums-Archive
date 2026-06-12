---
title: "Ubuntu Installer and/or LiveCD goes to Black Screen and USB Stick goes dead"
date: 2018-09-12
forum: Installation &amp; Upgrades
---

### Post by markackerman8@gmail.com on 2018-09-12
The title says it all.

I have been helping others for MANY years and Now I need some help.  I have installed ubuntu Variants on over 100 computers and today I can't install it on my new cutting edge ...

Brand new Hp Omen X 17-an0xx
Other have had success with this same model with adding nomodeset in 'e' for editing  grub - but sorry to say ... no luck for me.

It is a new NVMe awesome 1 TB HDD with Windows 10 re-installed on it.  The same one I put on my twins laptop (Asus ROG) and no problems installing 18.04 on it.  Running AWESOMELY!

I will probable find a solution after a nights sleep, but for now I am at a complete loss.  I even tried the "debian installer" with the same problem. 

And of course I have disabled "Secure Boot".

If I am having these troubles - I am SURE many others are too - or soon will be ... 

So please offer suggestions for me and all those others :KS

Thanks in advance,

Always Trying to Help, Mark
Sleep Well

---

### Post by gunna999 on 2018-09-12
Same boat. Ive been installing ubuntu off a usb thumbdrive for many years without issues. Did my pc a month ago no probs. Today I used the same thumdrive to install bionic onto a m8s pc and I have problems. Funny thing is my pc and the m8s pc are very similar builds, same motherboard, ram, & hdd, so Im scratching my head a little what would be the problem.

The install gets to the splash screen showing the beaver and then nothing else happens. I wiped the startup usb with gparted, downloaded the 1.8gb file again, used the startup disk creator in trusty, and tried the installation again. Same result it just freezes up at the very first splash screen.

---

### Post by markackerman8@gmail.com on 2018-09-12
I just solved my own problem - WooHoo

I hope it helps you.
/
An old trick for newer laptops with UEFI GPT partitions is to install Ubuntu in Legacy Mode.

So for the heck of it I tried it, even with my uefi Usb stick it WORKED!

I hope it helps.

Ubuntu now starting up in 12 seconds, and my old M.2 512 GB PCIe is reading 250 MB/s Faster at 750 instead of 500 which it was rated for WOW

and 60 GB of home copied in less than 60 seconds - Cool.  NVMe PCIe SSDs ROCK!

Always trying to spread the Good word, Mark

---

### Post by sudodus on 2018-09-12
Congratulations Mark, and thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by sudodus on 2018-09-12
> **gunna999 said:**
> ... used the startup disk creator in trusty, and tried the installation again. Same result it just freezes up at the very first splash screen.

The Ubuntu Startup Disk Creator in Trusty is an extracting tool, affected by several bugs. It was replaced with a new and reliable version, a cloning tool, in Xenial (Ubuntu 16.04 LTS). This cloning tool is also used in later versions (including 18.04 LTS).

If you want to create a USB boot drive in Trusty, you have better chances to succeed, if you use

- **Disks** alias gnome-disks, or

- [**mkusb**](https://help.ubuntu.com/community/mkusb)

See also this link and links from it, [Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

