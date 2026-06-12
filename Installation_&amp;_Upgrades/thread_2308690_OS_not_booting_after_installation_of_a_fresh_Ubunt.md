---
title: "OS not booting after installation of a fresh Ubuntu 15.10"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by Subhadip_Das on 2016-01-05
[FONT=arial]I recently installed ubuntu 15.10 on my desktop. After successful installation I rebooted the CPU. It was unable to boot from disk. I thought there might be some problem with the boot flag for my primary linux parition and checked/rectified manually using gparted. Again tried booting but no luck.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Next stage, I used boot repair and selected the recommended repair. It repaired successfully (At least thats what the logs saying). Again I rebooted the CPU, still the OS is not booting.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]POST giving an error "Reboot and select proper boot device or Insert Boot media in selected Boot Device and press a key"[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Badly stuck in this problem for past three days. Here's the pastebin log of boot-repair - - >[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/14408962/](http://paste.ubuntu.com/14408962/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Seek urgent help on this.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks,[/FONT]
[FONT=arial]Subhadip[/FONT]

---

### Post by ajgreeny on 2016-01-05
Can you press whatever key is needed for a one-time boot device change, often F11 or F12, and boot to Ubuntu from that?  Maybe you have not reset the boot priority device.

You may also have the boot flag on the wrong partition; it should be the EFI partition that carries the boot flag, in your case sda1 not sda2 so perhaps that is causing confusion as you have a boot flag on both at the moment.

With luck **oldfred** will appear on this thread as he is the expert with boot-repair on this forum.

---

### Post by oldfred on 2016-01-05
You show boot flag on two partitions. You can only have boot flag on one partition per device (drive).
So remove boot flag from sda2 with gparted, command line or whatever tool you like.

Then as ajgreeny suggests can you boot using one time boot key the ubuntu entry in UEFI boot menu?

What brand/model system? 
Acer requires you to set trust on grub boot files. 
Many systems modify UEFI to use description on only boot "Windows" description. We either copy shimx64.efi to bootx64.efi or rename the Windows entry in UEFI to really boot shimx64.efi. 

You also show Windows folder in ESP - efi system partition and have some obsolete entries in UEFI. UEFI has NVRAM and remembers old entires. You may want to house clean. 

Details in link in my signture if desired.

---

### Post by Subhadip_Das on 2016-01-08
I again did a fresh installation of Ubuntu 14.04 without changing the defualt options. (Erase and Fresh install). Still no luck.

Hardware is Lenovo Thinkstation C30. 

Tried booting directly from HDD by F12. No luck,

I tried the advance options of boot-repair to make things proper by disabling secure boot, changing the name to bootx64.efi, no luck. 

I am not sure about how I can clean the NVRAM as efi config is not running as expected on the system. boot repair logs can be found here --> [http://paste.ubuntu.com/14436323/](http://paste.ubuntu.com/14436323/)

I am soo confused as I am unable to find any problem in the installation and with the live CD. Not sure what I missed. I will greatly appreciate you guy's help in solving this. Let me know if you need more information about this.

---

### Post by oldfred on 2016-01-08
I do not see an entry in UEFI to boot default hard drive entry.
Some UEFI on a reboot or two will automatically add that.

Or you can create an entry with efibootmgr from live installer:
To see entries
sudo efibootmgr -v
Add entry
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
confirm new entry exists:

 sudo efibootmgr -v
Use new entry to boot from UEFI or one time boot key.
      
 Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

Most of these Lenovo threads are laptops, but UEFI may still be similar. Do you have a UEFI setting that locks boot order?

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
      
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

