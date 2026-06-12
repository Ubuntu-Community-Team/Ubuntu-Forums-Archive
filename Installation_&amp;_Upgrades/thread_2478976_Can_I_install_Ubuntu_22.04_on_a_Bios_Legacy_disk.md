---
title: "Can I install Ubuntu 22.04 on a Bios Legacy disk?"
date: 2022-09-10
forum: Installation &amp; Upgrades
---

### Post by jkaltes on 2022-09-10
I have an old sata Samsung EVO 840 ssd with a Windows 10 and an Ubuntu 22.04 boot partition (/dev/sda3). Because Ubuntu gives problems, I wanted to reinstall Ubuntu on the same partition as before.

 To get this old SSD recognized in the bios I have to USE LEGACY and UEFI. I have also added two newer NVME M.2 ssds which I don&#8217;t want to use for booting.
 The install medium is also on a newer USB memory stick able to use UEFI.

 During the install I specified that the old Ubuntu partition (/dev/sda3) had to be the root device and that grub should be put on /*dev/sda**. * 

 This leads the to the complaint that there is "*no EFI system partition"*. If I go on without creating a EFI partition, the installer crashes and mentioned that update-grub failed.

 If I press Ctrl-Alt-t, mount /dev, /proc and /sys on /target (mount point of /dev/sda3) and  

 chroot to /target and run grub-update, it gives the following output: *Memtest86+ needs a 16-bit boot, that is not available on EFI*

 And doesn't use OS Prober.

 If I add GRUB_DISABLE_OS_PROBER=false to /etc/default/grub, update-grub blocks.

 If I remove in the bios all UEFI modes for the USB disk from the list of boot devices and boot the USB disk and run in the above mentioned way again grub-update, it still does not use OS Prober, but doesn't mention "*Memtest86+ needs a 16-bit boot, that is not available on EFI"*

 Booting the disk thereafter brings me in some command line Ubuntu error repair screen.

---

### Post by tea for one on 2022-09-10
Is Windows installed in UEFI mode?

Edit:-
Windows 10 must be in Legacy mode if there was no sign of an EFI partition?

Did you boot the Ubuntu USB in Legacy mode?

---

### Post by jkaltes on 2022-09-10
Windows 10 is on the disk in legacy mode. The Ubuntu USB was in UEFI mode. Later I hoped to boot it in legacy mode by removing the UEFI usb disk boot options in the BIOS settings.

---

### Post by oldfred on 2022-09-10
I have seen where Ubuntu now in BIOS mode suggests an ESP - efi system partition for all installs. Someone posted just continuing worked.

Basically all systems since 2012 are UEFI as that was when Microsoft required UEFI/gpt.
And you could use gpt with BIOS boot with Ubuntu since about 2010. 
With my old BIOS systems back then I added both the bios_grub & ESP on gpt partitioned drives. Then easy to convert to UEFI as partition existed.

Also if system is so old as to require BIOS boot, it probably would work better with a light weight flavor. Full Ubuntu assumes a newer system that now would be UEFI boot. And very new systems are UEFI only, no BIOS boot option at all.

If you have not updated firmware for UEFI and also updated firmware for SSD, that may be why you have issues. 
To check firmware for UEFI run this and compare on vendor's site what is latest.
sudo lshw | grep -m 1 -A 5 "*-firmware"

And for SSDa & compare to vendor's site.
udisksctl status

---

### Post by jkaltes on 2022-09-10
> **oldfred said:**
> 
To check firmware for UEFI run this and compare on vendor's site what is latest.
sudo lshw | grep -m 1 -A 5 "*-firmware"

And for SSDa & compare to vendor's site.
udisksctl status
lshw | grep -m 1 -A 5 "*-firmware"

     *-firmware
          description: BIOS
          vendor: American Megatrends International, LLC.
          physical id: 0
          version: 1.30
          date: 05/18/2022

I have a newer SSD update than the update available at [https://www.samsung.com/nl/support/model/MZ-7TE1T0BW/#downloads](https://www.samsung.com/nl/support/model/MZ-7TE1T0BW/#downloads)

 disksctl status

MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
Samsung SSD 840 EVO 1TB   EXT0DB6Q  S1D9NSAF748568T      sda

---

### Post by tea for one on 2022-09-10
Is there anything to prevent the re-installation of Windows 10 in UEFI mode?

---

### Post by jkaltes on 2022-09-10
> **tea for one said:**
> Is there anything to prevent the re-installation of Windows 10 in UEFI mode?

                        The problem isn't Windows. I can't boot Ubuntu from that old SSD after the re-installation of Ubuntu.

---

### Post by tea for one on 2022-09-10
I understand that you cannot boot Ubuntu.
However, there are few forum members who successfully dual boot Windows 10 and Ubuntu 22.04 in[COLOR="#0000FF"] Legacy[/COLOR] mode, therefore it is difficult to reproduce your situation and offer advice.
UEFI and GPT offer distinct advantages over Legacy/MBR especially partition management.

Why not run the boot-repair report and see if anyone can offer advice?
Second option from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jkaltes on 2022-09-10
> **tea for one said:**
> I understand that you cannot boot Ubuntu.
However, there are few forum members who successfully dual boot Windows 10 and Ubuntu 22.04 in[COLOR=#0000FF] Legacy[/COLOR] mode, therefore it is difficult to reproduce your situation and offer advice.


                        Before I re-installed Ubuntu I could boot Ubuntu 22.04 from the legacy SSD, but the re-installation failed and required a EFI partition I didn't need beforehand.

---

### Post by jkaltes on 2022-09-10
I think that it is of importance that I didn't reformat the Ubuntu partition; I re-installed Ubuntu in the old filesystem, keeping the files not belonging to the system.

---

### Post by mIk3_08 on 2022-09-11
> **jkaltes said:**
> Before I re-installed Ubuntu I could boot Ubuntu 22.04 from the legacy SSD, but the re-installation failed and required a EFI partition I didn't need beforehand. Are you booting the usb media in a BIOS MBR mode not in UEFI mode?  Regards and cheers

---

### Post by yancek on 2022-09-11
> required a EFI partition 

I don't believe it is 'required' as pointed out above.  I;ve seen threads here where users skipped that opton and proceeded with a successful install.  If you have a Legacy/CSM option in your BIOS firmware, make sure that is enabled and when you boot, you should see an option to boot either EFI or Legacy/CSM in the boot options.  If you boot in EFI mode, you will always see that message.  Since you have windows installed in Legacy mode, you must have that option in the BIOS firmware.

If you select to install to the same partition on which you had a previous Ubuntu install without formatting, it should simply install new system software.

Best next step is to run boot repair as suggested above using the 2nd option described on that site using the ppa and Create BootInfo Summary option and posting the link you get here so members can review it and make suggestions.

You can have a Legacy install of windows and an EFI install of Ubuntu on the same drive but that would require you to change boot options in the BIOS firmware each time you want to switch the OS.  Grub EFI won't boot a Legacy windows and windows BCD EFI won't boot Linux.

---

### Post by oldfred on 2022-09-11
Grub only boots working Windows.
That means Windows does not need chkdsk and fast start up/hibernation must be off.
But Windows turns fast startup back on with updates.
With UEFI, you just boot the UEFI Windows entry to fix Windows.

But with BIOS you only have one MBR. 
So you have to temporarily reinstall Windows boot loader, fix Windows, & then restore grub.
Be sure to have both Windows repair flash drive & Ubuntu live installer to to the MBR boot loader changes when grub stops booting Windows.

BIOS mode with newer Windows only really works with multiple drives, each install & its boot loader on that drive. Then when you need the Windows fix to turn fast startup off, you can in UEFI/BIOS switch boot drive to fix Windows. Grub will normally offer to boot Windows.

With new systems both Windows & Ubuntu may update UEFI. And with many systems, that reverts settings you changed to install Ubuntu back to defaults. Updates may occur as part  of other normal updates, so you may also need to check UEFI settings.
I have motherboards that are not in UEFI update from Linux with fwupate, so always know when I do an update. 
Do not know if Windows has setting to let you only do UEFI updates manually.

---

