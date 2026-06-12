---
title: "Installing on separate hard drive keeping current GRUB"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by ibbuntu on 2010-03-04
I'd like to install Lucid on a spare hard drive I have, so I can do my bit for testing it. I have a feeling that if I just burn the latest alpha .iso and install from that, it will replace my current GRUB, whereas I would prefer to simply add the Lucid install as an option in my current GRUB.

Of course I might be wrong, I just wanted to check before I went ahead with it. I was unable to find the info I needed via searching.

---

### Post by darkod on 2010-03-04
Last screen of the installer, before clicking Install. Click on Advanced and deselect installing a bootloader.
Boot Karmic and do

sudo update-grub

---

### Post by hypersleep on 2010-03-04
I've actually got a related question.

I have Ubuntu 10.04 alpha 3 and Windows 7 installed on my laptop. I decided to install the Lubuntu 10.04 alpha 3 on a USB flash drive, but like an idiot, accidentally installed a new bootloader. So now, grub throws up an error if I boot up my machine without the Lubuntu flash drive inserted.

How can I undo this stupid mistake and go back to the grub menu I had before?

---

### Post by darkod on 2010-03-04
> **hypersleep said:**
> I've actually got a related question.

I have Ubuntu 10.04 alpha 3 and Windows 7 installed on my laptop. I decided to install the Lubuntu 10.04 alpha 3 on a USB flash drive, but like an idiot, accidentally installed a new bootloader. So now, grub throws up an error if I boot up my machine without the Lubuntu flash drive inserted.

How can I undo this stupid mistake and go back to the grub menu I had before?

Plug the flash, and boot your Ubuntu 10.04. Run:

sudo fdisk -l

to check the disk names and partitions, also look at their size to figure out which is which.

Once you know your Ubuntu disk name, just run:

sudo grub-install /dev/sd[COLOR=Red]X[/COLOR]

Because Ubuntu is booted up, that will install the grub2 from ubuntu onto the MBR of sdX.

---

### Post by hypersleep on 2010-03-04
> **darkod said:**
> Plug the flash, and boot your Ubuntu 10.04. Run:

sudo fdisk -l

to check the disk names and partitions, also look at their size to figure out which is which.

Once you know your Ubuntu disk name, just run:

sudo grub-install /dev/sd[COLOR=Red]X[/COLOR]

Because Ubuntu is booted up, that will install the grub2 from ubuntu onto the MBR of sdX.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes

```

That's where I want to install grub, correct?

**edit:** Yup that fixed it. Thanks a bunch.

---

### Post by darkod on 2010-03-04
> **hypersleep said:**
> ```

Disk /dev/sda: 160.0 GB, 160041885696 bytes

```That's where I want to install grub, correct?

Without seeing the whole results, I have to say yes with reserve. Usually the internal would be /dev/sda and if there is only one, the external would be /dev/sdb.

So it would be:

sudo grub-install /dev/sda

---

### Post by ibbuntu on 2010-03-05
> **darkod said:**
> Last screen of the installer, before clicking Install. Click on Advanced and deselect installing a bootloader.
Boot Karmic and do

sudo update-grub
This didn't find the installed Lucid kernel, it only found the kernels on the drive with my Karmic installation.

So in the end I've updated the menu.lst manually to give myself an option to boot to Lucid.

---

