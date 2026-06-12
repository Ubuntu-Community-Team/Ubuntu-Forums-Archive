---
title: "installing ubuntu after broken win xp install"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by joecape on 2010-01-13
I've put together all the parts of a PC and thought I could use an old copy of W***ndows XP I had just to get things started and then later upgrade to w*ndows 7 and put Ubuntu on a second partition (I'm told I need to do things that way round: windows first, anything else will be more tolerant of not being the only OS when you try installing it as a second OS) . After going through the installation steps for XP, it asked me for the product key, which was fine - or it should have been - as I had that marked down. However, I failed to realize that the product key gives a license to install on just one PC and obviously that had been used up. 

So now, if I try booting from the CD drive, it goes straight from the manufacturer start-up to a prompt, saying I need to select the correct boot drive, or put something into the selected boot drive. It does this when I have an XP start-up disk in, and when I have the Ubuntu (version 9) disk in. If I allow the hard disk to be used for secondary load-up i.e. giving the CD drive priority, it skips whatever CD is in the drive and goes to a re-setting Windows XP installation screen, asking for the XP Home edition CD (although this didn't happen when I tried the same thing on a laptop, so the discs are fine ). 

Do I need to wipe the hard disk so that it forgets that I was installing XP (when I first started installing XP, I chose to partition 80GB of the hard disk and format it) ? Can I do this from the BIOS? I knew it was a bad idea to trust MS!!!

---

### Post by darkod on 2010-01-13
Regardless of the failed XP install, when you boot with ubuntu cd and the cd is before hdd in boot options, it should boot from the cd ignoring what ever is on the hdd.
Try it again. Make sure CD is before HDD in BIOS boot options. Then select Try Ubuntu to load the live desktop.
If you want to wipe the XP install the easiest thing is to open Gparted and just delete the created XP partition. That's it.

From there you can do as you want. You don't necessarily have to wait for win7. What I would do:
1. With Gparted either delete this ntfs partition and then create a new one with the size you want to allocate to win7. Or just reformat this partition as ntfs if you want to keep the same size.
2. If you want a second ntfs partition, create that too.
3. Reboot again with ubuntu cd, select Install Ubuntu and tell it to use Largest Available Free space. That should install ubuntu in the unallocated space left on the hdd after creating the one or two ntfs partition(s).

Later you can install win7 in the first partition which would already be ntfs and simply restoring grub2 to the MBR will make thing work just fine.

---

### Post by joecape on 2010-01-13
thnks, seems like the CD-reader was listed as "removable drive".

---

