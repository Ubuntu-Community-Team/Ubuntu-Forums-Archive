---
title: "Small problem on rebooting Ubuntu 14.04 dual boot with Win8.1 on Toshiba C70D laptop"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by zon14 on 2015-04-08
I've wandered over to askubuntu.com about how to dual boot Ubuntu with Win8.1, and already implemented most of what made sense there.  I turned off secure UEFI, and believe I installed both OSes that way, or at least reimaged Win8.1 like that.  Turned of fast boot in Win8.1.  Did the ol' bcdedit /set {bootmgr} path \EFI\boot\grubx64.efi in a normal command window(not the powershell) run as admin in Win8.1 to set it's boot manager.

So, on pushing the power button, I get GRUB.  That's good.  On rebooting Win8.1, I get GRUB.  Also good.  The bugaboo comes when trying to reboot Ubuntu.  I get the words &#8220;no bootable device &#8211; Please restart system.&#8221;  If I hit ctrl-alt-delete, it boots directly to Win8.1, no GRUB appears. Also at that point if I hit and hold the power button to forcibly shut it off and then back on, it boots directly to Win8.1, no GRUB.
 
 The problem's obviously not fatal, more annoying than anything.  I could just shut down Ubuntu every time and work around it, or reboot from Win8.1, but it seems like I shouldn't have to do that.

 I mentioned this is a Toshiba C70D, since I seems like many laptop manufacturers are fiddling with UEFI and hardcoding it to boot to Windows.  I feel like I've done all I can, and poked around with efibootmgr and bcdedit, but to no avail so far.
 
 Any ideas?  Thanks.

---

### Post by Mark_Hagan on 2015-04-08
Hi,

I've seen a few on here similar to this and indeed had a similar problem myself. 

The suggestion on this forum that worked for me was to use the Ubuntu boot repair. This worked perfectly for me. Link is here:- [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It doesn't seem to fix the issue of Windows blowing away GRUB but it at least gets you back your Ubuntu.

Mark

---

### Post by zon14 on 2015-04-08
I did try that earlier with no success at an earlier stage.  I can try it again and see if anything changed.  So far, Boot repair at least didn't throw me an error like last time. But then, I also went into advanced mode and fiddled with some settings.  So now here goes.  So after rebooting from both Ubuntu and Win8.1, all's well and GRUB shows both ways.

Or so I thought.  It worked for one reboot.  It solved one part, but not the other.  If I reboot from Ubuntu now, I still get the "no bootable device - please restart system" message, but now if I hit ctrl-alt-delete, at least it boots to GRUB rather than directly to Win8.1.  So there's still something weird going on, maybe with the firmware bootmgr that gets overwritten?

---

### Post by leunam12 on 2015-04-09
Try disabling fast boot at the BIOS.

---

### Post by oldfred on 2015-04-09
Others with Toshibas have renamed bootx64.efi with is the hard drive boot entry.

       Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

Detailed copy commands are in the link in my signature.


 From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. # Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
# only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip backup command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by zon14 on 2015-04-09
That was one of the first things I did.

---

### Post by oldfred on 2015-04-09
Post link to summary report from Boot-Repair.

---

### Post by zon14 on 2015-04-09
Actually the problem was much simpler than any of that.  I started poking around in Toshiba's setup, and found it set so that it would boot from usb first, DVD second, LAN third, and the hard drive last. I swapped the priority for hard drive third and LAN last, since I don't run a PXE server anyway.  THAT has solved it.  I've rebooted Ubuntu four times in a row just to test at the login screen and after logging in, and no "no bootable device -- please restart system" message.  So, finally solved!

---

### Post by oldfred on 2015-04-09
I would set hard drive first.

Does f12 get you to a boot menu, so then you can easily choose flash or DVD? Otherwise you would have to go into UEFI when you wanted to boot something other than hard drive.

---

