---
title: "Deleted Ubuntu partitions, Windows 8 won't boot, can't boot anything in UEFI"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by cjlindman on 2013-04-04
I'm guessing I won't be able to get much help with this since GPT and UEFI are so recent and presenting so many new problems and bugs, but I thought I'd make a thread anyways to get a conversation started and have something archived on the 'net regarding this issue.

I bought a ****** Dell laptop a while back, which came with Windows 8 and runs in UEFI (and SecureBoot, if that matters - I still don't know what the hell that is exactly). I set up a dual boot with Ubuntu 12.10 that took a while, but ended up working surprisingly well. However eventually I realized I was never using Ubuntu and booting into GRUB was unnecessary and annoying, so I ignorantly deleted the Ubuntu partitions without any thought to what that might do to my computer's booting capabilities.

Then my PC started giving me a number of different errors on startup depending on which boot options were selected - UEFI with SecureBoot, without SecureBoot, or Legacy boot. Booting in Legacy presents the text "Operation System not found", after which I CAN boot into a connected USB drive. UEFI without SB gives "error: no such partition. grub rescue>". As far as I can tell this prompt doesn't allow me to do anything, and I can't escape it to boot from USB. UEFI with SB gives "Image failed to verify with *ACCESS DENIED*. Press any key to continue." This repeats a few times before going to the boot options menu.

One final, important note about my available boot options: I can't attempt to boot anything but GRUB in UEFI mode! The options for a UEFI boot are Windows Boot Loader, Network, and ubuntu, and trying to boot to any of them gives the same grub rescue error.

 For a long time I didn't recall that I had an UEFI setup, so I started researching [an extremely similar error with the MBR]("http://ubuntuforums.org/showthread.php?t=1818449"): if one deletes Ubuntu partitions, their MBR still tried to boot to GRUB, which is no longer there, so it gives errors similar to mine. That error is fixed by using a Windows repair disc and repairing the MBR. However this fix does not work for me because, as I found out after many hours of frustration, my PC doesn't have an MBR in the first place; it's replaced by the ESP.

At this point I gave up on trying to save my files and decided to just do a clean install of Windows 8. I booted the USB image in Legacy mode (remember I am unable, as far as I can tell, to boot anything in UEFI without going straight to a grub rescue error) and deleted all partitions except my ESP.

Now the issue gets a bit convoluted.

From what I've read, my Windows 8 key/license is part of my ESP; I was never given an actual product key (I forsee a lot of crap-talking for using proprietary software - I'm sorry; I just love my video games!), and I have apparently no way of installing a licensed version of Windows after deleting my ESP, because that would delete my Windows key along with it.

So, as I said, I deleted everything but my ESP and tried to install Windows on a new partition, thinking that the Windows installation would do whatever it needed to do to repair the EFI and get rid of GRUB errors. Unfortunately, when I tried to select a partition for install, I received an error that read something like "Windows can't be installed on a GPT drive." After some research, I found out that this was due to my booting the installation in Legacy mode; to install Windows on a GPT, it must be booted in UEFI.

So basically, my problem is that I can't boot in UEFI to install Windows, but I can't delete the ESP either, because then I'll lose my Windows license. I imagine I could contact Dell and try to get some sort of key from them to do a new install, but I'm sure they'd give me a lot of ****, and there's no guarantee. If anyone has any thoughts, suggestions, or info on this issue, I'd greatly appreciate any input! I do need to do a bit more research on Windows 8 licensing in the meantime to make sure I have all my facts straight.

---

### Post by oldfred on 2013-04-05
Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

You probably should have run Boot-Repair and posted link to BootInfo report before deleting. Some systems have a one key recovery using the recovery partition to reinstall Windows. Several users had to do that after having too many issues with Ubuntu, but later learned the install process and got to dual boot.

Windows only boots on gpt partitioned drives with UEFI. And the pre-installed Windows 8 uses secure boot. Some systems will boot both Windows 8 & Ubuntu with secure boot on or off. Some only boot both with secure boot on.
Also some vendors have modified UEFI to only boot the Windows efi file. Boot-Repair renames Windows boot file to a be the grub shim file to boot grub and then grub boots Windows with a backed up name. You may have just needed to restore the original Windows efi file, somewhat like restoring Windows boot loader to MBR when deleting Ubuntu & grub boot loader is in MBR.

So what is deleted? Do you have the recovery partition? Or did you make a set of DVDs that is from the recovery partition. Or did you do a full backup of Windows which makes it easy to reinstall? 
If you have nothing, you will have to order a new install media set from Dell. If new computer they may not charge much or just a handling fee.

Others in Forum with Dell.

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by cjlindman on 2013-04-05
Great info, thanks! I don't know how you found it all.

I was mistakenly thinking my Windows key was attached to my ESP (hard drive) rather than my BIOS (mobo), so I was afraid I couldn't delete that EFI partition without losing my key. But since it's on the mobo, I just wiped the whole disk, which got rid of the GRUB errors, and then booted a vanilla Win8 install disc, grabbed the key from the BIOS, and installed Windows.

Your assertion that I needed to restore the original Windows EFI file seems exactly right. If I had done that initially, I think I could have kept my original Windows installation. However, in my case, I actually had deleted the recovery partition a long time ago, so I was pretty screwed. My only option would've been to order discs from Dell as you suggested. Even then, I'm not sure if I could repair the EFI partition without being able to boot those discs in UEFI mode, which I could find no way of doing. On a related note, my current, new Windows install had to be done in Legacy mode and thus with an MBR table, as I could not boot the disc in UEFI. Even now, without the GRUB errors, I can find no way to boot anything in UEFI. There's simply no boot option for anything related to discs or USB. Still just the old WBL and ubuntu boot options, which do nothing except take me straight back to the boot options menu that I just came from. Does this mean I'm stuck never being able to use GPT or UEFI again? This can't be true, since Windows must have accessed UEFI to grab the key. But how did it do so if I didn't boot the disc in UEFI? I'm sure all this confusion is only due to my general lack of familiarity with UEFI and GPT, so you don't need to answer these questions unless you wish to archive the info. I just need to educate myself more on the UEFI interface (redundant, I know).

Thanks again for the response! It's an awesome consolidation of info.

EDIT: I can't mark the thread as solved; the option doesn't show up in the thread tools drop-down. Could it be because I started the thread on a different PC?

---

### Post by oldfred on 2013-04-05
Windows only boots in UEFI mode from gpt partitioned drives. Or from UEFI you have to have gpt partitioned drives. And from BIOS you have to have MBR(msdos) partitioning.

Ubuntu will boot in either UEFI or BIOS mode from gpt drives. I only have BIOS but all my new drives are now gpt. But I never could install Windows on those gpt drives.

How you boot install media is how it installs, or if you boot install in UEFI mode it will install in UEFI mode. Not sure with Windows 8 if on your system it would want secure boot or not. Users could install older versions of Windows without secure boot, but new systems with Windows 8 have secure boot.

If you let Windows convert your drive to MBR, you have an issue installing Ubuntu. Windows converts primary gpt partition table to MBR, but ignores the backup gpt partition table. Linux sees MBR and backup gpt and gets confused on whether you really are MBR or gpt.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

But with UEFI, Windows has some very specific partition requirements.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

