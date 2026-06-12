---
title: "Dual Booting Windows (Not Encrypted) With Encrypted Ubuntu"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by firstlinux7 on 2012-11-07
Hello. I have been dual booting Ubuntu and Windows 7 for a while now. In the past, I have used the "encrypt home folder" option to add (some) security to my installation (ie. now no one can easily steal my home folder's contents by booting a live CD or using Windows to access my Ubuntu root partition). This is why I was excited to learn about the new Full disk encryption option in 12.10. I was able to successfully burn and boot the DVD. However, disk encryption and home folder encryption are not available options under "install along side them [the other operating system(s)]". Since I do not want to lose the Windows installation, I obviously do not want to select "erase disk".

Basically, here is what I would like to happen:
Power on > BIOS > GRUB > user choice (Windows or Ubuntu)
[INDENT]User Choice (Windows) > Non-encrypted, normal Windows (no encryption pass-phrase required)
[/INDENT]
[INDENT]User Choice (Ubuntu) > Encrypted Ubuntu 12.10 installation (with pass-phrase required)[/INDENT]

Now, I am able to access the "Something else" custom option, but I want to make sure I am doing everything right here.

My current partition setup looks like this:
/dev/sda1 is a small NTFS claimed by Windows (boot related??)
/dev/sda2 is the very large, main Windows partition
--16GB free--
/dev/sda3 is manufacturer recovery

So, I think I need to create:
1. a /boot partition (small, less than 100MB)
2. a "physical device for encryption" (within which / will be)
3. a swap partition

I have some questions, namely: 
A)Will this work as intended? and
B)What sizes should I use for these partitions (I have 4GB RAM, but running out of memory has not been much of an issue in past installations.)?

---

### Post by firstlinux7 on 2012-11-08
It seems that there are others having trouble with manual partition setup. Notice the error screenshots at the bottom of the page:
[http://www.linuxbsdos.com/2012/11/03/ubuntu-12-10-installation-and-disk-partitioning-guide/](http://www.linuxbsdos.com/2012/11/03/ubuntu-12-10-installation-and-disk-partitioning-guide/)

---

