---
title: "Problems with multiple disk UFI dual boot setup"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by cj.guttormsson on 2014-01-04
What my system looks like:

Lenovo Y500 laptop
1 TB HD -- Windows 8.1 installed (primary, original operating system)
16 GB mSATA SSD -- used originally for caching by Windows, trying to install Ubuntu to it (will be upgrading if this works)
System set to UFI mode -- (UFI partition exists on 1 TB HD)

What I'm trying to do:

I want to set up my system to be able to dual boot Windows 8.1 and Ubuntu 13.10. I want to leave the 1 TB drive alone, and let it be used for only Windows, and I want to install Ubuntu to the mSATA SSD. I have successfully gotten Ubuntu to boot from the SSD (when I choose it as a boot device by hitting F12 when I turn on my computer), but I have been unable to get a boot loader (boot manger?) properly working. I've been dual booting Ubuntu on computers for years, but this setup with multiple disks and UFI seems to be causing a lot of problems I've never had before.

What I've tried:

I first attempted to install Ubuntu to the SSD from a live usb drive. I noticed during installation that the system did not recognize that I had Windows installed on my main hard drive, but that did not seem to affect the install procedure. I'm also a bit confused as to why Ubuntu makes so many partitions; I understand the root filesystem and swap partitions, but why does it create a separate partition marked 'boot'? Creating a separate partition for /home also seems unnecessary to me (although I am aware of the arguments for it). Anyway, I managed to install it fine, but when I went to restart my computer, I found that although there was a menu option in grub for Windows, it didn't work (it gave some error which I can't currently remember). Booting Ubuntu from grub worked fine, though, so I did that. I next attempted to use boot-repair to fix grub, but I somehow only succeeded in deleting it. I tried restoring it using a guide on the internet that called for chrooting into my installation with a LiveCD, but that didn't work for me (the guide told me to run install-grub, which didn't work; I couldn't find any packages that would restore it either).

That having failed, I wiped the SSD and reinstalled it, this time instructing the installer to only create a single ext4 partition (the separate /home thing had been giving me out-of-space errors, and it just seemed more simple this way). I ran into the same problem with grub not booting Windows (it gace the same error), but I discovered that turning off secure boot in the BIOS options made it work. However, when I did that, it prevented Ubuntu from being able to be launched from grub! Grub would boot one or the other, but not both. I couldn't find a solution for this, so I attempted then to use rEFInd instead. I installed it, but I couldn't figure out to configure it. Striking F12 at system startup allowed me to choose rEFInd as a boot device, but it didn't present me with any kind of menu, and instead launched me straight into Windows.

Has anyone had a similar experience? My best guess for what I'm doing wrong is missing some partition on the SSD, or possibly having some flags set incorrectly. Both Windows and Ubuntu will boot and run just fine, but I am completely unable to get a dual-boot menu to work.

---

### Post by cj.guttormsson on 2014-01-06
Well, I fixed it. Simply turning off Secure Boot allowed rEFInd to work. There are some instructions on the website for enabling rEFInd with Secure Boot, but they seem kind of complicated, and involve a weird custom install procedure. I may attempt that when I get my new SSD.

---

