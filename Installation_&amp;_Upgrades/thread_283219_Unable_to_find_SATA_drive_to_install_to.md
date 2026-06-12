---
title: "Unable to find SATA drive to install to"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by glsitdept on 2006-10-23
I am trying to install Ubuntu to an IBM server xSeries 336 that ONLY has a SATA drive connected to a PCI-X SATA card (SiI 3124 is a single-chip PCI-X to 4-port Serial ATA (SATA) host controller.)

I have tried 6.06 'dapper' and 6.10 'edgy' - latest build with no success - nothing seems to be able to find the card and hence the drives connected to it.

The card 'appears' to be found when running the 'live' dvd and shows that it uses sata_sil24 but install will not 'find' a drive.

I have been able to successfully install and run Knoppix but I'd prefer to run Ubuntu.

I'm a bit of a newbie here so any help would be greatly appreciated.

Thanks in advance,
m4000

---

### Post by T.Louis on 2006-10-24
Hi,

I'm probably stating the obvious but you need to have a driver for your Sil.

Maybe this will help a bit, there are a few options explained of what you can do:

[Serial ATA (SATA) chipsets — Linux support status]("http://linuxmafia.com/faq/Hardware/sata.html")

The page is a bit messy I guess, but it does talk about Sil etc.

Hope it helps a bit.

EDIT: A shot in the dark would be to install dmraid with Synaptic  Packet Manager, supposedly has some kind of Sil support?

---

### Post by glsitdept on 2006-10-24
Ran desktop (live) cd today and did installation from 'live' desktop. All went great until the reboot. It loaded up the Ubuntu splash screen but eventually said that the hard drive did not exist and stopped there.

Sorry to be such a newbie, but isn't the sata_sil24 suppoesed to be built-in to the kernel? If not, how(where) can I get the driver and how do I go about loading it?

Cheers for any help:)

---

### Post by T.Louis on 2006-10-25
I'm not sure if its kernel supported but judging by the link I gave you it is supported that is sata_sil24.

> Driver Support for Each Known SATA Chipset:
...
link) Addonics SATA-II family — fakeraid. See Silicon Image 3124. Models ADS3GX4R5-E (eSATA-II RAID5/JBOD card), ADSA3GX4RL (SATA-II PCI-X RAID card), and ADSA3GX4R-E (4-Port External SATA-II PCI-X card) all use SiI3124 chips. Model ADSA3GPX1-E (eSATA-II PCI-Express card) uses SiI3132 chips.
...
(link) Silicon Image 3124/3124-2 (chip in 4-port SATA-II PCI-X cards) and 3132 (chip in 2-port SATA-II PCI Express cards) (Silicon Image, Inc., formerly CMD Technology, Inc.)  — libata's sata_sil24 driver supports Silicon Image 3124 (2005-08) and also the follow-on 2-port PCI Express SATA-II successor chip, the Silicon Image 3132. (Per 2004-07-08's libata status report, Silicon Image provided Garzik with docs and sample hardware.)


No need to apologize about being a newbie, cause I'm the same a newbie. :p 

Now to the problem:

What exact error message do you get after splash screen?

Is it something like this:

```

hdb:ide_intr: huh? expected NULL handler on exit
hdb:ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hdb, logical block 357298

```

or is it something with:

```

Can't mount /dev/sda1.
Can't mount root filesystem.

```

and so on?

A bit more detail would be great.

---

### Post by glsitdept on 2006-10-25
Messages on screen:

<crtl><alt><f1> shows me this:

Starting up ...
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.392000] PCI: Cannot allocate resource region 1 of device 0000:00:00.0
ALERT! /dev/sda1 does not exist. Dropping to a shell!


<crtl><alt><f8> shows me this:

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by T.Louis on 2006-10-25
> **glsitdept said:**
> Messages on screen:

<crtl><alt><f1> shows me this:

Starting up ...
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.376000] ACPI: Resource is not an IRQ entry
[17179574.392000] PCI: Cannot allocate resource region 1 of device 0000:00:00.0
ALERT! /dev/sda1 does not exist. Dropping to a shell!


<crtl><alt><f8> shows me this:

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

An odd question, have you disconnected HDDs while installing? Or have you added HDD or swapt SATA ports? If you have try to put the Linux drive in SATA port 1.

EDIT: It can be solved through Live CD, but I thought if this works it might be quicker... ](*,)  ;)

---

### Post by glsitdept on 2006-10-25
No hardware added or removed after install from live CD.

Live cd asks if you want to continue in 'live' mode or reboot - I select reboot - cd ejects and then reboots.

There is only one drive attached during install and I'm assuming that it installs the boot loader to it (to the mbr by default isn't it?) so it must be finding something of the hard drive otherwise I wouldn't think I'd get anything onscreen?

---

### Post by T.Louis on 2006-10-25
> **glsitdept said:**
> No hardware added or removed after install from live CD.

Live cd asks if you want to continue in 'live' mode or reboot - I select reboot - cd ejects and then reboots.

There is only one drive attached during install and I'm assuming that it installs the boot loader to it (to the mbr by default isn't it?) so it must be finding something of the hard drive otherwise I wouldn't think I'd get anything onscreen?

Ok, just do a search on "ALERT! /dev/sda1 does not exist. Dropping to a shell!" here and google, and you will find numerous solutions to try, ranging from recompiling Kernel quickly to fixing menu.lst and fstab paths.

---

### Post by Thark on 2006-11-01
Okay I see this thread is a bit old, however, I just got an SATA drive 160GB and ubuntu, and most of the other distros I have tried say I have no hard drive.  My question is this. If the LIVE disc does not come with the SATA compatibility, then how is one supposed to get the SATA to work with a LIVE disc so you can install?

---

### Post by Thark on 2006-11-13
yea so i feel super noobish on this.  I got it to work like a day after i posted that, my jackass had my SATA setting at IDE not raid.  a quick config at boot up and what do you know.. it works.  ha, imagine that.

---

