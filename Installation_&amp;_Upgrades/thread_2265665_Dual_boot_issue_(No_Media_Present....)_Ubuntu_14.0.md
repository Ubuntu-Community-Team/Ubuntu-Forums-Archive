---
title: "Dual boot issue (No Media Present....) Ubuntu 14.04 and Windows 8.1"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2015-02-16
Before attempting to install Ubuntu 14.04 on my Windows 8.1 system I read several articles, which pretty much list the same procedure:

- backup Windows system
- turn off fast boot
- disable secure boot
- shrink main partition to make room for Ubuntu
- boot Ubuntu LiveUSB and install using "something else"
- install and run boot-repair (because my machine booted straight into Windows upon restart when Ubuntu finished installing)
- run bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi from Windows command line (because my machine still booted to Windows after boot-repair successfully executed)

After all of the above, I have a successful dual boot system, but each time I turn power on or restart I get the following:

>>Checking Media Presence.....
>>No Media Present....

After some timeout period, the Grub menu eventually appears, allowing me to boot to Ubuntu, Windows 8.1, or the Windows Recovery Partition.  It is very annoying to have this come up each time and have to wait the timeout period before I can boot.

Any idea why the error messages and what to do to fix?

---

### Post by oldfred on 2015-02-16
What brand & model computer?
Did you install Ubuntu in UEFI boot mode?
As in BIOS mode it has to reboot so new data in UEFI mode can be written to drive.
I think even if UEFI mode, the Windows BCD uses the UEFI one time reboot setting anyway. Or you reboot when using that.

If install is in UEFI mode, you can also create or rename /EFI/Boot/bootx64.efi to really be grub or shim and boot the hard drive entry in UEFI. 
Many vendors are modifying UEFI to only boot Windows by description. That is not per UEFI standard.

       From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

Other options:

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by ken18 on 2015-02-17
Thanks for your reply.  It will take me some time to digest it.  My PC is a Toshiba Satellite P55-A5312 about 2 years old.  I did the Ubuntu install in UEFI mode.  Like I said, I have a successful dual boot system.  I just want a fix for the annoying error messages and timeout.

---

### Post by oldfred on 2015-02-17
Some probably similar Toshiba. Several did the same rename of bootx64.efi.

 Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

### Post by ken18 on 2015-02-19
Very strange indeed.  I tried running boot-repair to see what it would do.  Didn't like the result, so I restored a previous system image using Windows image restore utility.  For the next several boots, I had none of the previously mentioned errors at all, but the Grub menu was noticeably lower resolution (larger characters and not as visually crisp).  But, after a few boots into Windows and Ubuntu, the errors came back and the Grub menu was much smaller and higher resolution.

The behavior is repeatable.  This morning I restored the same image and the first boot was w/o error and the Grub menu was large and low resolution.  My guess is the same will happen; that after a few boots it will go back to the original errors and small, high resolution Grub menu.

Any speculation as to what is going on?

---

### Post by oldfred on 2015-02-19
Grub tries to use the video X by Y sizes of you monitor.
Depending on video driver that then may update and you do get smaller fonts since instead of some default size it changes to high resolution which then seems smaller.
At grub menu go to grub teminal (not Linux terminal) and see what video modes your system supports in grub with vbeinfo.

You can force a smaller resolution or change font sizes.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)


 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

       
 gksudo gedit /etc/default/grub

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by ken18 on 2015-02-19
I'm not too concerned about the actual resolution of the boot menu.  I only mentioned it because the higher resolution boot menu is coincident with the "No Media Present..." error message whereas the lower resolution boot menu is coincident with the absence of the boot error messages.  I was hoping to get a plausible explanation as to why I'm seeing the two different behaviors.  It would seem to a relative novice (i.e. me) that perhaps the UEFI implementation on my computer is less than stable.

---

### Post by oldfred on 2015-02-19
Probable then a video driver issue.

What video card/chip do you have?

---

### Post by ken18 on 2015-02-19
My video adapter is Intel HD Graphics.  How could that be related to the "No Media Present...." errors?  Just seems odd that the media errors (or lack thereof) are coincident with the Grub menu resolution.

---

### Post by oldfred on 2015-02-20
Does not seem like it should be related.

Sometimes Intel video needs a video setting also. You can test while booting to find one that works then make it permanent in grub. You add settings just like the nomodeset. But nomodeset does not for Intel. Use one of the other settings in second thread.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
      
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Is no media present a UEFI error, not grub?
That can be just another one of the UEFI that vendors modify to not be UEFI standard and only boot Windows. Then the BCD entry for one time boot, edit bootx64.efi or other work arounds are required.
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by ken18 on 2015-02-22
> I[COLOR=#000000]s no media present a UEFI error, not grub?[/COLOR]

Hmm, don't know and not sure how I can tell.  Actually, I can't attempt further debug because I no longer get the media errors (which is good news but also scary because I have no idea what corrected the problem).  And, since it is working (even though grub menu is poor resolution), I'd rather not try any more tweaking.  I've spent probably 40 hours over the past month trying to get a successful dual-boot system and am a bit burned out on putting any more effort into this.

In my web searches, I did find the following:

[http://ubuntuforums.org/showthread.php?t=2195819](http://ubuntuforums.org/showthread.php?t=2195819)

which sounds exactly like what I was seeing.  I think I believe the conclusion that the culprit is probably buggy BIOS firmware.  So, I guess I'm done for now.  Thanks for your help.

---

