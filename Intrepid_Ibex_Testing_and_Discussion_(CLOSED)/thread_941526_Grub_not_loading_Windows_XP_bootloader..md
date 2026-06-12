---
title: "Grub not loading Windows XP bootloader."
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SledgeHammer_999 on 2008-10-08
Hi my problem may be a side-effect of the things I describe here-->[http://ubuntuforums.org/showthread.php?t=941521](http://ubuntuforums.org/showthread.php?t=941521)

If you read the above link, I assume that my Windows install is either on (hd1,0) or (hd2,0). But no matter what I do the Windows bootloader never gets called. All I get from grub is "Starting up" and a flashing cursor but it just stays there. My only solution is to boot directly to the Windows disk and not use grub.

The relevant part of menu.lst:
> 
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1


I also tried from the livecd to "sudo grub/root (hd0,0)/setup (hd0)" but it didn't work.

Any ideas?

---

### Post by Delvien on 2008-10-08
> **SledgeHammer_999 said:**
> Hi my problem may be a side-effect of the things I describe here-->[http://ubuntuforums.org/showthread.php?t=941521](http://ubuntuforums.org/showthread.php?t=941521)

If you read the above link, I assume that my Windows install is either on (hd1,0) or (hd2,0). But no matter what I do the Windows bootloader never gets called. All I get from grub is "Starting up" and a flashing cursor but it just stays there. My only solution is to boot directly to the Windows disk and not use grub.

The relevant part of menu.lst:


I also tried from the livecd to "sudo grub/root (hd0,0)/setup (hd0)" but it didn't work.

Any ideas?

Try 

```
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1
```

That's what mine is on.

---

### Post by SledgeHammer_999 on 2008-10-08
This doesn't make sense. Ubuntu is on hd0, Windows is on hd1(or hd2). Plz read the post I link to first.

---

### Post by caljohnsmith on 2008-10-08
When booting Windows XP from any drive other than the boot drive, you have to fool XP into thinking it is on the boot drive using Grub's mapping technique:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
One of the above entries should work for you assuming you don't have any Windows XP issues. Let me know how it goes. :)

---

### Post by WWSmith36 on 2008-10-08
To get better help please post the output of

```
sudo fdisk -l
```

Thank you

---

### Post by SledgeHammer_999 on 2008-10-08
> **caljohnsmith said:**
> When booting Windows XP from any drive other than the boot drive, you have to fool XP into thinking it is on the boot drive using Grub's mapping technique:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
One of the above entries should work for you assuming you don't have any Windows XP issues. Let me know how it goes. :)


Thank you that did the trick(hd1). But I am wondering do I need to do this now? I had the SAME setup with hardy/gusty/feisty and I didn't need to use the map command.

---

### Post by caljohnsmith on 2008-10-08
> **SledgeHammer_999 said:**
> Thank you that did the trick(hd1). But I am wondering do I need to do this now? I had the SAME setup with hardy/gusty/feisty and I didn't need to use the map command.
If you don't use Grub's mapping trick, the only other way I know of that you can boot Windows XP from a drive other than the boot drive is to modify Windows' boot.ini file. I don't think Vista has the same limitation as XP, so Vista will let you boot from a secondary drive without using Grub's mapping technique. If you were previously able to boot Windows XP without using mapping, my only guess might be that you had Grub installed to the MBR of your Windows drive, so you were actually booting from the Windows drive on start up; in that case you wouldn't have to do any drive mapping.

---

### Post by WWSmith36 on 2008-10-09
If your windows disk is the primary drive (hd0) and grub is installed to its MBR you will be fine.

The other posts are correct in calling for the map command.  Windows must be installed on the primary hard drive or it will not chainload properly.  The map command is used to fool windows in thinking that it is on the primary hard drive.  The windows ntldr and boot.ini explictly call for the primary disk.

Hope this helps

---

