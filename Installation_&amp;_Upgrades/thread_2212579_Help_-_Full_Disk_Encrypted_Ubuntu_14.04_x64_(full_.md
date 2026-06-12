---
title: "Help - Full Disk Encrypted Ubuntu 14.04 x64 (full install) on USB stick"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by fr33z0n3r on 2014-03-21
I'm looking to build a USB stick for single user design (obviously) running Ubuntu x64 14.04 with full disk encryption (LUKS) for use on UEFI and BIOS systems.  I'm a noob and I'm confused over the various things i've seen regarding partition layouts, etc.

**I've already built non-FDE Ubuntu x86 "full" installs on USB sticks for a year now, and they work as I need them.  I want to enhance this with a need for UEFI and FDE.**

I have just built/installed one that works, but I'm not pleased with the automatic partition design it used.  It is very wasteful on my 16gb USB thumb drive.  I will **try** to share a pic showing the partition layout on the drive that I don't like.  There is an enourmous /swap inside the LUKS.  But I can share more info if you like.

[ATTACH=CONFIG]251377[/ATTACH]

**Requirements**:
As few partitions as possible
Only if a separate /boot partition is required I want it to be 1GB (can't stand old kernels causing install problems anymore)
I want to skip the swap partition (the other usb sticks I've made have worked fine without it)


I think I will be forced to use the Ubuntu installer to layout my partitions using the "custom partitioner" during install.

Here is what I was going to create.  **I'd like to know if this is a valid design AND if the installer would handle it without problems.**  I'm not very capable at linux.

_GUID Partitioned USB drive_
1.  300MB EFI partition  (FAT32)
2.  (only if required)  1GB /boot    (ext2)
3.  ~15GB LUKS
4.  ~15GB LVM2 Physical Volume

Partitions inside LUKS/LVM:
~15GB /   (ext4)


Is this acceptable for my goals?

---

### Post by Iowan on 2014-03-22
Moved to Installation & Upgrades by request.

---

### Post by ubfan1 on 2014-03-22
For a gpt partitioned disk to boot on a MBR/BIOS system, you will need an additional small 1M partition with the grub-bios (or bios-grub?) flag to hold the core.img which can no longer fit right after the MBR.  OR, use msdos partitioning which may be more portable anyway, and doesn't need the additional partition.

---

### Post by fr33z0n3r on 2014-03-23
Thanks for the resply ubfan1.  I included the proposed /boot, as even the installer was kind enough to tell me it was required.  I was suprised by how well it helps the user nowadays.  And it appears to be working.

Now I just need to find out how I can verify that secure boot mode is in use/active?  I just have a standard install (other then the points I've mentioned), so I'm guessing it has simply gone through the secure boot process, but isn't validating the hardware or "chain".

Is there a command I can run to confirm that secure boot mode was used for the current session?

---

### Post by ubfan1 on 2014-03-23
You enable/disable secure boot in the UEFI settings, and it's not even supposed to be programmatically alterable.

---

### Post by fr33z0n3r on 2014-03-23
Sorry, by "UEFI settings", do you mean BIOS/UEFI?   Or something inside Ubuntu?  I've seen indications that other linux flavors have had some support for a check that secure boot was used.

---

### Post by ubfan1 on 2014-03-23
"UEFI Settings" is for the new machines like "BIOS Setup" was to the old ones.  Just a new term for the same old function.   There is a was to tell if UEFI mode is used, look in /sys/firmware/efi (I think).  If you have the efivars directory, you are running in UEFI mode (something like that).  The Ubuntu live media have both MBR and UEFI boot mechanisms (secure boot), so they work in both types of systems.  The secure boot (signed) executables will run with secure boot off, so that's no way to tell.  But the unsigned executables will not run with secure boot on.

---

### Post by fr33z0n3r on 2014-03-23
ok, thanks for verifying that for me.  Sucks there is no way to confirm secure boot mode is used....seems like a very important check to not have.

---

### Post by ubfan1 on 2014-03-24
Well two of the efivars are SecureBoot and SecureBootEnforce, which contain the info if secure boot is on.  you can use fwts uefidump to dump the variables to look at them in an editor, or just octal dump the variables.  The fwts dump gives you attribute/value and is much better for humans to read, with a "Secure boot mode is on" comment for value 1 (or off for 0).  The attributes are 6 for SecureBoot and hex 17 (dec 23) for SecureBootEnforce if you are looking at the od program dumps.

---

### Post by fr33z0n3r on 2014-03-24
nice!  Thanks for that!

---

### Post by fr33z0n3r on 2014-04-19
I've finally been able to get Ubuntu loaded on this system (Dual boot with Windows 8.1).   The USB stick will not be seen by the UEFI BIOS, unless I add it to the boot order pointing at the EFI file (not the "quick" boot menu).  (more info @ [http://ubuntuforums.org/showthread.php?t=2144458&p=12992838#post12992838](http://ubuntuforums.org/showthread.php?t=2144458&p=12992838#post12992838))

Also when the device (Dell XPs 18) is powered on, it now gives a red error saying "Secure Boot Violation - Invalid Signature detected.  Check Secure Boot Policy in Setup".  This screen sticks until Enter is pressed.  It then goes to the Ubuntu boot menu with Windows Boot Manager as an option.

I was able to just run this inside the laoded Ubuntu:
sudo fwts uefidump - 

I have just checked these variables and SecureBoot seems to be set to 1.

So what does the RED warning  I'm seeing tell me?  I think I'm in secure boot mode in both Ubuntu and Windows,  but is this a correct assumption?  And if so, does this error indicate that the shim signature is NOT accepted by my UEFI?  (which I thought would PREVENT it from being bootable)

@ubfan1 - If you (or anyone) has any info/experience it would be appreciated.  Most posts I've found about this error tell users to disable Secure Boot - and I'm not going to do that.

---

### Post by ubfan1 on 2014-04-19
Check your current boot entries with sudo efibootmgr -v  , something has probably replaced the shim entry with grubx64, which of course is not signed by Microsoft, and will fail, but then their appears to be a vendor specific fallback, probably to /EFI/Boot/bootx64.efi, which probably is a copy of shim.efi, and has a copy of the signed grub present in the same directory, so it actually boots, and finds the grub.cfg file in /EFI/ubuntu.  Happened to me too -- way too many changes get made to the nvram boot selection, which really should never change after you set up your grub bootloader and the order.  I just left things alone since the boot worked, and eventually turned off secure boot, so I could boot Windows through grub.

---

### Post by fr33z0n3r on 2014-04-22
@ubfan1 - Thanks!  That showed the boot entries.  I then realized that I could set the boot order in the BIOS! (UEFI) .  Sure enough, there were 3 entries now (1 for Windows, 2 for Ubuntu)  I was so relieved when merely changing the order from using the grubx64 entry to the shimx64 entry fixed the boot error.  Unfortunately, both of the boot entries for ubuntu have the same label, so are impossible to distinguish.   I made an additional entry with a clear label to solve that issue.  Now the owner boots to Windows automatically, and can press F12 at boot to get into Ubuntu.  Sufficient for us.


So the original intent of this post was for USB usage  AND encryption, but I am equally pleased with a basic HDD install of Ubuntu.  It will be more reliable.  The encryption was much more necessary for a USB stick.  Dell has certainly annoyed me with preventing a USB stick from being usable at boot time in UEFI mode.

---

