---
title: "Macbook Air 4,2 EFI/GPT 12.04 install works, but won't boot kernel"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by househead on 2012-10-16
So, I've been a Linux user for some 8 years or so now, and I've installed many a distro on many a machine, but I've not struggled like this for years.

My MacbookAir 4,2 11" is a beautiful laptop. OSX is ace, but I need Linux on it too. I'd moved away from being an Ubuntu user at work (on my Dell XPS13) and opted for a mega-minimal Arch Linux/Fluxbox rig.

The Air is my personal machine, so OSX mostly does what I need, but sometimes it would be nice to be able to boot into Linux. I have installed Ubuntu (and other distros) on a Mac before, as I also have a MacMini. It was always a breeze to install Ubuntu on the MacMini.

Anyway, onto my current situation...  I decided that I don't want to use Refit, and to stick to GPT disk partitioning without the MBR syncing. I also intend to use the Air in pure EFI mode, and utilise Apple's bootloader. As I do with my other linux laptop, I wanted swap and root to be encrypted, luks/lvm style.

So, I installed using the standard 12.04 install CD for amd64. Had a few issues getting both the luks/lvm sorted and also with installing grub2-efi etc. Once I got round those, installing grub-efi binary into my EFI system partition and getting /etc/crypttab correct, I managed to boot ... but only so far.

The boot process got as far as loading initramfs, asking me for a passphrase, and opening the LVM/Crypt devices etc, then it tries to run a few initscripts (see attached image). Due to this, I though I'd boot in recovery mode. In recovery, my root fs is mounted (strangely though, /boot is not).

Figuring that my crypt devices might be confusing the whole thing, I did the install again, this time totally standard (except grub2 which is a few extra steps). I get the exact same issue :(

On the provided image, it seems to hang on CUPS?! But personally I refuse to believe this is the problem till I can see more.

I'll be gutted it I cannot install Ubuntu on this laptop. I'm sure it's possible, but these days there's only so much I will struggle at it (especially given my XPS13 does a great job anyway).

Any help appreciated, and obviously I can provide whatever information on my settings/hardware etc. Thanks in advance. Peace

---

### Post by househead on 2012-10-16
Oh and it's probably worth stating that the fsck output in the photo is due to me having to hard reboot!

---

