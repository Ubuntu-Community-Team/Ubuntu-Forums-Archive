---
title: "About to install Ubuntu, just have some questions"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by handsheldhigh on 2013-01-15
Okay. About to install Ubuntu 12.10 on my Acer Aspire One 725-0487.
 
1. Will 12.10 and Windows 8 play nice with each other in a dual boot?
2. Will the battery life be similar to Windows 8?
3. Will I have to do a fresh install to update to 13.04 when it comes out?
4. Can I delete the Ubuntu install from Windows 8 with a partition manager?
5. Will my mic/webcam work fine, and does Skype work okay in Linux?
6. Will Unity run smoothly?
 
 
Thanks for your help in advance ):P

---

### Post by darkod on 2013-01-15
1. Depends. There are steps to follow BEFORE you start since win8 usually comes with the new uefi boot process AND secure boot. From what I have seen on the forum, very few people have got it right the first time. :)
2. No clue.
3. No, you can upgrade to 13.04 but it sometimes goes wrong, so be ready for it if you don't want to do a clean install.
4. Yes, but not sure if you will need to do something about the bootloader first. With legacy boot you have to, I don't know about uefi.
5. I have seen some problems with skype on ubuntu. The quality is not really what you would expect from it.
6. Probably.

---

### Post by handsheldhigh on 2013-01-15
> **darkod said:**
> 1. Depends. There are steps to follow BEFORE you start since win8 usually comes with the new uefi boot process AND secure boot. From what I have seen on the forum, very few people have got it right the first time. :)
2. No clue.
3. No, you can upgrade to 13.04 but it sometimes goes wrong, so be ready for it if you don't want to do a clean install.
4. Yes, but not sure if you will need to do something about the bootloader first. With legacy boot you have to, I don't know about uefi.
5. I have seen some problems with skype on ubuntu. The quality is not really what you would expect from it.
6. Probably.
 
I was able to get to Legacy BIOS, and I can boot from USB and such there. I'll check to see if Win8 boots in Legacy BIOS (it should, Windows 8 worked fine on another machine that used Legacy BIOS)

---

### Post by handsheldhigh on 2013-01-15
Ubuntu is able to boot from USB. Most things seem to work, although I think I might need a different driver for desktop effects.

---

### Post by darkod on 2013-01-15
> **handsheldhigh said:**
> I was able to get to Legacy BIOS, and I can boot from USB and such there. I'll check to see if Win8 boots in Legacy BIOS (it should, Windows 8 worked fine on another machine that used Legacy BIOS)

Win8 (same as Win7) will work just fine with legacy boot if that's how it was installed. On the other hand, if it's installed (or came preinstalled) in uefi mode, I don't think you can simply switch it later by switching the boot type in bios since the boot files are different.

So, if you installed it in legacy mode or it came that way, fine. But if it's in uefi, you can't change that regardless if the bios has Legacy Boot option.

And both OSs have to be installed in the same mode, so if win8 is uefi you have to stick to uefi for ubuntu too.

---

### Post by handsheldhigh on 2013-01-15
> **darkod said:**
> Win8 (same as Win7) will work just fine with legacy boot if that's how it was installed. On the other hand, if it's installed (or came preinstalled) in uefi mode, I don't think you can simply switch it later by switching the boot type in bios since the boot files are different.
 
So, if you installed it in legacy mode or it came that way, fine. But if it's in uefi, you can't change that regardless if the bios has Legacy Boot option.
 
And both OSs have to be installed in the same mode, so if win8 is uefi you have to stick to uefi for ubuntu too.
 
WIN8 was installed in UEFI mode... How would I install Ubuntu in UEFI mode?

---

### Post by handsheldhigh on 2013-01-15
Okay. UEFI is on, secure boot is off. Since I'll be installing from USB, do I just set the USB as the first, and install as usual? I understand that Ubuntu has UEFI support, correct?

---

### Post by darkod on 2013-01-15
Yes, the 64bit version has uefi support.

To install in uefi you have to boot the usb/cd in uefi mode, not legacy. On boards with uefi support, the boot devices are doubled. There is uefi version of the dvd/usb, and standard legacy version.

You have to boot the uefi version of the stick to install in uefi mode. Otherwise it will install in legacy without telling you anything and you won't have dual boot.

It might be easier to use the computer boot menu with F12 or similar, rather than chasing up boot device order in bios. For a one time boot to install, the boot menu is better and more precise.

---

