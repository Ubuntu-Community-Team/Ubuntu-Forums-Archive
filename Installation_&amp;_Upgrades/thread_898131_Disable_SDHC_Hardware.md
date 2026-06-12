---
title: "Disable SDHC Hardware"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by RogerM on 2008-08-22
I have a Presario V2310 that installs Kubuntu 8.04 but won't boot up, it hangs when it gets to the SDHC driver.  How can I get Kubuntu 8.04 to ignore that driver and proceed with startup?

Thanks,
  Roger

---

### Post by Shazaam on 2008-08-22
Do you have a card reader with an SD card inserted or a camera plugged in while booting?

---

### Post by RogerM on 2008-08-22
No, I believe the mother board is defective.  Windows XP (original recovery disk) will not install either.  I also believe the problem is with the memory card interface, which I don't need. So, rather than replacing the mother board I was hoping to somehow make the memory card interface invisible to the Kubuntu so it will boot up.

Note: Kubuntu appears to install correctly it just hangs during boot during installation of hardware devices.

---

### Post by Shazaam on 2008-08-23
Can you disable the card slot in the bios setup screen?

---

### Post by coffeecat on 2008-08-23
I'm a bit dubious that this will work, but anyway...

Presumably you can see the boot error message. Is it telling you the name of the kernel SDHC driver? If so you could try adding the driver to /etc/modprobe.d/blacklist - you'll have to boot up with a live CD to edit the file. Hopefully, with loading of the driver blocked the system won't see the faulty SDHC interface.

---

### Post by RogerM on 2008-08-23
No, I can't disable it at the bios.

Unfortunately, live CD hangs at "Loading Hardware Drivers".

I might be able to take out the hard drive and access it on another system but I am not exactly sure how to identify the hardware driver to put in the blacklist.

---

### Post by coffeecat on 2008-08-23
> **RogerM said:**
> I might be able to take out the hard drive and access it on another system but I am not exactly sure how to identify the hardware driver to put in the blacklist.

I've booted into Gentoo to look into the kernel configurator. I don't compile my own kernel in Ubuntu so I couldn't check in Ubuntu, but Gentoo is using the 2.6.24 kernel atm just like Ubuntu 8.04, so this should be OK. This is what is says about the mmc_sdhci module:

> Secure Digital Host Controller Interface support MMC_SDHCI

This select the generic Secure Digital Host Controller Interface.
It is used by manufacturers such as Texas Instruments(R), Ricoh(R)
and Toshiba(R). Most controllers found in laptops are of this type.
If you have a controller with this interface, say Y or M here.The Presario V2310 is a laptop, is it? That's what google tells me. When you talked about replacing the motherboard I thought you meant a desktop. I've built my own computer(s) and changed the HD in a Mac Mini but I don't think I'm up to changing the motherboard in a laptop. :(

Anyway - if you can get the HD out and mount it on another system, try adding this line to /etc/modprobe.d/blacklist:

```
blacklist mmc_sdhci
```Again, no promises. I'm groping in the dark here.

**Edit:** I've corrected an extremely bad typo in that code for blacklist. Sorry for that.

---

### Post by gatenby_jp on 2008-08-23
You could try booting with a knoppix 5.1 cd ... does give you option of failsafe mode which should allow you to edit the blacklist. As suggested in the previous post.

I am not sure but I think if you select the recovery kernel on the the grub menu there is an option to get a shell login which should also allow you to make the entry in the blacklist

---

### Post by RogerM on 2008-08-23
Unfortunately, putting

blacklist mmc_sdhci

in the blacklist didn't work but thanks for trying.

Anymore suggestions to try?

---

### Post by RogerM on 2008-08-26
I used

blacklist sdhci

and it worked!

---

