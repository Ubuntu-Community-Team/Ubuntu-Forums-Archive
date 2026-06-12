---
title: "Boot from USB"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by II Luis II on 2010-07-23
Ok I used the USB installer to make a live USB with ubuntu (I didnt format the drive). It doesnt boot on start up so I went into setup/BIOS and cant figure out which i need to move up the boot order? This is what I get on the boot tab:

BOOT PRIORITY ORDER:
1: IDEO: HITACHI (serial here)
2: CD/DVD: PIONEER DVD-RW DVDRTDO8RS-(
3: NETWORK BOOT: BO2 DOO YUKON PXE
4: USB HDD:
5: USB FDD:
6: USB KEY:
7: USB CD/DVD ROM:

So which one is it that I move up the boot order and how far up does it need to go?

Thanks.

---

### Post by lechien73 on 2010-07-23
Is it a USB hard disk drive, or a USB memory stick? If it's a hard disk then move entry 4 to the top, if it's a USB memory stick then move entry 6 to the top. They need to boot before your primary hard drive. You may need to change the entries again after installation.

---

### Post by II Luis II on 2010-07-23
its a 2GB memory STICK, I can always change it back right? so its back to position six?

---

### Post by C.S.Cameron on 2010-07-23
With some BIOS you need to make the usb stick the first hard drive.
Also with some computers if you press F10 or F12 while booting you get an option for which device you want to boot.

---

### Post by II Luis II on 2010-07-23
Sorry just to clarify, I am using a Memory stick so I need to move number 6 to the top of the list? Also if I dont put in the memory stick will the computer just boot as normal?

---

### Post by linux18 on 2010-07-23
yes, put #6 at the top of the list.
if it doesn't boot you will just go back to the hard disk - changing boot order is perfectly safe

---

### Post by II Luis II on 2010-07-24
Meh didnt work thanks for all the comments/help cant get it to work so Ill just order a CD.

Thanks

---

### Post by Krabby.Linux on 2010-07-24
It is usually not really necessary to order the CD. What is your Problem now? Does your System start booting from your Harddisk? Or is it booting from your Stick but your stick does not work. Try again to create the Live Disk with Ubuntu and than go into your BIOS and change the Botting Order: Place the USB tagged Devices Up to the first places. Now the System will first go and search for a bootable device connected via USB.

---

### Post by lechien73 on 2010-07-28
Interestingly I just installed Ubuntu on a friend's Acer machine, and had to move "USB HDD" to the top to get it to boot, instead of "USB KEY" - even though I was booting from a USB memory stick. So you could try that.

You could also try re-creating the USB stick. As far as I know the procedure formats the drive before transferring the image, but it's worth giving it a go before ordering the CD.

---

