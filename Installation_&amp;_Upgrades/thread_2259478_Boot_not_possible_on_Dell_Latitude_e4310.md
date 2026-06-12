---
title: "Boot not possible on Dell Latitude e4310"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by emanuel8 on 2015-01-04
I bought a Dell Latitude e4310 laptop. I'm trying to install ubuntu on it. It is 48h that I'm trying to install and configure it. After each installation I get a grub rescue shell with "error: invalid arch independente ELF magic". I tried some tutorial on web, I tried to use boot-repair, tried to make a independente boot partition at start of disk, swap to grub2 amd64 instead of i386 and others but nothing changed. I got success only with elementary os (but it doesn't fit my needed) and one time with ubuntu, but after a update I got kernel problem. Now I'm able to login in ubuntu only if the live DVD is inserted at startup. This is the first time that I get a lot of problem with ubuntu and/or linux distro...I don't want to switch to windows!!!

In BIOS I have default property that include legacy (non UEFI) booting mode (it supports UEFI but I don't know well how to use it).

---

### Post by fantab on 2015-01-04
Download and install [Boot-Repair ]("https://help.ubuntu.com/community/Boot-Repair")tool after booting Ubuntu from DVD/USB.
Select and run the option 'Create Bootinfo Summary'... _note down_ the [url] to the bootinfo and post it here.

Also run [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") on the downloaded ubuntu.iso image to check its integrity. 
If the strings don't match then download the .iso again and burn it properly to a DVD or USB.

---

### Post by emanuel8 on 2015-01-05
This is the url [http://paste.ubuntu.com/9676834/](http://paste.ubuntu.com/9676834/)

The DVD .iso checksum is right.

---

### Post by fantab on 2015-01-05
> Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

Try **[fixparts]("http://www.rodsbooks.com/fixparts/")** to fix the above error.

---

### Post by grahammechanical on 2015-01-05
If Ubuntu is the only OS then it does not matter if we install it in EFI mode or Legacy (BIOS) mode. But once installed we must not change the mode in UEFI. From the little reading I have done this error message is related to not having grub-efi files where they should be. Now, that should not be necessary if Ubuntu was installed in BIOS mode and the motherboard is booting in BIOS mode.

[http://askubuntu.com/questions/72003/how-do-i-resolve-a-grub-invalid-arch-independent-elf-magic-error](http://askubuntu.com/questions/72003/how-do-i-resolve-a-grub-invalid-arch-independent-elf-magic-error)

[http://ubuntuforums.org/showthread.php?t=1965810](http://ubuntuforums.org/showthread.php?t=1965810)

[http://stackoverflow.com/questions/18120835/debian-grub-rescue-invalid-arch-independent-elf-magic](http://stackoverflow.com/questions/18120835/debian-grub-rescue-invalid-arch-independent-elf-magic)

Look at the second and third post in the StackOverflow link. The third post is from the person with the problem and it explains how he/she solved it.

Regards.

---

### Post by emanuel8 on 2015-01-05
@fantab
I used fixparts using c and s arguments but nothing changed.

@grahammechanical
I already used the solution proposed in these post but nothing changed.

I installed grub customizer and used Install to MBR... and now seems to work!!! I didn't understand what the problem was, but for now it works...I hope it is a durable solution.

Thanks to all!

---

