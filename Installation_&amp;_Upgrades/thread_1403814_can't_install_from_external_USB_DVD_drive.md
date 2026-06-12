---
title: "can't install from external USB DVD drive"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2010-02-10
I'm trying to install Ubuntu onto an HP Envy 15 laptop, which has an external USB DVD drive. I can boot into the Ubuntu boot menu (where the choices are to boot the Live CD, start the install, etc.)

but whatever I chose here, I always end up with an initramfs error, saying it cannot find a live filesystem.

I've tried Ubuntu 9.10 and 9.04, both have the same result (though 9.04 does not display the same error message, just drops you into busybox). I verified the DVD medium, and the same disk is able to boot & install on a desktop system.

I've seen threads about Ubuntu running on an HP Envy 15 - I wonder how those guys made it work.

what could be wrong here?

---

### Post by foresthill on 2010-02-10
Some computers can't boot from an external drive. Your best bet is to boot into windows, let it detect the drive, then install the .exe file on the Ubuntu disc. When you reboot, you should have all the drivers needed to detect your external drive and boot from it.

Failing that, you can poke around in your bios and look for an option to boot from an external drive, but on older systems, this is often not possible.

So you may need to find way to install windows, just so you can boot from the external drive.

Why are you using an external drive anyway?

---

### Post by akos.maroy on 2010-02-11
> **foresthill said:**
> Some computers can't boot from an external drive. Your best bet is to boot into windows, let it detect the drive, then install the .exe file on the Ubuntu disc. When you reboot, you should have all the drivers needed to detect your external drive and boot from it.

Failing that, you can poke around in your bios and look for an option to boot from an external drive, but on older systems, this is often not possible.


well, this is a brand new system, and it can boot from the external drive - for example, the Windows installer / rescue this can boot from it.

> **foresthill said:**
> So you may need to find way to install windows, just so you can boot from the external drive.

Why are you using an external drive anyway?

because it doesn't have an internal DVD :)

---

### Post by akos.maroy on 2010-02-11
> **foresthill said:**
> Some computers can't boot from an external drive. Your best bet is to boot into windows, let it detect the drive, then install the .exe file on the Ubuntu disc. When you reboot, you should have all the drivers needed to detect your external drive and boot from it.


now I tried this, and interestingly, I get the same result...

---

### Post by foresthill on 2010-02-11
Sounds like you have a netbook then?

Another possibility is to install from a USB flash drive, but in order to create one, you have to have a good install CD and Ubuntu up and running. In System / Administration there is a program called "USB startup disc creator".

I wonder also if Ubuntu is not seeing your hard drive. Can you do a live CD install?

---

### Post by akos.maroy on 2010-02-11
> **foresthill said:**
> Sounds like you have a netbook then?

It could be that you have a bad install disc. I would try re-downloading Ubuntu and burning a new disc at a slower speed.

Another possibility is to install from a USB flash drive, but in order to create one, you have to have a good install CD and Ubuntu up and running. In System / Administration there is a program called "USB startup disc creator".

Assuming your bios is set up to boot from the external drive, a bad install disc sounds like about the only possibility.

not a netbook, but an HP Envy 15, which does not have an internal optical drive.

it wasn't a bad disk, but I managed to make a USB stick work since then.

now I get to the end of the install, and there install grub fails... so still some way to go...

---

### Post by foresthill on 2010-02-11
There are different places you can install grub. It can either be on the master boot record, or on another partition. So I would probably try both ways and one of them ought to work.

---

