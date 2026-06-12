---
title: "installed ubuntu 16.04.3, now can't boot ubuntu 17.04"
date: 2017-08-29
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2017-08-29
Hi, I had a 17.04/windows 10 dual boot working nicely.
I removed the 17.04 / windows 10 drives, installed 16.04.3 on a third drive, all went fine - 16.04.3 installed ran etc. well.
I then reconnected the 17.04 and win 10 drives.
Now I can boot into 16.04 and windows 10 but not 17.04.  
I can see the 17.04 drive in 16.04 and windows 10, so i don't think there's a flakey connection or any hardware related problem like that.
When I attempt to boot into 17.04 (selecting the boot record of that drive from the uefi), I boot into windows.
If I disconnect the 16.04 drive and attempt to boot into 17.04 I get stuck at a blank screen with a blinking cursor.
1. Any advice? 
2. When I get a chance, I'll attempt to copy the files off the 17.04 drive from within 16.04.  Rather than resuscitate 17.04, I would then like to install a new copy of 16.04 onto that drive, leaving the existing / new 16.04 in place.  How do I do that?
I would really like all three systems (win 10 + 2* ubuntu 16.04), booting independently (each off it's own distinct drive).
Thanks for any help.

---

### Post by oldfred on 2017-08-29
IF UEFI, you just about cannot have them boot separately.

I have several installs of Ubuntu on sda & sdb and they all install grub to the ESP - efi system partition on sda in /EFI/ubuntu. So each overwrites the previous and you dual boot from one default and have all the others in your grub menu. I quickly learned to back up ESP and restore default  or my main working install's settings back into the ESP. It really is only a 3 line grub.cfg that calls the full grub config in an install.  

I do add an ESP on all drives. I have not tried, but you may be able to manually install grub to sdb and manually maintain a grub.cfg to boot the install on sdb.

You have to make sure all installs are UEFI as UEFI and BIOS boot is incompatible. Once you start booting in one mode you cannot switch. Or grub only boots other installs in same boot mode. You have to boot from UEFI boot menu if not in same boot mode.

If you have more than one drive or more than one install, best to learn to use Boot-Repair and its summary report. Then you have a better understanding of what is installed where, plus some documentation of configuration.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Hodor on 2017-08-29
Hi Fred,
Thank you.
Link to report below - some uuids anonymised, hexdumpts removed, let me know if your need this.
Is there a good guide to dual booting you can point me to? Is there something on the esp-efi system partitions, how to back up etc (I'm moderately it literate and apparently need to know this stuff a little better).
It's uefi, but ASRock uefi /bios is pretty helpful.
I would like to install two ubuntu 16.04.03 on separate drives (1 me programming, 2nd: daughter minecraft modding), they can share a grub if needs be.
I need to be able to choose grub vs windows boot in uefi, as I have to turn some hardware off for ubuntu/linux but on for windows.
I'm now no longer able to boot yesterdays installation after reconnecting the drive - I can't get the boot option to appear in the uefi, only the broken link to 17.04, but all the work is backed up so I'm happy to torch the lot and start again.
Kind regards,
Hodor



[https://paste.ubuntu.com/25428779/](https://paste.ubuntu.com/25428779/)

---

### Post by oldfred on 2017-08-29
UEFI forgets its NVRAM saved entries if you disconnect a drive.
You can use efibootmgr to add entries back again.
To see entries. This may not work on your BIOS/MBR installs. Or live install in BIOS boot mode. But I just noticed that Boot-Repair in BIOS mode is showing entries, so they may have updated BIOS install to include efibootmgr since most new computers are UEFI.
sudo efibootmgr -v

You are showing mixed UEFI/BIOS and mixed MBR(msdos)/gpt(GUID) installs.
And then you can only boot UEFI installs from UEFI boot menu, not from grub. Grub only lets you boot other installs in the same boot mode as you start to boot. Grub should let you boot BIOS installs.

You show grub installed to both the MBR of sda and the MBR of sdb. I cannot tell for sure, but it looks like each grub boots the install on that drive.
And you have Windows booting in UEFI boot mode from sdd.

I typically suggest that if you have UEFI hardware you install Ubuntu in same boot mode as Windows. And if multiple drives always use gpt for any Ubuntu drive and include both ESP - efi system partition for UEFI boot and bios_grub partition for BIOS boot. Then you can install in one mode but later easily switch as you have correct partitioning for UEFI.
Only Windows in BIOS boot mode has to have the now 35 year old MBR(msdos) partitioning scheme.

Unless installs are brand new, you may want to keep them as BIOS/MBR boot. But if reinstalling I would at minimum convert drives to gpt and add ESP & bios_grub.

One problem with multiple drives is that grub only installs to ESP on drive seen as sda. Since your sda is BIOS it makes it difficult. There is a way to add a FAT32 partition in somehow flash it as an ESP, but booting in UEFI from MBR is very unusual. But installer is both BIOS & UEFI from FAT32 and USB flash drive can be MBR or gpt.
Since Boot-Repair sees UEFI & possibly secure boot on, it wants to install grub-efi-amd64, but that will fail since you have BIOS.

Because you disconnected drive UEFI may have remembered settings for Windows and that is why it is booting. It should be using GUIDs, but I do not know how UEFI enumerates BIOS boots.
You should be able to in grub/Ubuntu that does boot just run this & boot both BIOS Ubuntu installs:
sudo update-grub 

Only if wanting to start over, I would have Windows in SATA0 on motherboard, so it is sda, and then each drive in SATA port order skipping no ports. And do not have a DVD in between any SSD or HDDs. And then have all drives as gpt & all installs as UEFI. 
But disconnecting Windows drive may cause UEFI issues? Most UEFI seem to find Windows, but need help re-finding Ubuntu.

Not sure then which options you want to try. I would first just run sudo update-grub in working install.

---

### Post by Hodor on 2017-08-30
Thanks,
I don't currently have a working Ubuntu installation (other than a live usb).
I would rather not leave my windows drive in place whilst installing Ubuntu - if I mess something up I will have a lot of problems. (I should have mentioned that my Windows installation is on an SM951 drive that uses a pcie gen 3*4 interface, not sata.)
In the past, I've: removed the windows drive, installed Ubuntu on a separate drive, reconnected the windows drive and presto, a dual boot (maybe a bit of tweaking I don't recall; I have just now backed up my Boot Configuration Data in windows).
Can I not do that again?

Maybe I need to ask on a windows forum, but if my drive with the Ubuntu 17.04 installation is all correct (the uefi interface on my mobo sees this data, eventually when it's connected), can I not populate the Boot Configuration Data with appropriate values to boot into that system from the uefi interface?
Is my situation something like this: the Ubuntu 17.04 installation on the drive is fine, the mobo UEFI interface sees the boot record and populates the boot options menu with this choice, but now when I select that choice, the UEFI interface attempts to find the location of the boot loader via the Boot Configuration Data which no longer has the correct details (Windows rebuilds the file on rebooting with the windows drive reconnected - correctly populating the Windows 10 values but ignoring Ubuntu), and so the attempted boot fails?

Kind regards

---

### Post by oldfred on 2017-08-30
Your UEFI entry works as it is a BIOS boot entry, not a standard UEFI entry.
Some systems used to require you to turn on/off UEFI or CSM/BIOS to boot in that mode. Many now will boot based just on entry in UEFI boot menu.

I think Windows entries may have worked as Windows does not chainload or directly boot Ubuntu. It forces a UEFI reboot, so then UEFI is really booting & then boot mode can be BIOS or UEFI. UEFI has a one time reboot setting.

Once you start from UEFI in one boot mode you cannot switch. Grub does not have a option to reboot into UEFI and boot another install in different boot mode.

Did you turn UEFI Secure Boot on? You cannot boot BIOS mode with Secure boot on.
Boot-Repair said this:
```
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
EFI in dmesg.
[    0.000000] ACPI: UEFI ... (v01 ALASKA A M I    01072009      00000000)
SecureBoot maybe enabled.
```

Still better to have your Ubuntu installs in UEFI boot mode.

---

### Post by Hodor on 2017-08-30
It works! Thanks very much (my daughter is very happy, me too).
Short: needed to set the HDD boot order priority in the UEFI interface correctly - previously, I'd been able to just choose a boot loader and ignored the HDD boot order.
Now, I need to select correct HDD order, and that way I can even get the new 16.04.3 install to boot (even though the boot loader is not showing up as an option in the uefi screen).
I do turn secure boot off for Ubuntu, and enable CSM legacy boot.
Sorry for the bother.

---

