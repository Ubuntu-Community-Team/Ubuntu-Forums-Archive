---
title: "Installed Ubuntu, first time, now can't access BSD. HELP!"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by demonfire11 on 2011-08-10
Back in February I built my FreeBSD 8.2 (64 bit) box and was running  without issues. Last month I installed Windows 7 (64 bit), not by  choice but I needed an app that is windows only, on a second drive... I  unplugged my BSD drive and plugged in the new drive for the install,  when done I swapped the cable back and when happily back to BSD.

Last weekend I decided to try out Ubuntu 11.04 (64 bit), and followed  the same procedure, new drive, all other drives unplugged...install,  play, swap back...

This is where I hit a wall. Seems that Ubuntu's Grub2 flashed info to my  BIOS defining my boot sequence, and not allowing me to boot anything  unless the Ubuntu drive is connected. OK, no big deal, I would like to  be able to boot into all three without having to open the case, so I  connect all three and start fiddling with Grub2's config. Grub sees the  Windows drive without issue automatically, but not the BSD. I play with  it till I get Grub2 to locate and acknowledge the BSD drive, but BSD will  not boot. I just get a blinking cursor!!!

I am using the custom grub menu, the code that loads the drive and gets to the blinking cursor is:
     Code:
     menuentry "FreeBSD 8.2" {
    set root=(hd1,1)
    chainloader+1
} 
How can I get BSD to boot?

---

### Post by raja.genupula on 2011-08-10
your using separate harddisk right . so if you wanna boot from your bsd then that also need to have same grub . for that process follow this thread 

[http://ubuntuforums.org/showthread.php?t=1822033](http://ubuntuforums.org/showthread.php?t=1822033)

---

### Post by demonfire11 on 2011-08-10
Raja, Thank you.

Will installing Grub2 on the FreeBSD drive harm or break my BSD install? I really don't want my Unix install touched as it works great

---

### Post by demonfire11 on 2011-08-10
OK, that didn't work. The BSD drive is read-only when accessed via Ubuntu, and can not be changed.

If I was able to boot BSD, I could install Grub on that file system via the BSD port tree, but thanks to Ubuntu flashing information to the BIOS, I can't do that either. 

More suggestions?

---

### Post by Justinba1010 on 2011-08-10
I seem to have done that by using F10 or F2 to determine where to boot.

---

### Post by raja.genupula on 2011-08-11
> **demonfire11 said:**
> OK, that didn't work. The BSD drive is read-only when accessed via Ubuntu, and can not be changed.

If I was able to boot BSD, I could install Grub on that file system via the BSD port tree, but thanks to Ubuntu flashing information to the BIOS, I can't do that either. 

More suggestions?

i think you can do it by changing booting order , go to BIOS settings man , and pick up there the right option to boot from BSD

---

### Post by demonfire11 on 2011-08-11
yeah, tried that Sunday... epic fail!

It seems that Grub2 wrote information to the BIOS making it impossible to boot anything other than through Grub2.

I know, I know, that can't happen. Well it did. If I remove all HDD and CD/DVD drives from the machine, boot and go into BIOS, the only thing in the boot order is 'ubuntu'... which should not be there as there are no drives. Then if I connect a drive, including the CD/DVD drive, by itself and try booting directly from it, the system will halt with a message that it can not locate the HDD that Ubuntu is installed on. If I connect the Ubuntu drive (in location 1, 2, or 3), it always defaults to boot Grub2, which can't pass to FreeBSD.

---

### Post by demonfire11 on 2011-08-11
More information / issues.

I figured maybe I would update my BIOS to get rid of this issue, but thus far have been unsuccessful.

My box is running an 1155 (SandyBridge) chipset, which apparently is the first consumer based chipset to come with EFI ability, which is to say UEFI ability. As Grub2 is a UEFI boot loader, it is able to alter/enable UEFI in the BIOS on my board. Since it has altered/enabled UEFI, I am now not able to update my BIOS as the BIOS updates from the Asus site are not EFI BIOSes. So, I am stuck!

EFI/UEFI is capable of booting FreeBSD, but my BSD drive does not have EFI files on it in the boot area (or elsewhere as far as I know) which may be why I am having issues.

---

### Post by demonfire11 on 2011-08-12
I finally got the BIOS updated (to the most recent one out of Beta),  which did remove the UEFI 'ubuntu' listing out of the BIOS boot menu,  but the system still requires the Ubuntu drive to be installed, and  still defaults to Grub2, so still no BSD yet.

---

