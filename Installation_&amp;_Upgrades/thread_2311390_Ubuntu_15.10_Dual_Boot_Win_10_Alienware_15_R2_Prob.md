---
title: "Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by hopjopper on 2016-01-26
Okay so i have been having a problem with post installation 

I boot into the live USB i install it using the Something else option(i have also tried the normal option)

I choose the hard drive and set up / and swap space, i also make sure to choose THAT hard drive for the mbr 

It installs 

The computer reboots and.....i get an error [COLOR=#111111][FONT=Ubuntu]"The selected boot device failed. Press any key to restart"

[/FONT][/COLOR]Windows works fine, but when i choose to boot the "ubuntu" option from bios, it always gives me that error 

Here is after i ran boot-info from the live usb , i also tried the boot-repair and nothing was repaired

I dont know what to do next, i am all out of ideas, i have searched EVERYWHERE for a solution ,  and NOTHING

Driving me crazy really 

Here is the boot-info pastebin (if it helps)

[COLOR=#111111][FONT=Ubuntu]paste.ubuntu.com/14675452/[/FONT]

[FONT=Ubuntu]However there is another problem , now even if i try to install other Linux distribution it doesnt load either

When i tried linux Mint it only gives me the minimal grub shell and does not load into Linux Mint either 

Before Ubuntu installation Linux Mint installation used to work fine [/FONT][/COLOR]

---

### Post by ubfan1 on 2016-01-26
Looks like you did a legacy install on a UEFI machine.  Some reading:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by hopjopper on 2016-01-26
nope i didnt install with legacy i installed with uefi option

and besides i have repaired the boot with boot-repair and the problem still persists

---

### Post by ubfan1 on 2016-01-26
Looks like boot-repair totally missed the  /dev/nvme0n1p1,... devices.  Since you have no bootloaders (neither MBR nor UEFI) on sda, do you have the /EFI/ubuntu/grubx64.efi, (and grub.cfg and shimx64.efi) on the nvme0n1p1 partition?  boot-repair suggests reinstalling the grub-efi-amd64-signed, but don't know if it's needed, or what it would do with it (maybe put on sda1?).  
  The efibootmgr report is also missing at the end of the boot-repair report, so that sort of implies to me that the live media is running legacy, so the install might have been legacy too.  If you have the files in /EFI/ubuntu, what choices do you get from the EFI boot menu (some function key at power-on) to give you a choice of boot options.  
  Can you boot off sda?  If so, you could install grub there, but unless you are really trying to keep grub off the nvme... device, it should make no difference where it's put.

---

### Post by hopjopper on 2016-01-26
i got into the nvme0n1p1 device and deleted the ubuntu folder

ive checked to see if i can find any other ubuntu files efi or cfg or otherwise and i have not found anything else 

the only choice i had got before said "ubuntu" and it always lead me to the "Selected boot device failed..." no matter if there was an installation or not

right now i removed ubuntu from the windows drive , and i quient frankly dont know what to do next because i already tried this,. i removed the ubuntu folder and reinstalled and even repaired the windows boot and reinstalled linux mint and ubuntu (seperately) and still gives me the same annoying error 

but the worst part is that i cant even install my previous Linux OS i.e Mint 

so now i am stuck without linux all together

and i definitely dont want to reinstall windows , i am really hoping not to go there. It would cause me an even bigger headache then this

unfortunately i dont have any other usb drives, i have checked this one 

but could it be a problem with the usb drive? maybe a faulty usb drive causing the problem?

i just cant make sense why both Linux Mint or Ubuntu wont install , even after i deleted and formatted everything

---

### Post by hopjopper on 2016-01-26
could it have anything to do with an updated bios? because a few days ago i did update my bios-firmware on windows

also if i do reinstall windows would it make a difference?(although i really dont want to go there , but if its the only choice i have...)

---

### Post by hopjopper on 2016-01-26
im trying to reinstall this again

should i create an EFI partition on the second hard drive?

ive got 500gb of root /
17000gb of swap

should i create a EFI partition also?

---

### Post by ubfan1 on 2016-01-26
I thought you had an (empty) EFI partition on sda.  It needs a FAT filesystem, and the boot flag.  The installer usually ignores where you tell it to install the bootloader, and puts it  on the first disk (usually sda, but not in your case).  You could have just copied the /EFI/ubuntu files over to the sda, they're just files.  There should be no need to install Windows again, its bootloaders are in another directory, /EFI/Microsoft/Boot/...  It's not a bad idea to copy all the /EFI directories to sda's EFI, just for backup.  It's good to have the latest firmware.  There should be a "check media" choice on the USB installer main menu to confirm the media is good.  It does not hurt to leave the /EFI/ubuntu files on the nvme disk either, they don't take up that much room.  Can you even boot off sda (a choice in the UEFI settings/BIOS boot order?

---

### Post by hopjopper on 2016-01-27
yeah i can boot off it but it always leads to that screen that says failed to boot

i am just running a boot repair now, and its taking a looooooooooooong time , installing kernel on sda1 , after i clicked in advanced separate option 

will see what happens after this, and i will post the paste bin 

also it seems i have two /boot/efi and /boot 

just waiting for this to finish

its currently "purge kernels then reinstall last kernel sda1(ins)"

---

### Post by hopjopper on 2016-01-27
okay when i try to create a /boot partition that is fat32 or fat16 the installer complains that it cannot mount a fat32 or fat16 partition on linux system

---

### Post by hopjopper on 2016-01-27
okay i think i may have solved this problem 

apparently in my bios there was an option that bios always loads with both UEFI and Legacy compatibility and give you the option to load your drives in both, and it was doing it all along, so i had to go into bios and turn it off because in default it was starting in UEFI but could discretely instantly switch during loading grub/windows etc so it had to be explicitly turned off

and it tried to discourage turning it off saying some disks will become invisible hence adding to the confusion

now my bios is running purely in UEFI and i am installing Ubuntu with all the right options , so hopefully it should work this time

before it started in UEFI but was always prone to switch to legacy the moment it detected the option and hence unknowingly you could be running legacy while installing UEFI because in boot options it starts in UEFI but is not required to stay in it

---

### Post by hopjopper on 2016-01-27
okay still doesnt work 

here is the paste bin from boot repair which i ran to try to fix this

[http://paste.ubuntu.com/14677078/](http://paste.ubuntu.com/14677078/)

---

### Post by ubfan1 on 2016-01-27
This latest report does look like it booted in UEFI mode, with the efibootmgr report at the end.  The EFI report has ubuntu in the first place, good.  Your sda is MSDOS partitioned, with the standard MBR grub,ignored,  but also contains a logical (?????) EFI partition, ignored.  The EFI files ubuntu should use are on the nvme... in /EFI/ubuntu.  You run the shimx64.efi, so secure boot should work (and turning it off should still work).  I think the sda setup is odd, but OK.  What errors do you get trying to boot?  Does grub start?  
  Some systems need things changed in a non-UEFI standard way to work (thanks very little, you vendors who know who you are).  Things like the name "ubuntu" might need to be changed to "Windows Boot Manager".  Things like the name of the shimx64.efi file change to bootmgfw.efi.  A trick that sometimes works on internal disks is to copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi (note name change), copy /EFI/ubuntu/grubx64.efi to /EFI/Boot/grubx64.efi (no name change).  On external media, the default location for the bootloaders is /EFI/Boot, so that might get invoked on some failures .

---

### Post by oldfred on 2016-01-27
Others have had issues with NVMe drives.
But your latest Boot-Repair report is only showing a BIOS install with MBR(msdos) partitions on sda.

I would try partitioning in advance with gparted, but you need to download the very newest gparted from gparted, to have a version that supports NVMe drives.

       AHCI’s replacement, NVMe
So maybe it is time to refresh on some not too familiar or oft-used linux administrative commands to see a bit more. The simple part is to look in "/dev/nvme*". The devices will be numbered and the actual block device will have an n1 on the end, to support NVMe namespaces. So if you have one PCIe card or front-loading 2.5" drive, you'll have /dev/nvme0n1 as a block device to format, partition and use.
gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Thread on Asus, but mentions Dell:
[http://ubuntuforums.org/showthread.php?t=2307273&p=13416829#post13416829](http://ubuntuforums.org/showthread.php?t=2307273&p=13416829#post13416829)
Has link to this:
[http://www.dell.com/support/article/us/en/04/SLN151664/en](http://www.dell.com/support/article/us/en/04/SLN151664/en)
> I found that DELL XPS users are facing a similar issue, but they can fix  this by using "nvme_load=YES" on the linux boot command.


I do not have NMVe, but use gpt partitioning for both UEFI & BIOS booted systems.
 If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

And I make the ESP- efi system partition first on a new drive or any second drive that I partition. But do not create duplicate ESP on same device. All systems share one ESP per drive.

---

### Post by hopjopper on 2016-01-27
what your describing sound very complicated and i dont know how to do it 

so i am going to try to first do this

i am going to install linux mint since that installs nice and easy

and then i am going to install ubuntu side by side with it 

and then delete linux mint but keep the EFI 

hopefully that would work

---

### Post by hopjopper on 2016-01-27
Okay that didnt work either

I give up , whoever designed the installation process is dufus

why is it that Linux Mint is able to install without any problems or tweaking? But Ubuntu is just pure retarded 

bunch of dumbasses , hopefully one day they take cue from Linux Mint how to create a simple installation process 

unbelievable , i have been trying for like 2 days now 

if it was a problem with Linux in general Linux Mint wouldn't install but it does so perfectly and easily without any problems , but Ubuntu which uses the same system cant seem to get it right, just absolutely useless and pathetic

and if they cant get the installation process right then i can imagine their whole OS must be standing on weak legs

and the most messed up thing is that even after i installed linux mint with EFI partition and it was working and loading fine and then installed ubuntu side by side with it, Ubuntu converted the boot space into fat32 and caused the same error as i stated above to occur with neither Mint nor Ubuntu able to be loaded

---

### Post by oldfred on 2016-01-28
Are you sure you installed Mint in UEFI mode?
As it would also have to have the FAT32 formatted partition with the boot flag to be the ESP - efi system partition.
After installing Mint posts new link to Summary report from Boot-Repair.

---

### Post by C0derBear on 2016-01-28
FWIW, I got Ubuntu 15.10 working stable on my wife's new Alienware 15 R2 over Christmas.

I too spent a lot of time on different initial directions, maybe wasted maybe not.

There are a couple caveats though.

1. Under no condition could I get the Killer-N WiFi to function. I probably spent most of two weeks working *just* on that. I got the driver going and tried a large variety of firmwares but nothing in the end worked. In the end I bought an Intel 7260 NGW off Amazon for 18$ from someone in Tucson and swapped in in. *instant* wifi, zero issues. **My 2c? Save yourself the heartache and swap the WiFi card out.**

2. I haven't figured out how to get the machine to resume from either sleep or hibernate, cleanly. It comes back quickly enough but soon after the drives go read-only. Kind of makes things totally non functional. I have completely disabled sleep & hibernate for now, and set the lid-close to shut the machine down. It boots off the NVMe drive cold in less than 10 seconds so it's not a HUGE deal, but it is a complete PITA for my gal to not be able to save a session and come back to it. :^(

3. **I had to blow away the Windows 10 install completely**, letting Ubuntu take over the NVMe drive 100% - no what I wanted initially BUT not an issue for my gal since she has no use for Windows at all. We just setup the AlienFX colors to cobalt blue all around and wiped the drive. I took a Clonezilla backup of the Windows image first though, so if we need to restore/return/whatever I can flip the system back easily enough. You MAY be able to get around this with a late enough GParted run to resize volumes. Maybe try USB-booting 16.04? If I'd had the Intel WiFi in when doing that I could have fetched GParted from the net while USB booted, alas that wasn't my situation.

Last, and least ...

4. She is experiencing an wacky bug in Nautilus, where attempting to delete a file causes the file browser to close (!). I don't know that it's not been induced by something she has installed, and I don't recall having that problem when I was working on it, so it may not be a global problem.

5. **Sometimes, after a grub update, the system "loses" the UEFI entry for Ubuntu and won't boot.** This isn't a huge deal, just use F2 to get into the BIOS and rebuild the Ubuntu entry from the shim64.efi loader.

Other preparations that happened ...

- turned off and uninstalled Intel Rapid Storage, set BIOS to UEFI instead of RAID mode (did this to Windows 10 before backup and wipe). If you dig a little on the 'net you can find out how to reset the low level disk drive for Windows after swapping the BIOS setting, without reinstalling. I don't have the details handy but it may only require going through boot-repair once after changing the bios. My procedures was basically a) uninstall Intel RST and all crazy stuff from within Windows 10, b) reboot into bios to change RAID mode to AHCI, c) boot and repair Windows so it was happy that way.

- setup AlienFX colors to taste, assuming they can't be changed in Linux

- Update BIOS (to 1.2.3)

- take all Windows updates / hardware updates / etc

- Clonezilla USB boot to make an image of the OS drive

- Install using Ubuntu 15.10 USB, completely wiping and taking over the NVMe drive

  ** addendum ** - forgot to say that I wiped and reset the partition table on the HDD to GPT and 100% ext4, for Linux use.

- Take all Ubuntu updates

- Configure EITHER graphics-drivers ppa *OR* NVidia Cuda 7.5, we went with the latter since she's doing Cuda/OpenCL development

- had intermittent crashes of 'plymouthd', solved by adding FRAMEBUFFER=Y to /etc/initramfs-tools/conf.d/splash file and then running 'sudo update-initramfs -u -k all'

- created a file /etcmodprobe.d/blacklist-ath10kpci.conf with the ath10k driver named to prevent loading of the Killer-N/Atheros driver, system was unhappy with that loaded and not used, maybe not needed now that we switched over to the Intel 7260 WiFi

- disabled hibernation and sleep, set lid-close to power-off, until that issue is resolved

Best of luck.

---

### Post by hopjopper on 2016-01-28
here is the pastebin 

[http://paste2.org/pe7xExND](http://paste2.org/pe7xExND)

---

### Post by hopjopper on 2016-01-28
> **C0derBear said:**
> FWIW, I got Ubuntu 15.10 working stable on my wife's new Alienware 15 R2 over Christmas.

I too spent a lot of time on different initial directions, maybe wasted maybe not.

There are a couple caveats though.

1. Under no condition could I get the Killer-N WiFi to function. I probably spent most of two weeks working *just* on that. I got the driver going and tried a large variety of firmwares but nothing in the end worked. In the end I bought an Intel 7260 NGW off Amazon for 18$ from someone in Tucson and swapped in in. *instant* wifi, zero issues. **My 2c? Save yourself the heartache and swap the WiFi card out.**

2. I haven't figured out how to get the machine to resume from either sleep or hibernate, cleanly. It comes back quickly enough but soon after the drives go read-only. Kind of makes things totally non functional. I have completely disabled sleep & hibernate for now, and set the lid-close to shut the machine down. It boots off the NVMe drive cold in less than 10 seconds so it's not a HUGE deal, but it is a complete PITA for my gal to not be able to save a session and come back to it. :^(

3. **I had to blow away the Windows 10 install completely**, letting Ubuntu take over the NVMe drive 100% - no what I wanted initially BUT not an issue for my gal since she has no use for Windows at all. We just setup the AlienFX colors to cobalt blue all around and wiped the drive. I took a Clonezilla backup of the Windows image first though, so if we need to restore/return/whatever I can flip the system back easily enough. You MAY be able to get around this with a late enough GParted run to resize volumes. Maybe try USB-booting 16.04? If I'd had the Intel WiFi in when doing that I could have fetched GParted from the net while USB booted, alas that wasn't my situation.

Last, and least ...

4. She is experiencing an wacky bug in Nautilus, where attempting to delete a file causes the file browser to close (!). I don't know that it's not been induced by something she has installed, and I don't recall having that problem when I was working on it, so it may not be a global problem.

5. **Sometimes, after a grub update, the system "loses" the UEFI entry for Ubuntu and won't boot.** This isn't a huge deal, just use F2 to get into the BIOS and rebuild the Ubuntu entry from the shim64.efi loader.

Other preparations that happened ...

- turned off and uninstalled Intel Rapid Storage, set BIOS to UEFI instead of RAID mode (did this to Windows 10 before backup and wipe). If you dig a little on the 'net you can find out how to reset the low level disk drive for Windows after swapping the BIOS setting, without reinstalling. I don't have the details handy but it may only require going through boot-repair once after changing the bios. My procedures was basically a) uninstall Intel RST and all crazy stuff from within Windows 10, b) reboot into bios to change RAID mode to AHCI, c) boot and repair Windows so it was happy that way.

- setup AlienFX colors to taste, assuming they can't be changed in Linux

- Update BIOS (to 1.2.3)

- take all Windows updates / hardware updates / etc

- Clonezilla USB boot to make an image of the OS drive

- Install using Ubuntu 15.10 USB, completely wiping and taking over the NVMe drive

- Take all Ubuntu updates

- Configure EITHER graphics-drivers ppa *OR* NVidia Cuda 7.5, we went with the latter since she's doing Cuda/OpenCL development

- had intermittent crashes of 'plymouthd', solved by adding FRAMEBUFFER=Y to /etc/initramfs-tools/conf.d/splash file and then running 'sudo update-initramfs -u -k all'

- created a file /etcmodprobe.d/blacklist-ath10kpci.conf with the ath10k driver named to prevent loading of the Killer-N/Atheros driver, system was unhappy with that loaded and not used, maybe not needed now that we switched over to the Intel 7260 WiFi

- disabled hibernation and sleep, set lid-close to power-off, until that issue is resolved

Best of luck.

i had the same problem with wifi in Linux Mint it didnt work there either, so what i did was hooked up my smartphone to the usb port and used usb thetering to get a wifi connection , simple, and i can use it anywhere i go as long as i bring the usb cable

and there is a wifi projection , i usually have my phone with me as well as my laptop so no hassles there

---

### Post by oldfred on 2016-01-28
Your sda drive is BIOS based.
But you seem to have UEFI boot thru the ESP - efi system partition on the NMVe drive's FAT32 partition.
Better if sda is also gpt partitioned for UEFI use.
Once you start using UEFI, you should not use MBR(msdos) anymore.

Another thread on Alienware.
[http://ubuntuforums.org/showthread.php?t=2311390&page=2&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&page=2&p=13430555#post13430555)

---

