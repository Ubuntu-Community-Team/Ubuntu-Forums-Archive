---
title: "HP laptop - &quot;Non system disk or disk error&quot; after installation"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by bradleypariah on 2018-10-16
I feel like I'm making some obvious installation mistake.  My laptop previously had Deepin on it, everything was running fine (it's never had Ubuntu, because I ran into this error previously).
HP Elitebook, Ubuntu 18.10
During install, my partition table has been attempted two ways:

P1 - Reserved for BIOS grub
P2 - /boot
P3 - / 
P4 - /home
P5 - swap

-and-

P1 - EFI
P2 - /boot
P3 - /
P3 - /home
P4 - swap

Depending on whether or not EFI support is on or off in BIOS will affect whether or not the installer warns me about having a "reserved" partition during the partitioning phase.

I have gone into BIOS and turned EFI support on and off for both partition set configurations, and I have tried manually selecting different drives during boot, but my laptop refuses to boot into Ubuntu 18.10 after installation.  After rebooting for the first time, I only get the error, "Non system disk or disk error, press any key to continue."

I always choose sda1 as my location for bootloader install. If I have EFI enabled, am I supposed to choose the specific partition, instead of the system disk?
If I have an EFI partition, do I still need a BIOS GRUB partition?  What combination of mistakes am I making?

---

### Post by oldfred on 2018-10-16
I started using gpt back in 2010 long before UEFI.
And then when Windows 8 came out & all new systems were UEFI, I started adding an ESP (for future) and bios_grub.
For quite a while after getting new system with UEFI, I partitioned with both UEFI and bios_grub in case I needed a BIOS boot install.
Or partitions only matter if missing for boot mode you are installing in. 
UEFI must have ESP & BIOS must have bios_grub if on gpt partitioned drive. Generally better to use gpt unless also booting Windows.
Then Windows has to have gpt if UEFI boot or must have MBR(msdos) if BIOS boot.

HP has some now common issues.
But those with newer UEFI seem to have fewer issues.
Have you updated UEFI from HP?

Most desktops do not need separate /boot partition. Some server or server type installs using LVM may need /boot partition.

How you boot install media, UEFI or BIOS is then how it installs and which supporting partition is used.
With BIOS you specify drive, not partition to install grub like sda, not sda1.
With UEFI, it does not matter what you specify, but specify drive. Grub in UEFI mode finds first ESP and uses that.

Some HP installs:
       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227)
HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

---

### Post by bradleypariah on 2018-10-17
Thanks for the helpful info.  I'll give it another go this evening.  

Not to trash on Ubuntu, but Deepin seemed to be a far easier installation.  I got stuck on this when I first got my laptop, and I only stuck with Deepin because it actually worked.  After using Deepin a while, Ubuntu came out with a new release, so I tried it again, but had this issue come back up. So, I tried KDE Neon, and that worked like a charm too.  After getting bored with KDE Neon, I just wanted my Ubuntu.  Ran into this dang problem again, so I went back to Deepin.  I've tried installing Ubuntu 17.10, 18.04, and now 18.10, (so I've been trying for a year) and Ubuntu is the only OS I can't make work on this laptop.  I even had Bohdi on it for a few weeks.  Debian too, but I couldn't get Wi-Fi working.  So weird.

---

### Post by oldfred on 2018-10-17
Were your other installs UEFI or BIOS?
Many have reported BIOS works with HP.
But HP violates UEFI standard that specifically says NOT to use description as part of boot. And only valid description is "Windows Boot Manager".
If only booting Ubuntu one work around is just to rename UEFI entry to boot grub as "Windows Boot Manager".  Details in link in my signature if that is issue.
But have not seen as many with HP having issues, so perhaps new HP UEFI does work better.

---

### Post by bradleypariah on 2018-10-18
My other installs were all UEFI.

Okay, so here's an odd result:
After trying every combination of configurations and partitions, I finally succumbed to just choose the option for "Erase entire disk and install Ubuntu."

[SIZE=3][B]It works fine.  
[/B][/SIZE]
WHAT ON EARTH.  That makes absolutely NO SENSE.  :confused:

USB legacy support on or off, no change.
Change UEFI boot order and legacy boot order, no change.
EFI partition with UEFI support ***on ***in BIOS - "failed to install grub to sda1" while still in live ISO.
BIOS grub partition with UEFI support ***off ***in BIOS - "Non system disk or disk error" after reboot. 
Separate /boot partition and just a / partition, no change.
SATA in AHCI, RAID, or IDE mode for all of the above, no change.

What's so different about everything being on one partition that makes it so the laptop sees the drive as a system disk?  -and why is Ubuntu the only OS that cannot install itself on my laptop when I manually choose partition sizes?

I'm super glad it's working now, I have my laptop back, but I feel like there's either something wrong with Ubuntu's installer, or I'm lacking some kind of critical information that I'm going to need later on down the road.

I had Deepin and ElementaryOS ISOs downloading on my desktop.  Choosing "Erase entire disk" was me being at my wit's end.  I was going to give up right after that.  I had absolutely zero belief it was going to make a difference.

---

### Post by oldfred on 2018-10-18
The only possible way to know difference would be to have Boot-repair's Summary report before & after and then do comparison of reports to see difference.
But it could be some setting in UEFI or an update to a kernel or other driver.

But glad it works now.

---

