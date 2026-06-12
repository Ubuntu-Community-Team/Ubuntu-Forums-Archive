---
title: "Universal USB Installer does not see drive"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by at0msk on 2010-06-06
20GB Laptop HDD in external enclosure with USB interface. Formatted FAT32. Shows up in Windows as E:. The Universal USB Installer, however does not see the drive. Is that app only set to look for a true USB flash drive and I'm just doing it wrong?

---

### Post by wilee-nilee on 2010-06-06
> **at0msk said:**
> 20GB Laptop HDD in external enclosure with USB interface. Formatted FAT32. Shows up in Windows as E:. The Universal USB Installer, however does not see the drive. Is that app only set to look for a true USB flash drive and I'm just doing it wrong?

Does the device mount at all? it has to be mounted to used.
Why are you using the universal when there is a on board ubuntu usb loader. And what exactly are you trying to do?

I think I understand you have no Ubuntu setup and your trying to get one using this install in a MS environment, is this correct?

---

### Post by at0msk on 2010-06-06
> **wilee-nilee said:**
> Does the device mount at all? it has to be mounted to used.
Why are you using the universal when there is a on board ubuntu usb loader. And what exactly are you trying to do?

I think I understand you have no Ubuntu setup and your trying to get one using this install in a MS environment, is this correct?


Yeah. If you mean mounted as in I can go to My Computer, open E:, and write files to it then yes.

If you check Ubuntu.com's download section there's a way to install Ubuntu to the flash drive so it's like a live cd.

---

### Post by darkod on 2010-06-06
> **at0msk said:**
> 20GB Laptop HDD in external enclosure with USB interface. Formatted FAT32. Shows up in Windows as E:. The Universal USB Installer, however does not see the drive. Is that app only set to look for a true USB flash drive and I'm just doing it wrong?

I think it is more limitation from windows than from the Universal USB Installer. Windows uses different driver for usb sticks, and different for usb hdds. Because of this limitation I think it's not seen same as usb stick would be.

---

### Post by bumanie on 2010-06-06
I have never managed to get the universal usb installer to install to a usb hard drive, works fine on usb flash drives - suggest you go to [pendrivelinux]("http://www.pendrivelinux.com/search/ubuntu+on+hard+drive") and follow one of the older tutorials for a usb hard drive, but they won't explain any thing about grub2, if you are trying to use the latest ubuntu. Make sure you do not install grub 2 to the mbr of your internal hard drive.

---

### Post by wilee-nilee on 2010-06-06
n

---

### Post by darkod on 2010-06-06
> **bumanie said:**
> I have never managed to get the universal usb installer to install to a usb hard drive, works fine on usb flash drives - suggest you go to [pendrivelinux]("http://www.pendrivelinux.com/search/ubuntu+on+hard+drive") and follow one of the older tutorials for a usb hard drive, but they won't explain any thing about grub2, if you are trying to use the latest ubuntu. Make sure you do not install grub 2 to the mbr of your internal hard drive.

Are you talking about installing on usb hdd? The usb installer is just to make a bootable usb stick with the ubuntu files, instead of cd. You are not making full install on the usb stick and have no choice where grub2 will go. The process is automatic.

On the other side, installing onto usb hdd is a different story.

---

### Post by bru3 on 2010-09-22
Had the same Problem.
Format the Stick using Windows solfs it.

---

### Post by Bezmotivnik on 2010-11-24
No, the problem is that the stupid $(&^$ "universal USB Installer **ONLY** sees a non-existent A: drive on the list.

Laboriously reformatting the USB E: drive does **nothing** to change this.

There's only A: drive in the list.  That's even the way it looks in the tutorial.  There's no mention of this on the site.

I've wasted a couple of hours trying to get this piece of crap to work and do an install.

---

