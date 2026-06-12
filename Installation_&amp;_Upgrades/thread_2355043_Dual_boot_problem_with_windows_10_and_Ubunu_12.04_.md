---
title: "Dual boot problem with windows 10 and Ubunu 12.04 LTS"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by monssaf10 on 2017-03-08
I am new to Ubuntu and I wanted to dual boot my laptop Hp dvEnvy 7 that already had windows 10 on it. when installing Ubuntu with a usb, I was prompted with a program that could partition my disk. I just deallocated 100Gb from the Windows partition and and gave 2Gb to a swap region and the rest to Ubuntu. After restarting everything worked fine and even Windows worked fine. However, when I decided to update Ubuntu to the latest version, Ubuntu still worked, but I can't access windows without and alternating black and white screen. 

Here is the link that boot-repair gave me: http:/paste.ubuntu.com/24142029

---

### Post by oldfred on 2017-03-08
You have an UEFI system.
And both Windows & Ubuntu installed in UEFI boot mode.
But you also have a Windows type BIOS boot loader in gpt protective MBR that will never work.
Only boot in UEFI mode.

You should be installing 16.04. There have been a lot of improvements since 12.04 especially in UEFI and drivers.
But only use Something Else install option, booted in UEFI mode, and choose same / (root ) as new /. 
And make sure you have newest UEFI from HP as vendors also have made lots of improvements in UEFI and how well it works.

But HP has not been dual boot friendly.
       Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
[/URL]
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

Also with Windows 10 make sure fast start up is off.
      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    [URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

### Post by ubfan1 on 2017-03-08
The boot flag is missing on the EFI partition, Windows isn't even seen in grub (except for the recovery), so I'd guess it was left hibernated so the disk could not be mounted by Ubuntu.  Try boot ing Windows through the EFI menu (some function key at power -up), and choose Windows.  Set the power options to not use fast-startup, and make sure you shutdown, not hibernate.  Rerun sudo update-grub in Ubuntu, and see if that lets Windows show up again.  Secure boot will have to be off to boot Windows through grub.  HP might need all sorts of non-UEFI modifications to the name of shimx64.efi to bootx64.efi and maybe even the name "Ubuntu" to "Windows Boot Manager".  Why are you starting with 12.04, UEFI was much better supported in later versions.  Use 16.04 for a Long Term Support version.

---

### Post by LostFarmer on 2017-03-08
Which MS Windows entire are you selecting ?  the correct one is labeled "Windows UEFI bootmgfw.efi"

---

### Post by oldfred on 2017-03-09
Another issue I now see is that your hard drive is shown as sdb.
In UEFI mode grub only installs to the ESP - efi system partition on drive sda.
But your ESP is shown as sdb2.

Not sure what the installer does, it may just install /EFI/ubuntu back onto the flash drive since it is FAT32 and seen as an ESP.
You would then need to copy that from flash drive to hard drive's ESP, before rebooting after install with continue testing.

---

### Post by LostFarmer on 2017-03-09
oldfred--> Another issue I now see is that your hard drive is shown as sdb That is the same with my laptop and it is no problem, the installer will use sdb1 (my internal hdd's ESP partition), even if I tell it not to.

The OP's problem is MS Windows will not boot, linux is good.

---

