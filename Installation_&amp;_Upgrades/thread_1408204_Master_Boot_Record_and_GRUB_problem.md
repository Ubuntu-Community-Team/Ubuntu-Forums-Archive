---
title: "Master Boot Record and GRUB problem"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by alexdnk on 2010-02-16
Oh no, I had to reinstall Xubuntu 2 days ago, cause I installed Windows 7 on my spare partition and it re-wrote my MBR ( I think, at lest GRUB was gone  ](*,))  So I couldnt boot into Ubuntu. I reinstalled it, but I will install Vista soon. So now I will be able to boot in XP, 7 and Vista, but not Ubuntu. How can I avoid this, so I can keep GRUB?
PS: I will install Starter or Home Basic.

---

### Post by dE_logics on 2010-02-16
Assuming you installed any other OS over Ubuntu or it's variants, there are many ways to reset the boot loader to Grub.

Boot the live CD (xubuntu or any variant). Mount your root partition and run - 

```
grub-install --root-directory=<the place where you mounted the root partition of your ubuntu install> /dev/<the HDD where all this mess has happened...e.g. hda, hdb or sda, sdb etc...>
```

This will install Grub as the bootloader, but the entries of the new OS that you installed will be missing (or no menu as such will be displayed). To fix this, boot your (now fixed) Ubuntu that's installed and run - 

> dpkg-reconfigure grub-pc

It will ask you a few questions...just leave the default.

---

### Post by darkod on 2010-02-16
There are more details about reinstalling bootloader here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just make sure if you had a clean install of 9.10, that's using the new grub2, when doing the restore to use 9.10 cd and use the instructions for 9.10. No need to reinstall linux just because of the bootloader!!!

Also, for grub2 after you reinstall it, to detect the new OS and create new grub menu is enough to run:

sudo update-grub

---

