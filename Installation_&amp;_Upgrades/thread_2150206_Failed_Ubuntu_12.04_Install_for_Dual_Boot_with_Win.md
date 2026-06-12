---
title: "Failed Ubuntu 12.04 Install for Dual Boot with Windows 8, LiveCD Boots Fine"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by andyg54321 on 2013-05-31
[FONT=Arial][COLOR=#000000]Hi, I'm trying to install  Ubuntu 12.04 to dual-boot with Windows 8 on my Asus X401ARF laptop. I  tried following the instructions here: [/COLOR][/FONT][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and have disabled everything it says in the BIOS. I let the installer automatically handle the partitions.

Neither Windows or Ubuntu boots from Grub menu. Selecting  Windows from Grub gives "error: unknown command `drivemap`. error: invalid EFI file path." Selecting Ubuntu from Grub just sits at a blank purple Grub screen without HDD activity. [At this point I was able to still boot Windows by using the BIOS' boot device list and selecting the HDD.]

I booted the LiveUSB and  ran Boot-Repair as suggested in instructions, it popped up a warning  about "EFI detected. Please check the options.", and then I selected the recommended repair and it seemed to complete fine. It gave me the URL  paste.ubuntu.com/5718834

After running Boot-Repair the behavior is the same as before for both Windows and Ubuntu. [One difference is that I am no longer able to boot Windows by selecting the HDD from the BIOS' boot list.]

If you could provide any insights it would be greatly appreciated.

Thanks,
Andrew

---

### Post by fantab on 2013-06-01
Have you set your BIOS boot options to load Ubuntu?
[QUOTE=BootInfo Summary]
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file![/QUOTE]

---

### Post by ubfan1 on 2013-06-01
To boot a preinstalled Windows 8, I think you will need "secure boot" enabled.  With secure boot enabled, the boot-repair program would probably do things differently -- use the .signed copies of grubx64.efi, and (hopefully, no experience here) suggest the Microsoft signed sda1/EFI/ubuntu/shimx64.efi instead of grubx64.efi (not signed by Microsoft, cannot boot with secure boot).  Don't know if the grub.cfg linux kernels would be changed by boot-repair to the "....signed" versions either, but really, grubx64 should be able to boot unsigned kernels too, so not sure what is lost without the .signed versions.  The Windows efi boot no longer works because the windows boot manager, bootmgfw.efi got renamed to bkpbootmgfw.efi, and a copy of shim put in it's place.  (boot-repair should be able to restore the backup files to their original names).  One vendor only boots from the bootmgfw, so the rename is meant to handle that.  The expectation is that all machines will boot windows from grub when the boot-repair fixes the grub commands, but in fact, several just wont, so the direct efi windows boot is still necessary for those (probably not you but check bug 1091464).

---

### Post by andyg54321 on 2013-06-01
> **fantab said:**
> Have you set your BIOS boot options to load Ubuntu?

I have set the BIOS settings as directed in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to the best of my ability, although some things were labeled slightly differently. Specifically "Fast Boot" is set to "[disabled]", "Launch CSM" to "[disabled]", and "Secure Boot Controll" to "[disabled]".

Should I re-enable one or more of these to boot Ubuntu?

Thanks!

Andrew

---

### Post by andyg54321 on 2013-06-01
> **fantab said:**
> Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

I think this may be OK as Grub does come up. I hope it is because I don't see how to set it in my BIOS.

Thanks again,
Andrew

---

### Post by andyg54321 on 2013-06-01
I tried booting in non-UEFI mode by setting "Launch CSM" to "[enabled]", which revealed a new option "Launch PXE OpROM", which I also set to "[enabled]".

Doing this made my USB install stick as two separate entries in the boot menu. One was UEFI as usual, but the other did not have that. I booted the non-UEFI version and tried to reinstall Ubuntu. Nothing changed. I rebooted the live stick and ran Boot-Repair again. It still seemed to do UEFI type of repair, but I'm not sure. At the next reboot the GRUB menu was somewhat "cleaned up", i.e. fewer entries with better names. But still no joy. I then disabled "Launch CSM" and booted to Grub. Ubuntu still fails with purple screen, but Windows 8 is able to boot again. So some small step in the right direction.

My new paste is paste.ubuntu.com/5722017.

Thanks,
Andrew

---

### Post by andyg54321 on 2013-06-01
> **ubfan1 said:**
> To boot a preinstalled Windows 8, I think you will need "secure boot" enabled.

Thank you. I don't believe secure boot was ever enabled, and I now have Win8 booting for the time being. See my previous post.

Thanks again,
Andrew

---

### Post by fantab on 2013-06-01
> **andyg54321 said:**
> I have set the BIOS settings as directed in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to the best of my ability, although some things were labeled slightly differently. Specifically "Fast Boot" is set to "[disabled]", "Launch CSM" to "[disabled]", and "Secure Boot Controll" to "[disabled]".

Should I re-enable one or more of these to boot Ubuntu?



This is not required. Disabling 'Secure Boot' IMO is a better option than having it enabled.
However ensure that your Windows is actually shutting down, and not 'Hibernating'. Windows8 is calling this feature 'Fast Startup'. [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


> **andyg54321 said:**
> I tried booting in non-UEFI mode by setting "Launch CSM" to "[enabled]", which revealed a new option "Launch PXE OpROM", which I also set to "[enabled]".

Doing this made my USB install stick as two separate entries in the boot menu. One was UEFI as usual, but the other did not have that. I booted the non-UEFI version and tried to reinstall Ubuntu. Nothing changed. I rebooted the live stick and ran Boot-Repair again. It still seemed to do UEFI type of repair, but I'm not sure. At the next reboot the GRUB menu was somewhat "cleaned up", i.e. fewer entries with better names. But still no joy. I then disabled "Launch CSM" and booted to Grub. Ubuntu still fails with purple screen, but Windows 8 is able to boot again. So some small step in the right direction.

My new paste is paste.ubuntu.com/5722017.



Non-UEFI will not work as for dual boot it is a MUST to have both OS in UEFI mode, for GRUB to work efficiently without any manual interfereing. By the way, PXE is for network booting, I think. Not relevant here.

Sometimes it can be that the current EFI partition can be corrupt. Here's a workaround: 

1) Use Gparted from Ubuntu LiveUSB/DVD and create another EFI partition (FAT32, 200MB, located in the first 100GB of the disk), move the 'boot' flag on it
2) Install grub-efi in this new ESP 
 [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)


However, before you apply the above workaround, I suggest you format Ubuntu partition and reinstall. Ubuntu MUST be installed in 'EFI' mode only to be able to boot in EFI mode.

---

### Post by andyg54321 on 2013-06-02
> **fantab said:**
> 

Sometimes it can be that the current EFI partition can be corrupt. Here's a workaround: 

1) Use Gparted from Ubuntu LiveUSB/DVD and create another EFI partition (FAT32, 200MB, located in the first 100GB of the disk), move the 'boot' flag on it
2) Install grub-efi in this new ESP 
 [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)


What are some ways I can tell if the EFI partition is corrupt or not corrupt (besides Ubuntu booting obviously)? Anything I can enter at a prompt or anything? It boots to grub fine, and it has reasonable menu entries, doesn't that indicate that more than likely the partition is OK?

Thanks again,
Andrew

---

### Post by fantab on 2013-06-03
It does indicate that the partition is ok.
Try Boot-Repair again from LiveDVD/USB. I suspect that GRUB is not reading GRUB-Files from your / partition. Reinstalling GRUB with Boot Repair using '[Advance Options]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options")' may help solve that.

If that doesn't help then 'REINSTALL' Ubuntu. Make sure you boot Ubuntu in EFI mode when installing (if booting in EFI then Ubuntu will show black screen with options, if not its purple).

---

### Post by andyg54321 on 2013-06-07
Tried installing Raring Ringtail in hopes that it would handle this UEFI stuff better. And it is just a touch better. Installed everything from EFI mode. Still had to do boot-repair. Grub now shows a purple screen (as before), one option to boot Ubuntu leads to a blank purple screen as before. This time there is an "Advanced options for Ubuntu" selecting that and then "Ubuntu, with Linux 3.8.0-19-generic" finally shows a little something it shows "Loading Linux 3.8.0-19-generic ..." followed by "Loading initial ramdisk ...", and is then hung. Recovery mode does the same thing. I added one more echo at the end of the grub script and it does hit that. Looks like it may be through grub and into a Linux kernel not starting issue.

---

### Post by oldfred on 2013-06-07
If you get grub menu you are past grub boot and it is having issues loading a driver. Most often video, but could be something else.

What video card/Chip?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

You can also use Boot-Repair to add nomodeset:

 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

---

### Post by andyg54321 on 2013-06-07
Machine is Asus X401A, with Intel B980 CPU. Ubuntu Live boots using i915 driver.

I've tried "nomodeset" and setting GFXMODE explicitly to the native resolution (may not have gotten refresh rate right), but there is no change in behavior.

Would like to see more of the kernel console boot messages, but "nosplash --verbose text" doesn't work. Not sure how to specify "single", "root prompt", or "resume" options as mentioned in the megathread link. Any help getting console messages would be appreciated.

Thanks,
Andrew

---

### Post by oldfred on 2013-06-07
Asus seems to have many models. Only one K555N so far seems to not work and it was a video issue.

Other Asus that worked.
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

Do you have the latest UEFI/BIOS? If using Intel many had to use this:
      
 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

      
 Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

---

### Post by andyg54321 on 2013-06-07
I've tried those to the best of my ability. I'll go back and retry and record what I try to make sure I cover all of them.

I. Since Ubuntu Live boots right up is there a way to pull the pertinent information from there?

II. I'm guessing there is no way to see the console error messages until the video driver is up? Does "single" or some other mode allow early access to these messages?

III. I've seen some say that this kernel version I'm using (3.8.0-19-generic) is no good. Could you please point me to how to install a newer kernel using Ubuntu Live?

Thanks again,
Andrew

---

### Post by oldfred on 2013-06-07
From liveCD you can run these:
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

You can remove quiet splash when you add nomodeset and it should show boot process. That same info is in log file dmesg in /var/log. Many other log files in /var/log. Also recovery mode use nomodeset.

I never have changed a kernel, so cannot help on that.

---

### Post by andyg54321 on 2013-06-08
[B]**** Thank you for all the help and support from the forum members! ****

[/B]I finally have my system booting Ubuntu. A combination of #1 and #3 turned out to be the key for me, although I'm not sure this is the best way to solve this.

This isn't the path I took to get there, but I believe the short recipe is:
1. Boot Ubuntu Live (USB stick).
2. Mount the Ubuntu partition on the laptop HDD, in my case with all the Win8 and UEFI partitions this was /dev/sdb9 (the last one)(USB drive took /dev/sda). So something like:
```

sudo mkdir /mnt/myubuntu
sudo mount /dev/sdb9 /mnt/myubuntu
```
3. Replace the generic Linux kernel on HDD with what appears to be "the EFI kernel" from the Live image.
```

sudo mv /mnt/myubuntu/boot/vmlinuz-3.8.0-19-generic /mnt/myubuntu/boot/vmlinuz-3.8.0-19-generic.orig
sudo cp /cdrom/casper/vmlinuz.efi /mnt/myubuntu/boot/vmlinuz-3.8.0-19-generic
```
*Note: Using the generic kernel name avoids editing the GRUB menus, no extra parameters or anything were required.*

4. Sync, unmount, reboot.
```

sync
sudo umount /mnt/myubuntu
sudo shutdown -r now
```
[End of short recipe]

As I say this may not be the best way. I could see that this might cause problems during future upgrades or when building kernel modules, but I'll cross those bridges when I come to them. If anyone knows of a better way please let me know.

In case the above recipe doesn't work the slightly longer path I took to get there included a couple of extra steps and reboots. Insert these steps above:
```

2.5 Copy /cdrom/casper/vmlinuz.efi to /mnt/myubuntu/boot, sync, umount, shutdown, remove Ubuntu Live USB stick, reboot and edit boot line in GRUB (at GRUB menu press 'e') to boot this kernel instead of -generic.
2.6 This booted Ubuntu for the first time from the HDD and I ran update-grub at some point, which updated grub.cfg to use "hd0" everywhere "hd1" had been, again due to USB drive I presume.
```
Continue with remaining steps from short recipe above...


[One more thing I learned was that the minimum GRUB-stuff I needed to boot my system was from the GRUB menu press 'c' to get a GRUB prompt then enter:
```

linux /boot/vmlinuz.efi root=/dev/sda9
initrd /boot/initrd.img-3.8.0-19-generic
boot
```
*Note: Assumes "root=hd0,gpt9" see [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) for more info.*]

[B]
**** Thank you for all the help and support from the forum members! ****[/B]

---

### Post by andyg54321 on 2013-06-09
One final note, I was able to build kernel modules and I was able to update to the 3.9 kernel following instructions here: [http://linuxg.net/how-to-install-3-9-kernel-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/](http://linuxg.net/how-to-install-3-9-kernel-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/)
The 3.9 kernel was able to boot. So I believe I am now back on a sanctioned path. It is probably possible to do the one-time boot using the vmlinuz.efi kernel (step 2.5 above) and then update to the 3.9 kernel.

---

