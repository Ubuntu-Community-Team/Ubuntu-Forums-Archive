---
title: "[SOLVED] GRUB Loading stage1.5. GRUB loading, please wait...Error 17"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by njhepler on 2007-12-07
Hello
I was going through the process of installing Ubuntu on a partitioned hard drive and received an error indicating there was something wrong with the install CD as a result the install was aborted. Since then I have been unable to boot any OS.  I receive a GRUB  error 17. I have burned another copy of the Ubuntu CD but I still get the error. I have checked the BIOS to ensure the first boot attempt is coming from the CD, I have also downloaded and tried running the Super GRUB disk but I still get the GRUB error 17. Any help would be greatly appreciated.

---

### Post by viking777 on 2007-12-07
If your installation aborted half way through, it is not at all surprising that you cant boot it. If you downloaded the Ubuntu iso did you check the md5 sum? It sounds to me as if your download is corrupt in some way, it has happened to me in the past. If that is the case I think your only answer is to download again and hope you are luckier this time.

You don't say what other operating systems you have on the disk. If it is windows you will have to boot into recovery console and run 'fixmbr' or 'fixboot' commands. If it is Linux you should boot into a recovery mode shell and try these commands:

```
  sudo grub
```

sudo probably not necessary because you should be root anyway.

```
find /boot/grub/stage1
```

If it locates another grub instance you will get something like:  (hd0,1) (hd0,2)
choose the instance that does not have the corrupt install and run

```
root (hd0,2)
```

then 

```
setup (hd0)
```

```
quit
```

Then reboot and hopefully you will have your original Linux installation back assuming you had one to start with.

---

