---
title: "[SOLVED] Unable to dual-boot Ubuntu and Windows 10 with two drives"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by lucas-sg on 2018-04-27
Recently I decided to install Ubuntu LTS on my desktop PC which already has Windows 10 on it. I read a few tutorials before installing and downloaded the .iso image of Ubuntu 18 LTS. But after installing Ubuntu, my PC won't recognize the drive on which I installed it. Here are some hardware details and some measures I took before and after installing Ubuntu:

_Hardware:_
[LIST]
[*]Motherboard: ASUS B350M-A Prime
[*]Drive 1 (C:): 120GB SSD WD
[*]Drive 2 (D:): 500GB HDD WD
[*]There is one partition for the C drive and two partitions for the D drive. The C drive has Windows 10 in it and the D drive has all my documents and programs that I use with Windows in one partition. The other partition was just made for Ubuntu or a different Linux OS.
[/LIST]
[U]
Before/during installation:[/U]
[LIST]
[*]Burned the Ubuntu image into a USB flash drive.
[*]Disabled secure boot by deleting the PK in UEFI before installing. I followed the instructions in this link for this:
[https://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility](https://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility)
[*]When installing Ubuntu I chose "Do something else". Then I selected the 'free space' I had allocated for Ubuntu and made three partitions: root (30GB), swap (10GB since I have 8GB of RAM and I read that people recommended a bit more than you have on RAM) and the rest for the home partition. Then in the *select a bootloader device* section, I chose to use the root partition and I installed Ubuntu.
[*]Just for more details for anyone interested, the partitions were all set as Logical and ext4.
[/LIST]
[U]
After installation:[/U]
[LIST]
[*]Since GRUB didn't load after reseting, I decided to manually choose (in the UEFI) the HDD (D:) I installed Ubuntu on. But the UEFI didn't allow me to boot from that disk since it didn't recognize any OS. So I looked for more threads about dual-booting Windows 10 and Ubuntu on two different drives and I stumbled upon this link:
[https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)
I followed those instructions and installed Ubuntu once again, deleting the old partitions I had just made for Ubuntu and creating new ones but this time making also an EFI partition (700MB).
[*]This didn't work either, my PC kept booting Windows again. Again I tried to reset it and choose manually my D: drive, but this time, instead of not recognizing any OS at all, it booted Windows 10! Remember that this is not the drive that had Windows 10 installed in it, it was just a hard drive with all my programs and documents, Windows 10 is still installed in my SSD. And this is the same drive onto which I installed Ubuntu. I looked more into why GRUB wasn't loading up and I found this as a possible solution:
[https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)
I wrote the command it told me to write but nothing changed.
[/LIST]

In conclusion, I do not know what to do anymore. How can it be so hard to install Ubuntu on a different drive than Windows 10 and dual boot at the same time? I'm guessing the one causing problems here is Windows with its bootloader. Either way I would love it if anyone could come up with a possible solution for this.

PS: No, deleting Windows 10 and just using Ubuntu is not a solution for me. Deleting everything that's on the D: drive and use it just for Ubuntu isn't either. As of now I'm using Virtualbox to run Ubuntu but I wish I could install it and have it run smoothly on my PC.

---

### Post by oldfred on 2018-04-27
Are you installing in UEFI or BIOS boot mode. To gpt partitioned drive?
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Are these your issues, some should be fixed by now.

 ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

### Post by lucas-sg on 2018-05-09
Thanks a lot! Figuring out whether I was installing the correct mode (UEFI or BIOS) with my Windows installation and checking whether the drives were GPT solved my issue.

---

