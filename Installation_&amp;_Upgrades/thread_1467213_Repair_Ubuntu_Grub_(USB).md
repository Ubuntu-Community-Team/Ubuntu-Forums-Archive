---
title: "Repair Ubuntu Grub (USB)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by SilentPirate007 on 2010-04-30
Hello all,

I had been running ubuntu 9.03 for quite some time, but for school I needed windows, so after installing windows on a free'd partition, it will not give me the ubuntu boot option and loads staright into windows(vista)[typical windows]. I am aware that one is able to repair it with an ubuntu boot disk, but my dvd-rom isn't functioning.

My question is, is it possible to repair it with a USB stick instead?

Many thanks--

---

### Post by carl4926 on 2010-04-30
Do you mean Ubuntu 9.04?

Yes, repair grub from usb is possible

Use unetbootin to write Ubuntu to a usb drive and boot from it. Assume you have USB booting?!
then follow this:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by SilentPirate007 on 2010-04-30
> **carl4926 said:**
> Do you mean Ubuntu 9.04?

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
 I haven't used the verison installed on my PC for quite some time now, but I thought it was 9.03

Anyway, thanks for your responce -- I'll give it a shot

---

### Post by SilentPirate007 on 2010-05-01
Well everything is working as it should be again...

Many thanks for your help again carl4926

---

### Post by carl4926 on 2010-05-01
> **SilentPirate007 said:**
> Well everything is working as it should be again...

Many thanks for your help again carl4926

Good to hear.
Well done!

---

### Post by theHands on 2012-03-05
> **carl4926 said:**
> Do you mean Ubuntu 9.04?
 
Yes, repair grub from usb is possible
 
Use unetbootin to write Ubuntu to a usb drive and boot from it. Assume you have USB booting?!
then follow this:
 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
 
ARE YOU KIDDING??

You have to be einstien to follow all that.
 
is there now simple way to fix this error?

I hav a netbook with windows 7, xp, and ubuntu on it..
and i get this error.. my netbook is effectively bricked.
can sumone sort it out please.
 
theres not a hope in hell i can understand that HUGE article

---

### Post by Herman on 2012-03-05
If you have Ubuntu installed in a USB drive all you need to do is boot your USB auxilliary Ubuntu installation and run sudo grub-mkconfig -o /boot/grub/grub.cfg and when it finishes reboot to your USB's GRUB screen. 

You will now see an option in your USB Ubuntu's GRUB Menu for booting you regular Ubuntu installation which is inside your computer. Scroll down to it and boot your regular Ubuntu.

When your regular Ubuntu inside your computer has booted up, then run whatever commands you need to fix your regular Ubuntu installation's GRUB.
Most often sudo grub-install /dev/sda if your MBR has been overwritten should fix it. 
Use sudo update-grub or else sudo grub-mkconfig -o /boot/grub/grub.cfg if you want a new GRUB Menu.

For this method to work you need a real Ubuntu installation in a USB or some other drive in your computer, you need to know how to boot from your BIOS's boot menu, (press F8 or F12 in most compters, or consult your motherboard manual).

A 'Persistence' Live CD installed in a USB won't work because those don't boot with GRUB, but with syslinux instead. If you have one of those you can still fix your GRUB, but you'll need to use the chroot method, which is not easy for new users.

---

