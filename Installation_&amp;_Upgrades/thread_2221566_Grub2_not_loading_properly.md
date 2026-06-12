---
title: "Grub2 not loading properly"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2014-05-02
I have recently installed a clean fresh Ubuntu 12.04 LTS.  The installation was normal with no problems.  Or so I thought.  My grub2 menu shows 2 Windows 7 loaders, one for sda1 and sdc1.  I tried working with the Grub Customizer and I can't get rid of the sdc1 in that sda1 will function properly.  They both have to be there in order for me to be able to go into Windows.  I have removed both Windows 7 loaders and only restored the sda1 and the grub2 menu only continues to recycle itself giving me an additional 10 seconds to decide.  When I restore the sdc1 windows loader then one of them will direct me to Windows 7.  So, how do I repair this so only sda or sda1 shows and functions without the second loader(sdc1)?

---

### Post by oldfred on 2014-05-02
Windows normally only has all boot files in one active partition.
That is the drive set in BIOS to boot from, and the NTFS formatted primary partition with the boot flag on that drive.
All other installs normally move all boot files into that one install. If you copied boot files to the other install you may need to run repairs to have BCD or boot.ini correct.

I prefer to manually update grub. You can turn off os-prober and copy which ever entry works correctly into 40_custom.

May be best to see details:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gilloz on 2014-05-02
Thanks Old Fred for your response.  Well, I played around with Grub Customizer, again, by removing and saving combinations of the Windows loader for both sda1 and sdc1, then restoring them in location 5 or 6 back and forth until I got the proper indication of only having one Windows 7 loader and it being the sda1, which is what I was looking for.  Now my grub menu is functioning like I wanted.  I knew if I played with it a bit, I would get the correct combination, and I did.  Thanks again for your response Old Fred.

---

