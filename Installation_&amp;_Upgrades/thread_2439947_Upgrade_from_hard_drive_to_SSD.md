---
title: "Upgrade from hard drive to SSD"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2020-04-03
I bought a faster old computer that has win 10 currently installed. I want to upgrade the internal drive to an SSD and add Ubuntu to it.
There is only one internal drive bay - so I am unable to add the second drive and clone from one to the other easily. Is there another way to clone to an SSD through USB perhaps?

---

### Post by CelticWarrior on 2020-04-03
Yes, there is, but it's a waste of time because with most tools the clone will not boot.

Better to just backup your personal files and reinstall everything in the new drive. Make sure to download all the drivers needed for Windows 10 from the vendor before doing that.

---

### Post by michael351 on 2020-04-03
The problem is installing Win 10. I don't have the installation media/license. The computer I bought comes with Win10 pro installed. I want to keep that and add Ubuntu to it for dual boot.

---

### Post by CelticWarrior on 2020-04-03
Installation media you can download from Microsoft anytime and if UEFI - any computer from the last 10 years or so - the license is already there in the EEPROM, you can and should install without providing any license and it will activate. This is just some basic stuff for any Windows 8 or newer.

---

### Post by dragonfly41 on 2020-04-03
> [COLOR=#000000]There is only one internal drive bay - so I am unable to add the second drive[/COLOR]

When I was exploring various HDD/SSD configuration options I read that some (without a second drive bay in their PC) have just stuck their added SSD to the side of the PC using velcro tape.
Others have put their SSD in the DVD caddy.
I opted for an external USB 3.0 dual docking station (StarTech). (note: probably would not work on older PC without USB 3.0 +)
I am using external SSD right now on Dell 3268. Windows 10 and an early Ubuntu installation remain in internal drive.

---

### Post by michael351 on 2020-04-03
I did not know that - thank you!

---

### Post by SeijiSensei on 2020-04-03
> **CelticWarrior said:**
> Yes, there is, but it's a waste of time because with most tools the clone will not boot.
I've cloned the hard drives to SSDs in two laptops using ddrescue, and both images booted with no problems.

To do this I used a SATA to USB converter like this one: [https://www.newegg.com/vantec-cb-isatau2-usb-to-ide-sata/p/N82E16812232002?Item=N82E16812232002](https://www.newegg.com/vantec-cb-isatau2-usb-to-ide-sata/p/N82E16812232002?Item=N82E16812232002)

Install ddrescue with

```
sudo apt install gddrescue
```

then connect the drive to the USB port with the adapter.  Likely it will appear as /dev/sdb.  Then to clone the drive run

```
sudo ddrescue /dev/sda /dev/sdb
```

My machines had only Linux and no Windows partitions.  However ddrescue does a bit-for-bit copy of one device to the other, so I'm guessing it should work if Windows is there as well.

/dev/sda should not be mounted during this procedure. The easiest way to manage that is to boot from an Ubuntu ISO and choose "Try Ubuntu" when prompted.  Then install gddrescue, and you'll be on your way.

---

### Post by CelticWarrior on 2020-04-03
> **SeijiSensei said:**
> I've cloned the hard drives to SSDs in two laptops using ddrescue, and both images booted with no problems.

Yes, but you have Linux and you know what you're doing. The OP doesn't fulfill those conditions.

---

