---
title: "windows not recognized by grub"
date: 2018-10-01
forum: Installation &amp; Upgrades
---

### Post by copperly on 2018-10-01
So I have a Lenovo IdeaPad 15-abr with an AMD fx-9800p processor and a Radeon r7 graphics card. I had Linux Mint 19 dual booted with windows 10 on a two terabyte hard drive. I then decided to install fedora workstation 28 and did a manual install putting the swap root and home on Linux mints. I also put the bootloader on dev/sda1 which was an EFI partition. After finding out that #1 my trackpad didn't work on Fedora and that Windows 10 was no longer in my grub boot menu I installed ubuntu 18.04 over fedora the same way as last time. The trackpad issue was fixed but now I don't even get a grub menu on startup (probably because Ubuntu would be the only one on it) I have tried using boot-repair and got this error 

"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as GParted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/EFI partition:] option."

Here is my boot info summary from boot repair, at the end seems to be something of value about unhiding windows or something.
[https://drive.google.com/file/d/1O9RkSx62l94oF4goLJbstRm2Ve6fd4IB/view?usp=sharing](https://drive.google.com/file/d/1O9RkSx62l94oF4goLJbstRm2Ve6fd4IB/view?usp=sharing)

---

### Post by oldfred on 2018-10-01
You have an UEFI system and systems installed in UEFI boot mode.
But seem to have an old BIOS Windows boot loader in MBR that will not work. As long as you do not attempt to boot in BIOS/CSM/Legacy to use the BIOS boot loader you are ok.

But if Boot-Repair is asking for a bios_grub partition, you are in BIOS boot mode.That partition is only required for grub install in BIOS boot mode to gpt partitioned drives. Windows requires gpt for UEFI boot. 

You also show Windows is hibernated or fast start up is on. Grub only boots working Windows, so will not boot a hibernated Windows. But with UEFI you can directly boot Windows from UEFI boot menu, but with various Lenovo models, may be f8, f10 or f12.

Directly boot Windows from UEFI and turn off fast start up. Make other repairs if necessary.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If booting Ubuntu live installer or Boot-Repair always boot in UEFI boot mode.
How you boot install media for both Windows & Ubuntu is then how it installs or repairs. 
Since system is UEFI, only boot in UEFI mode. The boot choice of your flash drive is somewhat independent of settings in UEFI for installed system.

---

### Post by copperly on 2018-10-01
alright, so I went into my bios and made sure I was booting in uefi, I also changed the boot order with ubuntu first then windows, and when I tried to boot into windows to change the fast boot from the boot menu it booted me into ubuntu instead.

---

### Post by oldfred on 2018-10-01
Grub will only boot working Windows. Or Windows that does not have fast start up on.

You have to boot Windows directly from UEFI boot menu. And may need to get into Windows internal repair console. Or you have to boot a Windows repair flash drive or installer that has the repair console.

---

### Post by copperly on 2018-10-01
I have a windows repair disk, what exactly do I need to do?

---

### Post by oldfred on 2018-10-01
This is an Ubuntu forum.
this user posted some commands.
[https://ubuntuforums.org/showthread.php?t=2105418](https://ubuntuforums.org/showthread.php?t=2105418)

---

### Post by copperly on 2018-10-02
YAY! I can now chose between windows and ubuntu on boot! my grub menu was turned into kind of an eyesore, it added a million different options to boot including some residual files from fedora. Is there a way I can make this just ubuntu and windows (and the advanced options, and one more that I can't remember, but I had four options originally)?

---

### Post by oldfred on 2018-10-03
If they are from Boot-Repair adding entries:
       [http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 
    
If UEFI entries, it could be like this which is about removing Ubuntu.
       Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

