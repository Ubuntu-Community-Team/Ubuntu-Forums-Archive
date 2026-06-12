---
title: "Wiping windows 7 with ubuntu on a netbook. Does not work"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by gravitate on 2013-11-30
I have an Asus netbook that I want to put ubuntu on. I have tried using unetbootin used the pendrivelinux.com from both windows 7 and OSX to make the USB flash drive boot. I have also tried this on an SD card and on 4 separate USB's which are usb 2, 3 etc. 
Anyway I have tried multiple combinations and I get no where because It is not picked up with the netbook. The sd port and usb port see the devices when windows is loaded but not to boot from.
I have been into the netbook bios and prioritised the USB devise and nothing happens. I have even tried disabling the HD drive for boot up and still get nothing.

If anyone has any ideas please help because I have tried everything asked everyone who knows anything about computers. No one knows and this is my absolute last resort.

---

### Post by The Cog on 2013-11-30
I always use dd to create bootable sticks these days. Something like
```
sudo dd if=ubuntu-whatever.iso of=/dev/sdf bs=1M
```

But it might be worth testing the stick in another PC to verify whether or not the stick is bootable - perhaps your Asus doesn't have the ability to boot from USB at all?

---

### Post by GGG83kf on 2013-11-30
t depends on whether the netbook is configured to boot with UEFI or Legacy BIOS. You can inspect the BIOS setting to see if UEFI is switched on. Since the netbook won't pick up the USB stick created by Unetbootin, I suspect it's been booting in the UEFI mode. If so, then that could be what's causing the problem.

---

### Post by gravitate on 2013-12-01
Hi actually you do not get [COLOR=#000000] UEFI or Legacy BIOS in windows 7 only windows 8 so this doesn't help at all :([/COLOR]

---

### Post by GGG83kf on 2013-12-02
Windows 7 does boot from UEFI, I am doing this everyday. A quick way to tell if windows 7 is booting from UEFI is to check if your hard drive has GUID Partition Table (GPT). On a hard drive with GPT, windows 7 only accepts UEFI booting. If it's confirmed that your netbook is booting from UEFI, you may want to make sure that Secure Boot is not used (creating a boot loader for Secure Boot can be complicated given you are working in windows). Hope this helps. Good luck :)

---

### Post by fantab on 2013-12-02
> **gravitate said:**
> I have an Asus netbook that I want to put ubuntu on. I have tried using unetbootin used the pendrivelinux.com from both windows 7 and OSX to make the USB flash drive boot. I have also tried this on an SD card and on 4 separate USB's which are usb 2, 3 etc. 
Anyway I have tried multiple combinations and I get no where because It is not picked up with the netbook. The sd port and usb port see the devices when windows is loaded but not to boot from.
I have been into the netbook bios and prioritised the USB devise and nothing happens. I have even tried disabling the HD drive for boot up and still get nothing.

If anyone has any ideas please help because I have tried everything asked everyone who knows anything about computers. No one knows and this is my absolute last resort.

What Asus Netbook?

In some BIOS, you need to 'enable' USB Boot plus make USB your boot priority. Just making it a priority won't help. Check again in the BIOS. I have an Asus Netbook, however, I can't remember if I had to enable Usb booting...

Are you sure that the downloaded ubuntu.iso is of genuine integrity? Do a [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM") Check. If the sums don't match then re-download the .iso.
Is the USB drive you are using good? Try another USB drive or check the drive you have on another PC to check.
Also check if you have 'FastBoot' enabled in BIOS... if it is enabled then disable it.

---

