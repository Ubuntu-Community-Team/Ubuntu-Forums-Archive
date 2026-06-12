---
title: "Problems booting a UX32A after install"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2013-08-24
I've tried installing Ubuntu amd64 13.04 on my Asus Zenbook UX32A. The usb boots fine. Installation goes fine but when I reboot the problems start. Here's my setup:

```
/ on /dev/sdb2
/home on /dev/sda7
swap on /dev/sda6
EFI boot on /dev/sda1
```

I tried installing grub once on /dev/sdb (which is the SSD drive) and the rest of the times on /dev/sda (which is a regular sata HD). Stupid, I know, so now I've got two ubuntu in BIOS... When I boot, Grub starts fine and at the beginning I got the error: "An error occured while mounting /boot/efi" and the choice to manually mount or to skip. If I skiped I get a prompt and can do things but X won't start. Since reinstalling I just get the purple screen and that's it.

I saw something about wrong fs type, bad option, bad superblock on /dev/sda1. 

When I try booting the other OS that came with the mandatory laptop tax (Windoze 8) from grub I get: "Error: Can't find command 'drivemap' Error: invalid EFI file path".

I can boot into the recovery mode. That is, I get the menu with the choices but I can't start x, nor can I get Wifi going. I'm going to try to get a wired connection going at home but there's only lo. No eth0. I can boot to root and fiddle around.

BIOS has secure boot disabled, quickboot (or whatever it's called) disabled and boot set to Ubuntu (one of the two). 

I've read quite a few blogs and threads on this but not yet found a solution. I used to know this stuff but this new BIOS thingy makes me feel oooold... Help is MUCH appreciated.

---

### Post by oldfred on 2013-08-26
Best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by 1/0 on 2013-08-26
Thanks. I sat with the computer this afternoon and figured it out. I figured since I got the error message about wrong fs etc on /boot/efi, something's wrong with the config. The new grub2 config is more of a script and really makes editing more complex imo. 

Anyway, I did some reading on grub2 and added this to /etc/grub.d/40_custom by chrooting from the live USB (since the fs in recovery was mounted as read only...)

```

menuentry "Windows 8" {
insmod part_gpt
insmod ntfs
insmod search_fs_uuid
insmod chain
search --fs-uuid --no-floppy --set=root 5435-6B34
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

```

Suddenly Windoze was up and running. Embarrassing to say that I got that working first. So I tried adding the equivalent for ubuntu:

```

menuentry "Ubuntu 1" {
insmod part_gpt
insmod ext4
insmod search_fs_uuid
insmod chain
search --fs-uuid --no-floppy --set=root /dev/sdb2
chainloader (${root})/EFI/ubuntu/grubx64.efi 
}

```

No go. Grub complained that ext4 was wrong fs and there was no /EFI/ubuntu/grubx64.efi. So I made a more old fashioned version:
```

menuentry "Ubuntu 2" {
  search --file --no-floppy --set=root /vmlinuz
  fakebios
  linux /vmlinuz root=/dev/sdb2 video=efifb
  initrd /initrd.img
}

```

This worked! Now I just have a lot of entries in Grub but that I can fix later. I tried some Grub repair GUIs before but they only said that it was fixed when it wasn't. I hope this helps if there'se anyone with the same problem as me. It bugs me that Ubuntu is starting to behave as Gentoo when it comes to this. Installation should be way smoother, especially when configuring grub is automated.

---

### Post by oldfred on 2013-08-26
You fixed the os-prober bug. Normally Boot-Repair added correct chain load entries to 25_custom.

Not sure about your Ubuntu entry. Are you really booting Ubuntu in BIOS mode with the fakeBIOS entry?
Boot-Repair can convert a BIOS install to UEFI boot by uninstalling grub-pc and installing grub-efi.

---

### Post by 1/0 on 2013-08-27
> **oldfred said:**
> Not sure about your Ubuntu entry. Are you really booting Ubuntu in BIOS mode with the fakeBIOS entry?
Boot-Repair can convert a BIOS install to UEFI boot by uninstalling grub-pc and installing grub-efi.

Well, I was booting with that option but I can't remember why I added it. I tried booting without it and it worked fine so I removed it.

I tried the boot-repair tool again and it boots ubuntu and Windoze but I get one problem when booting ubuntu; it can't mount /dev/sda4, i.e. the Windows equivalent to the / partition. It can mount it using my manually added config... Boot-repair created an [online log]("http://paste.ubuntu.com/6031566/"). It's not the worst problem ever but it shouldn't be that way and it is convenient to access the files from ubuntu, as I use some Windows software for school (cad, mathematical and materials science software).

Thanks again for your help by the way! Some good references you've collected. I guess this creates a lot of questions on the forum...

---

### Post by 1/0 on 2013-08-27
Somehow it works now. I hate not knowing what solved or caused the problem. Did some updates, fixed some other things and it works... for now.

---

### Post by oldfred on 2013-08-27
If Windows needs chkdsk or is hibernated (Windows 8 always is) then the Linux NTFS driver will not mount the NTFS partition. 
If you turn fast boot off that should stop the always on hibernation. And perhaps restarting Windows ran a chkdsk? After any resize it has to run chkdsk.

UEFI on its own is different than BIOS but manageable, but UEFI with secure boot as Windows 8 is configured becomes complex and then Ultrabooks with Intel SRT using RAID and dual video not directly supported has made install a lot more difficult with new systems.

---

### Post by 1/0 on 2013-08-27
Now I get what probably happened. I started Windows as a test and it started repairing (or something) during boot. I think it was after that that the windows partition mounted fine again. It probably didn't unmount properly. 

Fast boot is not enabled (afaik) and sadly it's only Intel HD4000 graphics.... I do understand that it's complex but it's always been complex. I remember trying to make Red Hat 5.0 (?) work on a 486 though it was made for a 386. Getting sound cards to work, printers aso. Changing BIOS is just another step but it really makes installation much more difficult. You reboot and nothing. Then using the live USB trying to repair, often having to chroot with all the steps necessary (someone really should make a simple script in order to chroot instead of newbies having to figure out the sudo mount -o bind steps). I tried the boot-repair tool a few times and somehow it didn't work for me until after I started adding things manually. On the short term, there should imo be something added about this either during install in the form of info or on the live USB in the form of e.g. boot-repair. GNU/Linux and especially Ubuntu need a smother solution that works on the long term no matter which system it is. If I understand the situation correct, most new computers (desktops/laptops) use UEFI...

---

