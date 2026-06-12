---
title: "Dual boot Windows not booting anymore"
date: 2022-01-25
forum: Installation &amp; Upgrades
---

### Post by tech291083 on 2022-01-25
Hi Friends,

I used to dual boot Windows 7 and Ubuntu quite regularly up until a couple of years ago. Just a few days ago, I bought my first ever SSD, Crucial 240GB. My motherboard is Gigabyte H61M-S.

I decided to test a totally new dual boot on this new SSD with Windows 7 Home Basic 64 bit and Ubuntu Desktop 21.10 64 bit.

The very first time, I installed Windows first and then created a free space of around 90GB to install Ubuntu using a DVD. Ubuntu identified Windows and allowed me to install itself to the free space with no issues whatsoever. Windows and Ubuntu both were shown on the grub menu as soon as the PC was powered on and I could boot any of these two with no problems whatsoever. 

But the very next day I again tried to install Ubuntu after already having installed Windows, the Ubuntu installer did not identified Windows and I had to give up without installing Ubuntu.

I then wrote the Ubuntu iso to a pen drive (32GB) tried to install Ubuntu after already having installed Windows, but again the Ubuntu installer did not identify Windows and I had to choose an option called "Something else", which did show free space and the Windows installation, but I had to make partitions manually and then I could install Ubuntu, thereby making my PC a dual boot system. But, now I was not able to boot into Windows. I checked the boot options in BIOS but all looked OK and an Ubuntu entry was there, which meant that it was installed properly, but I simply could not boot into Windows anymore and I was even more shocked when I found out via the Disks app the Windows partition was intact. 

I decided to boot Windows again by doing the troubleshooting myself and in so doing I used many different tools/methods as listed below. I was able to boot into Windows, that too, by using the Super Grub2 Disk only, but then I was never able to do so. 

Windows system recovery
Rescatux CD
Super Grub2 Disk
UBCD
SystemRescueCD
Boot Repair Disk
Hiren's BootCD PE
Install EasyBCD in Windows after booting in to Windows using Super Grub2 Disk

If I write about each of the methods/tools and how I used them, it would be too long a post, so I am posting some links to a free image hosting website, with photos taken om my mobile, please forgive me the quality is not that good. Please have a look at them and suggest me a solution so that I can boot into Windows again and make this dual setup work. Also, please note that sometimes the photos are not uploaded in the right order as there are technical issues sometimes. Thanks.

Please note that - I am no expert, but I am always ready to try and learn new things on my own until I am no longer able to do think anymore. So the photos/images may show many mistakes on my part. But please bear with me.

Thanks a lot.



Ubuntu installation

[https://postimg.cc/gallery/Mcp0bfg/f956af73](https://postimg.cc/gallery/Mcp0bfg/f956af73)

Windows system recovery

[https://postimg.cc/gallery/nLFSBRY](https://postimg.cc/gallery/nLFSBRY)

Rescatux CD

[https://postimg.cc/gallery/Ngn6wG5](https://postimg.cc/gallery/Ngn6wG5)

Super Grub2 Disk

[https://postimg.cc/gallery/dsyw56b](https://postimg.cc/gallery/dsyw56b)

UBCD

[https://postimg.cc/gallery/s3sL8mh](https://postimg.cc/gallery/s3sL8mh)

SystemRescueCD

[https://postimg.cc/gallery/44ncnrq](https://postimg.cc/gallery/44ncnrq)

Boot Repair Disk

[https://postimg.cc/gallery/k8RNDsy](https://postimg.cc/gallery/k8RNDsy)

Hiren's BootCD PE

[https://postimg.cc/gallery/vfFQd8B](https://postimg.cc/gallery/vfFQd8B)

Install EasyBCD in Windows after booting in to Windows using Super Grub2 Disk

[https://postimg.cc/gallery/mBf25Py](https://postimg.cc/gallery/mBf25Py)

---

### Post by tea for one on 2022-01-25
I have only scrolled through the images concerning Ubuntu Installation and this [https://postimg.cc/1nBZbr9X](https://postimg.cc/1nBZbr9X) is key.

Are you familiar with Legacy boot mode compared to UEFI boot mode?
Here is some info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Finally, Windows 7 is unsupported now [https://www.microsoft.com/en-gb/windows/windows-7-end-of-life-support-information](https://www.microsoft.com/en-gb/windows/windows-7-end-of-life-support-information)

Edit: You have backups of your personal data?

---

### Post by tech291083 on 2022-01-31
> 
I have only scrolled through the images concerning Ubuntu Installation and this [https://postimg.cc/1nBZbr9X](https://postimg.cc/1nBZbr9X) is key.


Thanks a lot.

> 
Are you familiar with Legacy boot mode compared to UEFI boot mode?


> 
Here is some info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


> 
Finally, Windows 7 is unsupported now [https://www.microsoft.com/en-gb/wind...rt-information](https://www.microsoft.com/en-gb/wind...rt-information)


> 
Edit: You have backups of your personal data?

Oh yes.
> 


Thanks you very much.

---

### Post by tech291083 on 2022-01-31
I am also doing some R & D on my own in order to find ways in which I can make a Win 7 and Ubuntu Desktop 21.10 64 bit dual boot a success. I have created a plan. I have started a new thread on this very subject. Thanks a lot.

---

