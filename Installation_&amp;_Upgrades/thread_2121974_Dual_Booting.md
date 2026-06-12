---
title: "Dual Booting"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by techguy1001 on 2013-03-03
Hi,

I'm kind of new to this sort of thing, first off.

Anyways, here's the dealio. I've recently (about 2 months ago) home-built my own computer from scratch, and am so far loving it. In case it matters, it's got an i5 processor, GTX 660 graphics card, and 8GB of RAM.

Now, at the moment, I have Windows 7 installed on it. I do not want to install Ubuntu using the windows install version - i want them to be two totally separate operating systems. 

Also, here's the tricky part... At the moment, I have windows 7 installed on my SSD, and the programs and files on the HDD (my SSD is only 64GB). Therefore, I doubt I'd be able to fit both OS's on the SSD. How would I be able to install ubuntu on the side of Windows, with my hard drive configuration.

Thanks in advance.

---

### Post by darkod on 2013-03-03
The best option is always the manual install because you have total control where you create the partitions and where the bootloader goes. If you feel comfortable with it.

Another option is leaving unallocated space with the size you want for ubuntu on the hdd, and using the Install along side windows auto option. That way it should use the largest available unallocated space which in this case would be the space you left it. If there is no unallocated space on the hdd you will have to shrink one of the existing ntfs partition(s) to make some. You can shrink with windows Disk Management.

In the auto method the bootloader grub2 might end up on the ssd since I assume that's the first disk you boot from. The manual install offers you to select where you want grub2 manually.

Another important thing. Did you install win7 in uefi mode? Are you using uefi boot? Or the standard legacy boot? Ubuntu will need to be installed in the same mode as windows, so it will depend how you boot the ubuntu cd/usb.

---

### Post by techguy1001 on 2013-03-03
Far as I know, it's a standard install. So basically, the manual install is just doing it where I boot it up as if it were a brand new computer? So totally separate partitions and everything? Would that basically split my hard drive?

---

### Post by oldfred on 2013-03-03
Both Windows and Ubuntu will install in the same mode as you boot installer. New computers may just default to UEFI install with Windows.

If SSD is gpt then you are UEFI mode with Windows and if first partition is efi then definitely UEFI. Post this from terminal:

sudo parted -l

---

