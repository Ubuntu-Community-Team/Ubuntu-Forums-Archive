---
title: "Unable to boot after install on Dell XPS 15 9560"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by newdev4ios on 2017-10-07
Well here is the deal... I was able to get kali linux installed on my external hdd a few months back and was able to boot it perfectly fine for a while...

well i just tried booting my kali linux drive a few days ago and it refused to boot, and i could do nothing to get it working... 

so i decided to reinstall linux, but this time i decided to install ubuntu...

well i was able to boot from the usb drive and have it install linux onto my external drive with no issues...

but when i go to boot from the drive it just gets stuck at the ubuntu with 5 dots below it screen with no animations or movement...

secure boot is off...
AHCI is enabled...
Legacy boot mode is enabled...
fastboot mode is set to thourough...
Bios version: 1.5.0
Current OS on internal m2.ssd: windows 10 (i keep this drive disabled whenever i try installing the linux or even try booting linux)...

Also i have the i5 model 4k touch
32GB RAM...
256GB m2.ssd storage... internal
External WD2500BEKT 250GB WD Scorpio Black drive
...

please help me thanks...

I really need a linux installation for school and the sooner it is fixed the sooner i can get back to working on my assignments...

---

### Post by oldfred on 2017-10-07
Are you installing to external drive in UEFI boot mode or BIOS boot mode?
Internal drive is UEFI if Windows pre-installed.
Are you partitioning external drive in advance with gpt and including an ESP - efi system partition?
And/or a bios_grub partition if you really want the now 35 year old BIOS boot configuration.

 Dell XPS 13 9560 install without issues (But internal drive)
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321) 


 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad
And Ubuntu's UEFI grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP on external drive.

---

### Post by luciuz on 2017-10-08
I have a similar problem with the Dell XPS 13, Ubuntu installs fine, and it reboots fine, but once you shut it down it won't boot again- just get No bootable device message.

I did some research on this topic, and according to this guy [https://youtu.be/kvsgTJbIWNo?t=229](https://youtu.be/kvsgTJbIWNo?t=229)  , GRUB is not configured to work with the NVMe SSD's present in these laptops. What seems to be necessary is removing GRUB in favor of systemd

There is a guide here: [https://gist.github.com/0x414A/7f1c27ac24f05a42ed43aa73946a7033](https://gist.github.com/0x414A/7f1c27ac24f05a42ed43aa73946a7033)  however it does not work with LVM/dm-crypt which I absolutely need so I am stuck as well.... If anyone could steer me to a guide on installing an alternative bootloader compatible with LUKS/dm-crypt it would be very helpful

---

### Post by oldfred on 2017-10-08
I have seen multiple posts of Dells with NVMe drives. But almost all required both Dell UEFI update and Samsung NVMe firmware updates.
Also seen grub boot many LVM installs.

       Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch) mega-thread
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)
[https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329](https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[URL="https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/"]https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/

[/URL]
 Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot 
[https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
Whole drive install erases ESP, LVM or full drive encryption fixed 2015
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323) 

[URL="https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/"]
[/URL]

---

### Post by newdev4ios on 2017-10-08
Im installing via UEFI mode, also i tried that second link and this time it just shows a black screen when trying to boot that way... (i am going to try again with a little modification...)

im going to try and see if i can install ubuntu 17.10 beta 2 and boot it... 

my internal nvme drive is disabled in bios so there should be nothing installing to my internal drive...

(last resort)...\/
im going to see if i can install linux to my internal drive and see if it boots, if it does then i will try cloning my internal drive to my external drive and see if that works...

im going to also clone my windows drive to my backup hdd before i do that so i can easily just clone it back... if needed.

---

### Post by oldfred on 2017-10-08
External drives do not boot the same way as internal drives.
Full install of Ubuntu installs grub to ESP - efi system partition on internal drive.
Grub installs to /EFI/ubuntu in ESP on internal drive.

But UEFI only boots from /EFI/Boot/bootx64.efi in ESP on external drive.
Both the Windows installer & Ubuntu installer use that name, but obviously different files.
I copy /EFI/ubuntu/shimx64.efi to & rename as /EFI/Boot/bootx64.efi on any external drive.
If grub2 UEFI boot loader installed to internal drive, I also have to copy all of /EFI/ubuntu to ESP on external. Shim or grub from full install expects to find more files in the ubuntu folder.

       UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad
And Ubuntu's UEFI grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP on external drive.

---

### Post by newdev4ios on 2017-10-08
ubuntu 17.10 beta completely failed to boot so im going to try to install 16.0.4.3 and see if that version works better...

also when i am installing the ubuntu (my external drive is shown as /dev/sda -- my internal drive is disabled so the computer doesnt see the drive at all when in Ubuntu or even booting...) so there should be no issues with the installer installing anything to my internal drive... there is no partitions from the internal drive beeing touched at all when i am installing or even booting to ubuntu/linux...

the drive when i reboot does show the ubuntu loader where it says boot ubuntu, advanced options, disk repair/system repair...

i will upload a video on youtube of what is happening and what i am doing... i will show what i am normally doing, then the way shown in the second link, and what happens...

i will have that probably in a couple of hours.

---

### Post by oldfred on 2017-10-08
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

And script does not parse ESP.
You should have in ESP.
/EFI/ubuntu
And this should have the UUID & gpt of the partition you install into. Its a 3 line configfile to the full grub.cfg in your install.
/EFI/ubuntu/grub.cfg
And if external you have to add this:
/EFI/Boot/bootx64.efi

---

### Post by newdev4ios on 2017-10-10
I won't be able to post any more replys(issues w/linux) for about 2-5weeks... 
For some reason my laptop just stopped recognizing any charger and so I have to send it to Dell to be fixed and it'll take some time for them to receive the package, to work on the laptop and then send it back, so now I have to use my desktop... (I will try to install Linux again when I get my laptop back and if it works I'll post so, and if not ill record a video of whats happening and upload it to YouTube and post the link here, but until then I can't do anything with it)

---

