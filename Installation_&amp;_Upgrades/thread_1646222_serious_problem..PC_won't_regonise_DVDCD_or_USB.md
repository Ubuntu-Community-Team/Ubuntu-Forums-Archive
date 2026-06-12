---
title: "serious problem..PC won't regonise DVD/CD or USB"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by teddy101 on 2010-12-15
I being a compleat twit, managed to deleate my windows partion while trying to install ubuntu.

I didn't already have any linux partions installed. 

I am using a Acer Aspire 5332. 

I am getting up an error screen saying put in windows disk to repair, bla bla bla (i dont have one)

I have set the computer BIOS to boot from both DVD drive and USB drive.

Both resultied in the same error screen coming up.

I do need a working laptop as soon as possible.

So any heroic genius, please, give us a hand.

Tom

thanks

---

### Post by coffeecat on 2010-12-15
Do you want to restore Windows or install Ubuntu? Even though you've deleted your Windows C: partition, you may still have a usable Acer restore partition from which you could reinstall Windows. It may be that it is not booting properly and hence the on-screen message. Whichever you want, boot up from a live Ubuntu CD or live Ubuntu usb pendrive, make sure you are connected to the internet and go to this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script and then post the contents of the results.txt file (in code tags - press the # icon - for legibility).

That will give us your partition layout and the state of whatever bootloader you have.

If the Acer partition is usable but presently unbootable, a simple repair of the Windows mbr may suffice. But if you want to abandon Windows and install Ubuntu, that is doable from the live session but it will be useful to know what partitions and disk space you have from the above output. Tell us what you want to do.

---

### Post by teddy101 on 2010-12-15
Thanks for the reply.

I want to install ubuntu.

I can't do as instructed as the laptop 'ignores' the USB or CD/DVD

---

### Post by wilee-nilee on 2010-12-15
> **teddy101 said:**
> Thanks for the reply.

I want to install ubuntu.

I can't do as instructed as the laptop 'ignores' the USB or CD/DVD

There is a per-session key prompt try hitting f12 at power on and see if you get a boot from menu choose what you want to boot.

---

