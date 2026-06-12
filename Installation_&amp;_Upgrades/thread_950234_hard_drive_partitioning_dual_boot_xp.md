---
title: "hard drive partitioning dual boot xp"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by cp3 on 2008-10-16
hi, new to ubuntu and these forums.  just a couple questions as regards to installing ubuntu.

right now my hd is setup this way.

```

[  c:\windows xp  ][  d:\storage  ][  ext3/slackware ][ linux swap ]

```

do i need to setup another partition for the bootloader?  i forgot where i read it but this person was suggesting for a /boot partition of at least 512mb with an ext2 filesys that should go before my windows xp partition.  and when installing i would select "manual" when at the partitioning setup for ubuntu installation right?

last question.  all installs ive done in *nix i see my drives represented as hda1-3 hdb1-3.  but now its sda1-3.  any reason why this is so?

thanks in advanced for the response. :)

---

### Post by caljohnsmith on 2008-10-17
> **cp3 said:**
> do i need to setup another partition for the bootloader?  i forgot where i read it but this person was suggesting for a /boot partition of at least 512mb with an ext2 filesys that should go before my windows xp partition.  and when installing i would select "manual" when at the partitioning setup for ubuntu installation right?

That advice about putting your /boot partition is meant to prevent a boot problem that arises when the BIOS can't see anything on the HDD past either 8 GB or 137 GB (depends how old the BIOS is which limitation it might have). Basically if your BIOS has one of those limitations, and your boot files are outside the range, you won't be able to boot; that's why putting the /boot partition near the beginning of the HDD can solve that problem. 

So how are you booting Slackware right now? If you are using Grub or Lilo to boot slackware OK now, then if you install Ubuntu over slackware or your storage space it should work fine as far as booting goes. :)
> **cp3 said:**
> last question.  all installs ive done in *nix i see my drives represented as hda1-3 hdb1-3.  but now its sda1-3.  any reason why this is so?

thanks in advanced for the response. :)
I don't know the details, but you're right, Hardy sees all IDE and SATA drives as sdX and not a mixture of hdX and sdX like previous releases. Sorry I can't help with that question. :)

---

### Post by zero7404 on 2008-10-17
> **cp3 said:**
> hi, new to ubuntu and these forums.  just a couple questions as regards to installing ubuntu.

right now my hd is setup this way.

```

[  c:\windows xp  ][  d:\storage  ][  ext3/slackware ][ linux swap ]

```

do i need to setup another partition for the bootloader?  i forgot where i read it but this person was suggesting for a /boot partition of at least 512mb with an ext2 filesys that should go before my windows xp partition.  and when installing i would select "manual" when at the partitioning setup for ubuntu installation right?

last question.  all installs ive done in *nix i see my drives represented as hda1-3 hdb1-3.  but now its sda1-3.  any reason why this is so?

thanks in advanced for the response. :)

there are several ways to install ubuntu, you may want to have a look at other options before you decide to put linux on the same hdd as windows.

for a beginner, i found it was best for me to take the external hdd approach. i disconnected my winodws drive(s) and installed ubuntu on an external usb hdd. over time i've learned and configured....linux is much more versatile than i thought. of course windows is as well, but it takes a bit more work and purchasing some power-software to be able to do the same things that linux can for free.

for example, i have an MBR on my raid 0 that was put there by my vista installation. i also have an MBR on the external hdd that was put there by ubuntu. i was able to configure ubuntu's bootloader to allow me to boot into windows, even tho it's on a raid array.

so now i have a completely dual-boot system, with the ability to pull the usb drive from the computer and it's like linux was never there...

the only tricky thing with installing linux is that it needs special attention when being installed on a physical disk that has another OS on it, even more attention is needed when trying to install it on a raid array.

---

### Post by cp3 on 2008-10-17
> **caljohnsmith said:**
> That advice about putting your /boot partition is meant to prevent a boot problem that arises when the BIOS can't see anything on the HDD past either 8 GB or 137 GB (depends how old the BIOS is which limitation it might have). Basically if your BIOS has one of those limitations, and your boot files are outside the range, you won't be able to boot; that's why putting the /boot partition near the beginning of the HDD can solve that problem. 

So how are you booting Slackware right now? If you are using Grub or Lilo to boot slackware OK now, then if you install Ubuntu over slackware or your storage space it should work fine as far as booting goes. :)

I don't know the details, but you're right, Hardy sees all IDE and SATA drives as sdX and not a mixture of hdX and sdX like previous releases. Sorry I can't help with that question. :)

im booting slackware through lilo.  but if i install ubuntu now over the slackware installation wont ubuntu override the lilo with grub?  wish i could keep lilo if theres anyway.

so when i do install just click "Manual" when going into the partition part, select the / partition to be mounted over the slackware installation and the setup will take care of the rest?

---

### Post by caljohnsmith on 2008-10-17
> **cp3 said:**
> im booting slackware through lilo.  but if i install ubuntu now over the slackware installation wont ubuntu override the lilo with grub?  wish i could keep lilo if theres anyway.

so when i do install just click "Manual" when going into the partition part, select the / partition to be mounted over the slackware installation and the setup will take care of the rest?
Grub should work just fine, so I wouldn't be afraid if I were you to change over to Grub from Lilo. In many ways Grub is a lot more robust than Lilo, and in most cases it is a better boot loader in my opinion. 

And about installing, yes, just do the "manual" install and set Ubuntu's root mount point "/" to the slackware partition. It's been a while since I've done a Ubuntu install, but I think it should be fairly explanatory since you obviously have some experience. :)

---

### Post by cp3 on 2008-10-17
thanks for that quick response.  will take the dive into ubuntu in a few.

---

