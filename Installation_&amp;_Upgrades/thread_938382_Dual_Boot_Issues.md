---
title: "Dual Boot Issues"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by GreenFire08 on 2008-10-04
Alrighty, so recently I set up a dual boot system with Ubuntu and Vista. I restored GRUB to the MBR, but I keep getting Error 17. The problem is that it keeps trying to boot to (hd0,0) instead of (hd0,1) where it should be. I can edit the commands and it works fine, but whenever I restart the computer the commands reset and I have to do it over again. Does anyone know how I can permanently fix this issue?

Also, Vista is not even recognized on the GRUB menu. I don't know where to begin trying to fix that problem.

---

### Post by caljohnsmith on 2008-10-04
When you boot into Ubuntu, open a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
That will bring up your Grub's menu.lst, and in there you can modify all your Ubuntu entries to use (hd0,1) instead of (hd0,0). Also be sure to change the "#groot=(hd0,0)" to "#groot=(hd0,1). 

About booting Vista, first post:
```
sudo fdisk -lu
```
And we can go from there. :)

---

### Post by JBWhitley on 2008-10-04
Don't know if this will help you, but reinstate the windows boot section:  

Try this:  [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

---

### Post by GreenFire08 on 2008-10-04
```
sudo fdisk -lu
```

I got this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12ac4d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95811660   205471349    54829845    7  HPFS/NTFS
/dev/sda2       205471350   301266944    47897797+  83  Linux
/dev/sda3       301266945   312576704     5654880    5  Extended
/dev/sda4              63    95811659    47905798+  83  Linux
/dev/sda5       301267008   312576704     5654848+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by caljohnsmith on 2008-10-04
OK, just add this entry to the end of your Grub's menu.lst, and you should be able to boot Vista if there are no other issues:
```
title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```
If that doesn't work, let me know exactly what happens after you choose that entry from the Grub menu on start up. Otherwise let me know how it goes. :)

---

### Post by GreenFire08 on 2008-10-04
Okay, I made all the changes to menu.lst like you said, and nothing happened. Both problems still exist. Does that mean there's something wrong with GRUB?

---

### Post by caljohnsmith on 2008-10-04
OK, I think I see your problem--you have two linux partitions, so probably the one you booted into is not the one that is in control of Grub in the MBR (Master Boot Record). So what exactly are partitions sda2 and sda4? Which one is Ubuntu? Whichever one you boot into, post the output of the following: 
```
mount | grep " / " | awk '{print $1}'
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
cat /boot/grub/menu.lst
```

---

### Post by Major Pain on 2008-10-04
I'm pretty new at this stuff, and I'm also trying to find the answer to a similar problem, but have you seen this post yet?

[http://www.debian-administration.org/users/fsateler/weblog/13]("http://www.debian-administration.org/users/fsateler/weblog/13")

Maybe it can provide some assistance.  Maybe not.  Like I said, I'm new.

---

### Post by theozzlives on 2008-10-04
Vista may be recognized as Longhorn, at least to Pioneer it is.

---

### Post by GreenFire08 on 2008-10-05
> **caljohnsmith said:**
> OK, I think I see your problem--you have two linux partitions, so probably the one you booted into is not the one that is in control of Grub in the MBR (Master Boot Record). So what exactly are partitions sda2 and sda4? Which one is Ubuntu? Whichever one you boot into, post the output of the following: 
```
mount | grep " / " | awk '{print $1}'
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
cat /boot/grub/menu.lst
```


Thanks for your help, here's what happened. Somehow I had made a copy of my original Ubuntu partition, and that was the one I kept booting into. I simply deleted the extra partition and changed menu.lst to fit the new settings, and everything works perfectly now. Thanks again. :)

---

### Post by GreenFire08 on 2008-10-05
Never mind, everything is not working perfectly. Vista still won't boot. It is listed under GRUB, but when I try to select it it tells me that it's missing or corrupt. Do I have to re-install? I hope not.

---

### Post by caljohnsmith on 2008-10-06
> **GreenFire08 said:**
> Never mind, everything is not working perfectly. Vista still won't boot. It is listed under GRUB, but when I try to select it it tells me that it's missing or corrupt. Do I have to re-install? I hope not.
So are you still using the Vista entry from post #5? If so, what is the exact error you get when booting it--i.e. does it say some specific file is missing or corrupt? Do you have a Vista Recovery CD? It sounds like you will probably need it, so if you don't have one, you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). When you installed Ubuntu, did you use Ubuntu's partition editor (gparted) to make space on your drive for Ubuntu, or did you previously make space with Vista's Disk Management?

---

### Post by GreenFire08 on 2008-10-06
I used gParted - is that the problem?

I was thinking that Vista might not be on (hd0,0). When I select Vista from the GRUB menu, it says this, word for word.

> Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \Windows\system32\winload.exe
Status: 0xc0000001
Info: The selected entry could not be loaded because the application is missing or corrupt.

Here's what I get when I input```
sudo fdisk -lu
```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12ac4d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95811660   205471349    54829845    7  HPFS/NTFS
/dev/sda3       301266945   312576704     5654880    5  Extended
/dev/sda4              63    95811659    47905798+  83  Linux
/dev/sda5       301267008   312576704     5654848+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

All I did was delete the extra Linux partition. My main one is now (hd0,3) if that helps.

---

### Post by caljohnsmith on 2008-10-06
OK, first make sure your Grub menu still uses (hd0,0) for Vista, and then you'll need to use a Vista Recovery CD to repair your Vista; if you don't have one, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). 

When you boot the Vista Recovery CD, you can either do a "Vista Repair" from the menus, or if you can get a command line, just run:
```
bootrec /rebuildbcd
```
That will probably be all it takes to get Vista working again, but let me know how it goes or if you run into problems.

P.S. Using gparted (or any other partition editor) to do any partition changes on a drive that has Vista is unfortunately a problem; Vista (unlike any other OS I know of) maintains its own partition table outside of the main partition table in the HDD's MBR (Master Boot Record). In practical terms that means if you use gparted or any partition editor other than Vista's Disk Management to make partition changes, it can break Vista; that's because the partition editor will update the MBR partition table like it should but of course won't update Vista's own partition table. So bottom line is, if your HDD has Vista, it is always best to use Vista's Disk Management to make any partition changes.

---

