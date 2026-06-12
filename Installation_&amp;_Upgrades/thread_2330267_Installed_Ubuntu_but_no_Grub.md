---
title: "Installed Ubuntu but no Grub"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by sjsawyer on 2016-07-09
I have installed Ubuntu 16.04 from a USB onto my Acer Aspire R5-471, but I am unable to access the Grub menu. I have even run Boot-Repair from a disk but it am still unable to access the grub menu. Additionally, I have disabled fast-booting (some new feature on windows) and secure-boot. I have also tried the command

```

sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

and received the warnings/error:

```

grub-install: warning: this GPT partition label contains no BIOS Boot Partition
grub-install: warning: Embedding is not possible. GRUB can only installed in this setup using blocklists. However, blocklists are UNRELIABLE and their use is discouraged.
grub-install: error: will not proceed with blocklists

```

After some additional research I ran the command as --force but still have no grub menu appearing.

Any suggestions? I think it might have something to do with my system's GPT or UEFI

---

### Post by grahammechanical on 2016-07-09
With UEFI and GPT and Ubuntu installed in BIOS/Legacy/CSM mode we need a bios_boot partition for Grub to install itself into. With Ubuntu installed in EFI mode we need an efi_boot partition (ESP). 

When Windows 8/10 is pre-installed the Windows installer will create an efi_boot partition that the Ubuntu installer will use to put the Ubuntu efi boot files into. There is space for them and the Windows efi boot files do not get over-written. But Ubuntu will need to be installed also in EFI mode for this to happen.

Regards.

---

### Post by oldfred on 2016-07-10
Acer UEFI is unique in that you have to go into UEFI, set supervisory password (do not lose that), and set "trust" on Ubuntu/grub .efi files in ESP.

Some older threads on Acer suggest downgrading UEFI to older version. But even newer say to upgrade to very newest and it will work.
So make sure you have newest UEFI from Acer for your system.

[URL="http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742"]http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742
[/URL] [http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 


 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912) 
      
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by sjsawyer on 2016-07-11
Thank you! All I had to do was indeed set "trust" on the Ubuntu/grub .efi files. After rebooting, they appeared under the "Boot" menu of the UEFI/BIOS and I simply moved grub above the windows boot manager. Now grub comes up immediately.

---

