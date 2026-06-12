---
title: "Xmas gift gone wrong - help?"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Chaos_Spear on 2010-12-24
Ok, so I've been using Linux for awhile now... and recently decided, hey, why not make a startup usb for my father for Xmas?  That way, when XP goes bad on his laptop, he can just stick in the usb drive and use it as a recovery system!

Well this all went well at first.  I installed Kubuntu 10.10 on a flash drive with no problems... but then I tried to boot back into XP without the flash drive in, and got a Grub error.

So I guess my mistake is, by doing a full installation rather than the startup disk option, I put Grub into the MBR of the regular hard drive.

After doing some reading, it seems the best way to fix this is to use an XP Startup disk.  I have one, but when I try to boot off this, it only sees the flash drive, and doesn't read the internal hard drive at all!

My only idea regarding this last part is that the XP disk I have... is slightly sketchy.(let's just say it fell off the back of a truck... and into my bittorrent client)  It's also not an OEM disk, so maybe that is part of it as well?

Am very confused.  Any help appreciated.

---

### Post by wilee-nilee on 2010-12-24
If it is just the mbr thats broken, you can install lilo from the thumb to boot XP, form the computer. so lets do this just to be sure where we are at and what is where. Don't install lilo without instructions you have to load it to the MBR as well.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between. You can run this in the Kubuntu thumb.

---

### Post by Chaos_Spear on 2010-12-24
The MBR isn't "broken" as much as "has GRUB installed."  Upon boot of the regular hard drive, GRUB runs, and needs the thumbdrive to be its root, so if thumbdrive isn't in...

If thumbdrive IS in, then by going through grub I can boot into XP, and once this process has started, I can remove the thumbdrive without any problems.

Of course, this means my gift is done wrong from the start: my gift recovery thumbdrive isn't bootable on its own.

---

### Post by wilee-nilee on 2010-12-24
> **Chaos_Spear said:**
> The MBR isn't "broken" as much as "has GRUB installed."  Upon boot of the regular hard drive, GRUB runs, and needs the thumbdrive to be its root, so if thumbdrive isn't in...

If thumbdrive IS in, then by going through grub I can boot into XP, and once this process has started, I can remove the thumbdrive without any problems.

Of course, this means my gift is done wrong from the start: my gift recovery thumbdrive isn't bootable on its own.

From the Kubuntu thumb booted it probably has lilo access. Generally this is done from a live cd/thumb booted rather then a full install but the command should work, use a live cd to be safe really.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

No I wanted the boot script to confirm that the sda in the command matched your set up. sda is the HD and the mbr.

Run in the terminal to confirm the HD.
```
sudo fdisk -lu
``` 

If this is confusing post the script, if not have a merry xmas.

---

### Post by Chaos_Spear on 2010-12-24
Ok, will try.

Sorry, just had no easy way to get the script onto that laptop - I am currently accessing the internet through another computer hooked up to a blackberry.

And yes, the thumbdrive I used would have been an excellent idea - if this weren't a Windows computer that can't read ext4. :p

EDIT: Just realized, if I can't get that computer onto the internet, then I can't very well apt-get... I guess this will have to wait.

---

### Post by t4thfavor on 2010-12-24
Should be able to boot into linux and edit the conf file so that it boots the Windows install, then you can reinstall the linux with grub on the flash disk instead of the real hdd.

If you want, you can use the WinXP recovery cd, to issue the fixboot, and fixmbr commands, then reinstall the flash disk ensureing that you install grub in the correct location this time.

---

### Post by Chaos_Spear on 2010-12-24
> **t4thfavor said:**
> Should be able to boot into linux and edit the conf file so that it boots the Windows install, then you can reinstall the linux with grub on the flash disk instead of the real hdd.
Not the issue.  Issue is that Grub is set up to use the thumbdrive as its root, so if thumbdrive is not attached, Grub returns an error.

> If you want, you can use the WinXP recovery cd, to issue the fixboot, and fixmbr commands, then reinstall the flash disk ensureing that you install grub in the correct location this time.
XP recovery cd I have won't detect the hard drives(read full body of first post for witty explanation) so I probably will have to track down OEM XP cd.  Hopefully that will work, if not, Lilo as suggested earlier in this thread.

---

### Post by efflandt on 2010-12-25
If you can still boot the USB, boot into that.  Check the output of **sudo fdisk -l** (small L) to make sure you know which is the USB drive.  Then do:

```
**sudo grub-install /dev/sdb** (or whichever USB actually is)
```However, there is more to it than that if you can no longer boot the USB (see** ****Reinstalling from LiveCD** way down on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) )

Then go about fixing the mbr on /dev/sda, if you have not already done that.

If you set your BIOS to boot from USB before internal drive, you might still have to press a key during BIOS splash screen (usually Esc or F12 for me) to select a boot device other than internal drive.

---

### Post by Chaos_Spear on 2010-12-31
Thank you everyone, MBR fixed and computer returned to normal working order!  Happy New Year!

---

