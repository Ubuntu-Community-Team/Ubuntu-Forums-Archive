---
title: "Impossible install GRUB (so any Linux distribution) to HP G6 250 notebook"
date: 2018-03-20
forum: Installation &amp; Upgrades
---

### Post by friiduh on 2018-03-20
Hi, I have now tried few days to install all kind Ubuntu/Kubuntu from 16.04, 16.10, 17.04, 17.10 etc to Arch Linux but GRUB installation "always" (one exception) fails without any explanation. 

grub-efi-amd64-signd (or so) doesn't just like to get installed, but just hangs to make configuration. 

Secure boot has been enabled, disabled, and even tried the legacy mode. But in any mode doesn't GRUB like to get installed past that. 

Almost every installation from Live mode just hangs in the end and computer boots to grub command line. 


I have once managed to get Kubuntu 17.10 installed and to boot normally, but I couldn't update or install any packages as dpkg wanted to be reconfigured and that forced to re-configure GRUB, and it just hangs. So it was just impossible even install any other package anymore nor update system without running grub reconfigure. 
So that once happened installation was useless regardless it was booting from SSD. 

I am now out of ideas what to do, I have read all kind UEFI manuals and guides but none of them is helping what so ever, example:
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-03-20
If UEFI mode you must have the ESP - efi system partition which is a FAT32 formatted partition with boot flag.
Or if legacy mode on gpt partitioned drive, you must have a bios_grub partition for grub's core.img. It is unformatted 1 or 2MB with bios_grub flag.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

HP often requires a work around as it violated UEFI standard and uses description as part of boot. And only valid description is "Windows Boot Manager". 


Boot-Repair now does  copy.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by friiduh on 2018-04-03
> **oldfred said:**
> If UEFI mode you must have the ESP - efi system partition which is a FAT32 formatted partition with boot flag.
Or if legacy mode on gpt partitioned drive, you must have a bios_grub partition for grub's core.img. It is unformatted 1 or 2MB with bios_grub flag.

Yes, the installer by default creates the correct partitions. But GRUB install fails.
I have as well done partition manually, and still it fails. With all the correct filesystems, partition flags etc.

> 
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

HP often requires a work around as it violated UEFI standard and uses description as part of boot. And only valid description is "Windows Boot Manager". []/quote]

I thought that HP has some kind non-standard / common thing with HP as I can't see reason why DPKG can't just install GRUB. 


Boot-Repair now does  copy.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

I need to try some of those... 

One of these nasty things with cheaper laptops that OEM doesn't like to make things easy!

---

