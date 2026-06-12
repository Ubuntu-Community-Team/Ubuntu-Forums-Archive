---
title: "Trying to dual boot mint and ubuntu. But no grub appears"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by oopsie on 2010-10-17
I just thought I'd give linux mint a whirl. I installed it to a separate hard-drive than the one Ubuntu is on, and it seemed to install fine.

But when I reboot my computer, no OS selection screen appears.

I look at what's on my hard drive, and there definitely appears to be mint installed to my harddrive. Lots of files there. I just don't know how to make it boot!

Could anybody possibly give me some suggestions or help?

---

### Post by sikander3786 on 2010-10-17
Your computer automatically boots into Ubuntu? Please run

```
sudo update-grub
```

from terminal and post the output. Might be you installed the Mint loader in the MBR of 2nd HDD and in Bios you are configured to boot from the 1st HDD.

---

### Post by oopsie on 2010-10-17
> **sikander3786 said:**
> Your computer automatically boots into Ubuntu? Please run

```
sudo update-grub
```

from terminal and post the output. Might be you installed the Mint loader in the MBR of 2nd HDD and in Bios you are configured to boot from the 1st HDD.

Thanks for replying! That command gives this output

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 9 Isadora (9) on /dev/sdb1
done

---

### Post by sikander3786 on 2010-10-17
It sees your Linux Mint now. Reboot and see if you see the Grub menu.

If you change your boot device to 2nd HDD, you will see the Mint's Grub menu and it should list Ubuntu there.

Now both your drives have Grub installed and both are configured for dual boot.

Cheers.

---

### Post by oopsie on 2010-10-17
Yay! It works! and to prove it, I'm posting from mint now =D

Thank you very much! <3

---

