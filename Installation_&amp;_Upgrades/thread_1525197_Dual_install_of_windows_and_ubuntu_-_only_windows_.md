---
title: "Dual install of windows and ubuntu - only windows running?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by tank.tmt on 2010-07-06
I had only had windows xp on my comp. Windows was already installed and first so.
I have downloaded and installed 64x ubuntu 10.04 on a separate hard drive
When it finished windows booted: windows does not see the hard drive anymore
Only windows will boot now: ubuntu does not boot there is no screen to even try
I want my hard drive back; I want ubuntu to boot
Please help

Edit: I did not import anything from windows - i will import stuff from windows on a reinstall of ubuntu and hope that solves my problem - i suspect it needs to import boot data
Update: I tried to reinstall ubuntu and import some settings, it did not work it said the drive had problems - it didn't say it before therefore it is because i was trying to install ubuntu on ubuntu; I am now reformatting drive and repartitioning in reverse order obviously, I will then try to install Ubuntu again
Update: reinstall has same problems even though I changed it so that that the HD was the first in Bios; looking for how to change GRUB but was still not given option of GRUB - assumed it went for default settings.

---

### Post by ACupOfCoffee on 2010-07-06
These are two separate problems.
1.)Ubuntu won't boot.
2.)Windows doesn't read the drive you installed Ubuntu to.

1.)Windows is likely installed on your first hard disk and Ubuntu on your second one. That's how it normally goes. What I think you did was to install GRUB on your second drive. I can see how that might seem sensible: You put the bootloader on the drive you wanted to boot. The BIOS in nearly all computers will only boot the first hard drive. In your case that's the one that still has Windows and its bootloader on it.

There are two fixes. You can swap drives to change the OS you want to boot to. I don't recommend doing that since Ubuntu knows it's on the second drive and making it the first may cause some problems.

The better solution is to reinstall Ubuntu and this time put GRUB on your first drive.

2.) Windows can't read ext2 formatted drives without special software installed. The last time I looked into that it worked, but not perfectly. I must admit, though, that this was several years ago and everything may work perfectly now. If you really need to move files from Ubuntu to Windows, the best thing to do would be to transfer them within Ubuntu.

---

### Post by tank.tmt on 2010-07-06
@ACupOfCoffee - Statement: The install did not give an option of saying where to place the booter, the booter which i believe is called GRUB2 was never mentioned; the options given were to install alongside windows, replace windows, on another hard drive or select manually - i placed it in another hard drive as i dont want the 2 OS on the same HD so i may remove a HD and still have the other

Query: How do I select where the bootloader goes? Where do I get that option? How can I tell which is which Hard drive for terms of being first second or third for booting?

Statement: In Bios I changed the HD numbering (is this what you mean when you refer to HD numbering) to see if it would work - it came up with a blank screen and did nothing so I am now trying to reinstall Ubuntu after i have reformatted the drive and repartioned it with the boot thing different
but as i have said - the ubuntu installer didnt give me the option of selecting where the boot thing went - or rather i didnt look i used default settings and just told it what it asked for

---

