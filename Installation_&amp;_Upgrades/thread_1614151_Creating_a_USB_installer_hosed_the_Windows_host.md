---
title: "Creating a USB installer hosed the Windows host?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by bofh47 on 2010-11-05
My daughter tried to create a bootable USB-stick version of ubuntu by following the steps on this site, which included using the "universal USB installer" utility from pendrivelinux.com. She was on a windows notebook (I don't know which version, probably XP), and had saved the .iso to the desktop.

She's generally pretty good about following directions, but now, with no CD or USB stick in place, the windows machine HD boots directly into the installer "Try ubuntu or Install ubuntu" screen, with no trace of windows! Naturally, her SO (it's his work machine) is more than a* little* upset.

Hosed MBR? Or worse? Things are a bit... ummm... "prickly" over there because of this, and all help would be greatly appreciated!

---

### Post by efflandt on 2010-11-05
Does it do that even when the USB stick is not inserted?

So click "Try Ubuntu", and from there do sudo fdisk -l (small L) in a terminal and see what partitions are there.  It is possible that she installed it to the main hard drive instead of the USB device.  Just hope that she did not click Format first or it may have wiped a partition and reformatted it as FAT32.

Even better would be to run this script and post the results (wrapped in code tags by highlighting pasted RESULTS.txt and clicking **#** in message window) [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you are lucky, all you have to do is fix the mbr.  If unlucky, you may need to reinstall Windows and programs.

---

### Post by bofh47 on 2010-11-05
Thanks, efflandt.
 
The machine boots directly to the screen from the Live CD that offers the "Try/Install" choice. There are no USB keys or CD's in the machine. Selecting "Try" opens a linux session, and browsing the "95.5gb filesystem" reveals the usual directory list for an XP box. 

Running fdisk -l shows two partitions - sda1 is HPFS, sda2 is W95FAT32, and the sda2 partition is marked as the bootable one. It seems that the best explanation would be that the "USB-installer" put the ubuntu .iso file into a partition on the HD that the user was previously unaware of. The author of the installer has confirmed to me that the tool was capable of doing that, and that as a result of this, he has now altered the code to limit installation to "removable drives" only.

When I phone the user tomorrow (this is all remote) I'll ask him to try to bring up the Grub menu during the boot. If there's a windows entry, we'll try to run that and see if the system files have been hosed. I'm hoping not.

---

### Post by bofh47 on 2010-11-07
Close,  but no prize. I had hoped to run update-grub, thinking that it might see the unreachable windows partition and add it to the grub menu, and that I could then set the default to boot into windows to make the machine look&feel like it did before this fandango.
 
But apparently the live-disk installer doesn't use the cascade of grub files that I was expecting - there is no update-grub, no file to alter in /etc/defaults etc. 
 
One thought I had was to go ahead and formally install ubuntu (from a liveCD) into the partition that was mistakenly taken by the installer, since whatever was in there originally is gone already, and then try to just make it a normal dual-boot machine (i.e. overwrite the liveCD .iso image with the actual ubuntu installation). But the owner is way too nervous at this point to accept that option.

Any ideas how to get it to recognize the windows partition without those pieces? I still think that 'doze is probably all there and intact, just unreachable.

---

### Post by uRock on 2010-11-07
Do you have the Windows installer? If yes and it is XP, then the disk can fix the MBR.

---

### Post by bofh47 on 2010-11-08
Thanks. I'll ask the owner if he has the CD, but probably doesn't since the notebook was school-issued. He's going to take it in to the tech support guy later today, so now a moot point.  He was trying to avoid that because he felt it would show he hadn't treated the thing with appropriate care - I told him as long as it wasn't loaded with kiddie porn (it's not), the problem he had with it wasn't going to be considered a big deal. <g>

Good to know for future reference, however. Thanks again to all for replies.

---

### Post by oldfred on 2010-11-08
From Ubuntu and many linux rescue disks you can install the lilo MBR  (not the full lilo bootloader). Lilo works just like windows in that it looks for the boot flag (active partition in windows speak) and jumps to the partition boot sector to continue booting. If windows is in the boot sector it will then boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

