---
title: "USB boot problem with UNR"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Bill1956 on 2009-12-22
I'm new to this.  I created a USB boot disk with a download of UNR, and created the boot drive using Penlinux.  Installed Ubuntu 9.10 UNR on my new Acer Aspire A0D250.  All good.  However, the USB boot hung up from time to time, so I tried installing again.  Now it hangs up every time on boot.  I have tried this using Penlinux, Unetbootin and the "Create a USB startup disk" utilty.   I'd like to install Ubuntu on a second Acer Aspire, but first want to be sure I've got a clean image that can be booted from USB.  Help!
Alternatively, is it possible to create my own image from the install I currently have on my hard drive?

---

### Post by phillw on 2009-12-22
Hi, under System --> Administration you should see the option to create startup disk.

That will make a fresh install onto your usb device.

Do note, that it will over-write any persistance that you may have had previously if you were running in persitence mode.

Phill.

---

### Post by Bill1956 on 2009-12-22
Tried that... it also hangs up on boot.

---

### Post by phillw on 2009-12-22
> **Bill1956 said:**
> Tried that... it also hangs up on boot.

Does the usb stick boot on the other computer ?  If so, then you're going to have to try different BIOS settings on your Acer - USB CD Drive / USB Hard Dirve seems to give decent results, whereas USB seems to fall over.

Some BIOS's **say** that they can boot from USB - They're fibbing.

[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

Has a test to weed out the fibbers from the honest ones ;-)

PHill.

---

### Post by aljoriz on 2009-12-23
Go to Applications> and look for Add/Remove or ubuntu software center> type UNetbootin

point in the direction of the iso file and press OK and wait

PRESTO!  

Ubuntu usb installer.  Now that was quick!

---

### Post by BZiadie on 2009-12-23
Hi. Trying to install UNR on an Asus EEE PC 1000HE from a USB stick. It'll start, but once I select the option to either try Ubuntu or install it, the screen goes black and all I have is the cursor, which indicates that it's loading, but it loads forever. It would be great if anyone could help. Thanks!

---

