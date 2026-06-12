---
title: "Installation failed and I have forgot my password"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by mildpigeon on 2012-04-13
Hey,

Many months ago I tried to install Ubuntu 11.10 (i believe) on a wiped Dell Latitude laptop, it failed on "checking battery state" so after a few failed attempted fixes I stopped trying. 

I now desperately need money and want to sell the laptop but need to wipe the setup data i entered. I know there is a fix to the "checking battery state" which requires access to the command line but i can't remember my login details, therefore i can't finish the setup and then wipe ubuntu!

I have tried for hours to get DBAN to work also with no luck.

So kind folk can someone please either:
1. tell me how to reset my password whilst i'm in this strange half way through setup scenario
or (and probably the best option)
2. help me DBAN the drive.

To DBAN I have used a USB flash drive. I am on a mac and have formatted the USB drive to FAT-32 and downloaded unetbootin to make DBAN bootable on the USB flash drive. I select ubuntu as distribution and ISO as downloaded from DBAN website. I ONLY have my PC set to boot from USB inputs, the rest are deselected.

The end result is it says "missing operating system"...Help!

thanks.

---

### Post by darkod on 2012-04-13
I don't understand. Do you want to wipe the disk?

If you have ubuntu cd that can boot in live mode, you can write zeroes to the whole hdd and that will delete any installation attempt.

Assuming your hdd is /dev/sda, you can do that from live mode in terminal with:
sudo dd if=/dev/zero of=/dev/sda

Of course, that will delete ALL data on the disk.

NOTE: Depending on the size of the hdd the process will take a while.

---

### Post by mildpigeon on 2012-04-13
Yes, ultimately now i want to wipe the disk - thanks! I will try your suggestion in the morning.

---

### Post by mildpigeon on 2012-04-14
Thank you very much buddy, that has worked :)

---

### Post by darkod on 2012-04-14
No problem. Please mark the thread as Solved, you can do that in Thread Tools above the first post.

---

