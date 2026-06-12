---
title: "Installer broke at 'installing Grub2' for solo boot Ubuntu"
date: 2017-12-13
forum: Installation &amp; Upgrades
---

### Post by scruffycrumpet on 2017-12-13
I have been pulling my hair out over this for a week now. 

I was attempting to install Ubuntu on my brand new HP Pavilion laptop and I Selected to wipe everything and install Ubuntu.
The installer worked as expected until it reached "Installing the 'grub2' package...". It kept giving the warning 
```
/usr/lib/ubiquity/frontend/gtk_components/nmwidgets.py:17: Warning: Source ID 28882 was not found when attempting to remove it
   GLib.source_remove(self.timeout_id)

```
over and over with different IDs.

I thought it looked similar to this thread [https://askubuntu.com/questions/392254/ubuntu-install-hangs-at-installing-the-grub2-package/392273](https://askubuntu.com/questions/392254/ubuntu-install-hangs-at-installing-the-grub2-package/392273)

After letting this run for hours and hours I eventually shut it off, and when i turned the machine on Ubuntu launched okay and I thought maybe I could fix it from within the system
 but then when I tried to install anything with apt i received a message
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```
which gives me this
```
setting up grub-efi-amd64 (2.02~beta3-4ubuntu7) ...
Installing for x86_64-efi platform.
```
...and then it just hangs there.

I have been looking at different threads, and seemingly no matter what I try, I get stuck on the line "Installing for x86_64-efi platform."

I tried running boot-repair, which also got stuck on the same line. The line "Installing for x86_64-efi platform" has been appearing in my nightmares and has caused me to consider getting counseling.
All this made me think maybe there's some security setting I have wrong on my computer, but I really don't know much about BIOS and UEIF. 
I've basically been changing settings and trying again for a week now.

Sorry if this thread is a bit of a train wreak, I have no idea what kind of information is useful for this type of problem, so here's a bunch of random information about my machine:

HP Pavilion x360 convertible 11m-ad0xx
Processor: intel pentium CPU n4200 
4G memory
F.09 BIOS version, insyde

---

### Post by oldfred on 2017-12-14
If a brand new system is it UEFI.
Are you installing Ubuntu in UEFI boot mode?

Is BIOS version latest for your HP?

Some of the older Intel low end chips required extra boot parameters, not sure if yours then does or not.
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+N4200+%40+1.10GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+N4200+%40+1.10GHz)

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kansasnoob on 2017-12-14
We need the link to a boot info summary produced by Boot Repair. When you run Boot Repair you'll be asked to write down the link. That link will likely provide most of the info needed. It would also be helpful to share more info about the laptop, like actual model or a link to HP system specs page.

---

### Post by scruffycrumpet on 2017-12-15
Okay so heres my boot repair link [http://paste.ubuntu.com/26187304/](http://paste.ubuntu.com/26187304/)

the model is the HP Pavilion x360 convertible 11m-ad0xx
[https://support.hp.com/us-en/product/hp-pavilion-11m-ad000-x360-convertible-pc/15551382/manuals](https://support.hp.com/us-en/product/hp-pavilion-11m-ad000-x360-convertible-pc/15551382/manuals)

---

### Post by oldfred on 2017-12-15
Are you able to boot from UEFI boot menu, often escape f9 with HP?
Your boot files look like they are all there and in correct places.

If not use Boot-Repair's advanced options and full uninstall/reinstall of grub.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

HP violates UEFI spec that says NOT to use description as part of UEFI boot.
And only valid description is "Windows Boot Manager".
You can boot with escape+f9 every time, but can create an entry that says Windows but actually boot Ubuntu.

You are not showing shimx64.efi which may be part of issue.


 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

So you can try this:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"

---

### Post by scruffycrumpet on 2017-12-16
ubuntu boots only when i have legacy mode enabled, though this line
```
  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
```
returns "EFI boot on HDD"

```
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"
```
throws a segmentation fault: (Core dumped)

I tried boot repair with the full purge and reinstall settings and followed the instructions here: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_mode)
and it told me to open a terminal and run 
```
sudo chroot "/mnt/boot-sav/sdb2" dpkg --configure -a
```
which then also gets stuck on "Installing for x86_64-efi platform."

---

### Post by scruffycrumpet on 2017-12-16
When i turn off legacy mode, I can't get ubuntu to boot or get the installer to boot from USB. Right now I think thats probably where I'm going to find the solution.

---

### Post by ubfan1 on 2017-12-16
You're pretty surely not booting sda in legacy mode: there is no MBR record on the disk, and it is gpt partitioned without a bios-grub flagged partition.  I'd add a "boot" flag to sda1, the EFI partition.  Not sure you'd need the  "-c" parameter for efibootmgr just to rename the existing ubuntu boot item.  Have you ever run sudo apt-get update  ?

---

### Post by scruffycrumpet on 2017-12-16
sudo apt-get update completes, but the problem persists. 

When i try to add a boot flag to sda1, fdisk doesn't have a command for adding that flag, and I cant install gparted without running dpkg --configure -a which crashes.

---

### Post by ubfan1 on 2017-12-17
In fdisk, that would be x to get to the advanced menu (m for help), then A to set the boot flag.  Not sure what to do about the dpkg,  maybe a corrupted file in /var/cache/apt/archives  ,
delete every deb file there and start fresh?

---

### Post by scruffycrumpet on 2017-12-19
When i tried deletng the deb files it no longer boots and im back with the same problem. setting the boot flag didn't seem to do anything either.

When I said i need legacy enabled, i mean this
[https://i.imgur.com/WqBLYyd.jpg](https://i.imgur.com/WqBLYyd.jpg)
more detail: [https://i.imgur.com/txkirF8.jpg](https://i.imgur.com/txkirF8.jpg)

earlier oldfred pointed out that shimx64.efi isn't present and I can't find any leads on how to fix that either.

---

### Post by oldfred on 2017-12-19
I think Dell is the only one that wants CSM/Legacy/BIOS mode on, but you still boot in UEFI mode. For some reason it loads extra drivers.
With all other systems the CSM mode then only boots in CSM mode and you cannot select UEFI boot.

You should only need shimx64.efi, if you also have UEFI Secure Boot on. While Ubuntu will boot and install with Secure boot on, you cannot add proprietary drivers as Ubuntu then cannot certify they are correctly signed. 

You must have originally installed in UEFI mode as you have this, and no BIOS boot loader in MBR from Boot-Repair report:
> 
    Boot files:        /EFI/ubuntu/grub.cfg

But you did not have /EFI/Boot/bootx64.efi.
Boot-Repair normally copies shimx64.efi as shim works for both Secure boot and standard UEFI boot. But you can manually copy grubx64.efi to /EFI/Boot and rename to bootx64.efi.
Many with HP have in past had to do that manually before Boot-Repair started copying shim.

Have you tried from Boot-Repair booted live installed in UEFI mode and total reinstall of grub from advanced options, not any autofix.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

      
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by scruffycrumpet on 2017-12-19
I dont seem to be able to enable or disable secure boot because I can only get it to launch with legacy enabled. I know I am still actually booting in UEFI, but the option to enable or disable secure boot dims out when legacy is enabled. when I try to boot with legacy disabled I just get to a black screen with a flashing cursor in the corner when I try to boot the installer off my usb.

I'm trying to rename files after i reinstall for the n-th time.

---

### Post by scruffycrumpet on 2017-12-19
I copied grubx64 and ran boot-repair agianIt still wanted me to run 'chroot "..." dpkg --configure -a' which still doesnt get past the nightmare line 'installing for x86_64-efi platform.'

---

### Post by oldfred on 2017-12-19
We have seen corrupted ESP. Or the FAT32 partition needs chkdsk if Windows or dosfsck from Linux. A very few have had to totally backup & then delete ESP and then recreate it.

change example with sdb1 to your FAT32/ESP.
       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sdb1
man dosfsck
 The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by scruffycrumpet on 2017-12-29
So i eventually figured out how to install it clean with this thread [https://askubuntu.com/questions/392254/ubuntu-install-hangs-at-installing-the-grub2-package/392273](https://askubuntu.com/questions/392254/ubuntu-install-hangs-at-installing-the-grub2-package/392273)

I needed to make a new partition with gparted in boot-repair and set a flag before it would work, but now it works.

---

