---
title: "Windows 7 Ultimate + xubuntu 12.04 LTS  on UEFI Mother board (P8B75-M) from USB stick"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by InuY4sha on 2013-03-10
After having spent one day looking around on different forums to get hints on installing the subject's described dual-boot OS environment I'd like to provide my experience on the subject.
[SIZE=5]Windows Installation[/SIZE]
[SIZE=4]First method through UEFI booting (FAILURE)[/SIZE]
fdisk formatted FAT32 bootable USB stick;
Assume you get the device named /dev/sdb (and partition /dev/sdb1 mounted on /mnt/sdb1)
mount iso:
```
mount -o loop windows_7.iso mycreatedfolder/
```
copy iso content to the mounted partition:
```
cp -r mycreatedfolder/* /mnt/sdb1/
```
copy efi/microsoft/boot one level up
```
cp -r  /mnt/sdb1/efi/microsoft/boot  /mnt/sdb1/efi/
```
copy bootmgr.efi (reading around they name it bootmgfw.efi, but within the ISO it was not named like that) into the  /mnt/sdb1/efi/boot/ renaming it "bootx64.efi"
```
cp -r  /mnt/sdb1/bootmgr.efi  /mnt/sdb1/efi/boot/bootx64.efi
```
reboot and force booting from UEFI: USB stick start from the bios.
With this method I got to see the usb stick as UEFI booting device, got into booting and saw the windows "pressed any key to start installing". After that I directly jumped out of the installation and were asked to "insert any media and press enter".
I believe my failure is due to a bad bootmgr.efi booting file which is probably not capable to correctly start Windows 7 installation. Anyhow I'm going to reiterate on this procedure to better describe it.

[SIZE=4]Second method with WinUSB(SUCCESS)[/SIZE]
I downloaded winusb package and started it by following [this]("http://shuffleos.com/5053/winusb-bootable-windows-installer-usb-ubuntu-linux/") post.
After I completed the installation on the usb stick, I unplugged/plugged and  I did rewrite the MBR with mbr package:
```
apt-get install mbr
install-mbr /dev/sdb
```
Then I rebooted and forced bios to boot directly from USB stick (NOT UEFI:!). This took me to a screen where I saw the text "MBR:" I happily started pressing some keys and eventually (somehow) got to press the sequence "A" and "1". Those keys started the Windows 7 installation procedure (I know it's funny but it was at the same time effective!).

Once installation was complete I could start and login onto Windows 7.

[SIZE=5]Xubuntu 12.04 Installation[/SIZE]
Again I used a fdisk formatted FAT32 bootable USB stick; This time I took advantage of UEFI booting which is much easier to get on linux.
Assume you get the device named /dev/sdb (and partition /dev/sdb1 mounted on /mnt/sdb1)
mount iso:
```
mount -o loop xubuntu_12_04_x64.iso mycreatedfolder/
```
copy iso content to the mounted partition:
```
cp -r mycreatedfolder/* /mnt/sdb1/
```
Reboot and force booting from UEFI: usb stick from bios.
From xubuntu menu select "Try xubuntu..."
When you login linux will not recognize Windows 7 formatted system partition. The issue is that Windows 7 formats the disk as "GPT" which - as I read here and there - "confuses" the installer partition manager.
To have linux recognize the disk and as consequence the windows partition(s), you need to get "fixparts" package (you need an internet connection):
```
sudo apt-get install fixparts
```
Then run fixparts on your hard drive (e.g. /dev/sda) like explained in [here]("http://www.rodsbooks.com/fixparts/"):
```
fixparts /dev/sda
```
A message like the fo
```
NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):
```
Press "Y" and you should see some magic automount bringing to life your windows partitions.
Now press "w" to write the MBR on disc and make it bootable (Hence not requiring boot from windows UEFI partition - or this was my understanding -).
If you now start installing Xubuntu it will detect the Windows 7 installation and ask you to perform linux installation aside of windows. Do it automatically or manually as you are used to.
Reboot and you again will ONLY see windows :(.
To complete the installation you need GRUB-2 to tell the /dev/sda MBR that the partition to start is the linux one - and not the windows one - and recognize all the other OS arounds and offer them to you. In order to achieve this, you will need to start xubuntu live, booting on the UEFI:usb stick from bios and selecting "Try Ubuntu...".
Once logged in you need to 
1) mount the linux root system partition (e.g. /dev/sda3) :
```
mount /dev/sda3 /mnt
```
2) Install grub as the MBR of the disk:
```
grub-install –root-directory=/mnt  /dev/sda
```
Reboot and you will have your grub menu asking you to login on xubuntu or windows 7 :)

Note that I also tried to install Windows 7 *after* the Linux installation, but this was not possible because Windows 7 asked me to remove all existing partitions in order to install its GTP disk type whatever. So to my understanding, I can't install windows 7 the way I did without having to erase the linux partitions. (maybe there are other ways or the Windows 7 UEFI installation doesn't complain but in the procedure described in Windows Installation -> Second Method, I could not install Windows 7 until I did not remove the existing partitions. Basically Windows 7 wants to manage the whole disk on its own and you have to please it (at least during the installation).

So a summery of the odd things I found:
1) The boot from UEFI in Windows 7 did not work for some unknown reason
2) Windows 7 did not accept other existing partitions during installation
3) Xubuntu did not see the Windows partitions until I forced deletion of the Windows GTP signatures in the disk.
4) In order to bring again back to life the two OS, you need to install the MBR on the disk (with **fixparts**) and reinstall grub with **grub-install** from the live xubuntu environment.

I hope to have been of some help to other people, but in any case it was a good exercise to have future notes to follow just in case of any of the so-common blue screens of death ;)
R

---

### Post by oldfred on 2013-03-10
Thanks for the info.

Anytime you install Windows in MBR mode, you have to use fixparts to remove backup gpt partition table. Windows only converts gpt primary table to MBR(msdos) and leaves backup gpt table at end of drive.

Just some info on UEFI.
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

 Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.


 Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


Windows has to be booted in UEFI mode to install in efi mode.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

