---
title: "Boot error on install."
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by pidey on 2012-10-25
Hello.  I am attempting to install 12.10 via usb on a 32bit computer.

The computer can boot into the windows that is already installed on it.

I used lili to create a USB installer (usb drive is 2gb).  However, when I attempt to boot from this USB drive, I simply get an error, stating "Boot Error"  Every time I hit a key, it simply repeats the error.

I have tried using the USB on another computer, and the installer started up just fine.
I have also tried putting 12.04LTS on the thumbdrive.  Same error.

What should be my next step?

---

### Post by dino99 on 2012-10-25
when you says "usb drive" do you mean stick or hdd? how is it formatted ? which ide option is set into the bios ? (ide, compatible or else)

---

### Post by pidey on 2012-10-25
The USB drive is a micro SD card reader with a micro SD card in it.  It is formatted with fat32.  It works properly on other computers.  I am not sure about the IDE setting, I will attempt to figure this out.

What SHOULD the IDE setting be set to?

---

### Post by 2F4U on 2012-10-25
Since it is a 32 bit machine, did you download the 32 bit iso image of Ubuntu?

---

### Post by pidey on 2012-10-25
Yes, I have used both the 32 bit version of 12.10 and 12.04LTS

These both worked on a different 32 bit computer.

---

### Post by dino99 on 2012-10-25
is that sd card already usable on that pc ? (seems like a driver issue for that hardware) and does the bios recognize it as a device ?

---

### Post by pidey on 2012-10-25
The bios recognises the USB SD card reader, as far as I can tell, the BIOS thinks it is an ordinary thumbdrive.

---

### Post by dino99 on 2012-10-25
i have no clue about lili, but maybe try something else like pendrivelinux or unetbootin

---

### Post by preetijpillai on 2012-10-25
just try booting from a dvd instead of a pendrive.. It might just work in that case

---

