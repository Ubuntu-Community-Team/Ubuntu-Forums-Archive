---
title: "Fix Boot without Windows CD?"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Panik on 2008-09-07
All, I just did a fresh install of Ubuntu.  I can no longer boot to Windows.  An option does not show in GRUB.  

I have been searching but unable to find a solution.  I do not have my windows CD any longer (at least I can't seem to find it).  I tried to add to menu.lst by adding the below (to no avail).

```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```

I see it in the boot option in GRUB, but get an error when I try to boot into windows.

Here is what I get when I run "sudo fdisk -l"

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x972f972f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82c882c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4500    36146218+   7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2632ab10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36483   293049666    7  HPFS/NTFS
```

Any ideas or further information needed?

Thanks, I look forward to the help.

---

### Post by doas777 on 2008-09-07
what error do you get?

usually the way it works, is you extend grub to show your windws os, rather than try to switch to the windows boot loader. this [thread]("http://ubuntuforums.org/showthread.php?t=393809") discusses exactly that.

once you can boot into windows, you can invoke the recovery console by interrupting with F8, and use fixmbr if you want to completely remove ubuntu.

---

### Post by Shazaam on 2008-09-07
Depends on which drive Windows is on. If it is on sdb this is what you would put in menu.lst under Windows...
```
root (hd1,0)

```
If on sdc do this...
```
root (hd2,0)

```
here (change the x's)...
```
title Windows XP
root (hdx,x)
makeactive
chainloader +1
```

---

### Post by Panik on 2008-09-07
> **Shazaam said:**
> Depends on which drive Windows is on. If it is on sdb this is what you would put in menu.lst under Windows...
```
root (hd1,0)

```
If on sdc do this...
```
root (hd2,0)

```
here (change the x's)...
```
title Windows XP
root (hdx,x)
makeactive
chainloader +1
```

Windows is on SDB, and I changed menu.lst as you suggested.  Now all I get is "System Starting..." or "Starting ..."  or something like that, and it simply sits there.  I believe the original MBR was not on the drive windows is running on.

I think GRUB messed up the original MBR.  But I can't run fixmbr because I don't have the XP CD.  Any other ideas?

---

### Post by Shazaam on 2008-09-07
Something I haven't tried yet is using the SuperGrubDisk for restoring the Windows mbr. A link...
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
```
Windows (Advanced) leads to a menu where you can
restore Window's NTLDR bootloader's IPL to MBR (equivalent to FIXMBR),
boot Windows by its boot sector (bypassing the MBR),
boot Windows on a non-first hard disk,
set the boot flag on a Windows partition,
and
re-install Windows NTLDR's IPL to a boot sector (equivalent to FIXBOOT).
```

---

### Post by caljohnsmith on 2008-09-07
Grub sees the order of your HDDs as the same as the BIOS boot order, which is sometimes different then the HDD order in Ubuntu. So bottom line is you'll need to try two possible options to boot Windows. Just add the following to your menu.lst and one should work (assuming you don't have any other issues):
```
title Windows XP (hd1)
root (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows XP (hd2)
root (hd2,0)
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Once you find which works, you can always delete the other entry obviously. Let me know how it goes or if you need any more details/info. :)

---

### Post by Panik on 2008-09-07
> **caljohnsmith said:**
> Grub sees the order of your HDDs as the same as the BIOS boot order, which is sometimes different then the HDD order in Ubuntu. So bottom line is you'll need to try two possible options to boot Windows. Just add the following to your menu.lst and one should work (assuming you don't have any other issues):
```
title Windows XP (hd1)
root (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows XP (hd2)
root (hd2,0)
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Once you find which works, you can always delete the other entry obviously. Let me know how it goes or if you need any more details/info. :)

Well, I guess I have other issues.  Both boot options give me the exact same error.

"NTLDR is missing"

What next?

---

### Post by caljohnsmith on 2008-09-07
When you are in Ubuntu, do you have it automatically set up to mount your sdb1 Windows partition? If you do, you can use the Nautilus file browser to check if your Windows has all the boot files it needs in its root directory, namely:
```
boot.ini
ntldr
NTDETECT.COM
```
Or if you don't have windows mounted, you could do:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
And that will list all the files in the Windows root directory.

Also, are you sure sdb1 is your Windows drive, i.e. the 37 GB drive? And is it really only 37 GB? I would imagine that isn't correct. If it isn't, then you may have a problem with how the sdb drive is set up in BIOS.

---

### Post by Panik on 2008-09-07
> **caljohnsmith said:**
> When you are in Ubuntu, do you have it automatically set up to mount your sdb1 Windows partition? If you do, you can use the Nautilus file browser to check if your Windows has all the boot files it needs in its root directory, namely:
```
boot.ini
ntldr
NTDETECT.COM
```
Or if you don't have windows mounted, you could do:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
And that will list all the files in the Windows root directory.

Also, are you sure sdb1 is your Windows drive, i.e. the 37 GB drive? And is it really only 37 GB? I would imagine that isn't correct. If it isn't, then you may have a problem with how the sdb drive is set up in BIOS.

That is the correct drive.  It is a WD Raptor.  I installed windows on that drive because of it's performance.  This is the setup that I have always had.  I do think you found the problem.  But I don't know how to fix it.

The root of that drive does not have those files.  But I'm positive they were on the drive Linux is on, but I (without thinking) had the drive auto formatted when installing Linux.  But I did have a windows partition on this drive.  It contained the windows boot info.  

I am able to view all files on the windows drive.

Please tell me I'm not up the creek?

---

### Post by caljohnsmith on 2008-09-07
> **Panik said:**
> That is the correct drive.  It is a WD Raptor.  I installed windows on that drive because of it's performance.  This is the setup that I have always had.  I do think you found the problem.  But I don't know how to fix it.

The root of that drive does not have those files.  But I'm positive they were on the drive Linux is on, but I (without thinking) had the drive auto formatted when installing Linux.  But I did have a windows partition on this drive.  It contained the windows boot info.  

I am able to view all files on the windows drive.

Please tell me I'm not up the creek?
No, I don't think you are up the creek, at least not yet. :) I've attached to this post the three files that you need, all you need to do is put them in your Windows' root directory. Reboot, and see if Grub can boot Windows yet, and if not, let me know the exact errors you get.

---

### Post by Panik on 2008-09-07
> **caljohnsmith said:**
> No, I don't think you are up the creek, at least not yet. :) I've attached to this post the three files that you need, all you need to do is put them in your Windows' root directory. Reboot, and see if Grub can boot Windows yet, and if not, let me know the exact errors you get.


w00t!!  I'm booting back into windows.

You added a nice little choice where I can go back to the grub bootloader.  Pretty cool.

I only booted in once, but the boot time seemed a bit long.  In addition, the time is WAY off.. Like 2:00 am or something, yet the ubuntu time is correct.

Not sure what would have caused that.  But I am able to boot into windows again....  THANKS!!!

---

### Post by chungy on 2008-09-07
Did you fiddle with the BIOS per chance and switch around the disk order reported?  These options are meant only for installing Windows on non-primary disks, and can have serious consequences if you use them for anything but installing/running Windows on other disks...

---

### Post by caljohnsmith on 2008-09-07
> **Panik said:**
> w00t!!  I'm booting back into windows.

You added a nice little choice where I can go back to the grub bootloader.  Pretty cool.

I only booted in once, but the boot time seemed a bit long.  In addition, the time is WAY off.. Like 2:00 am or something, yet the ubuntu time is correct.

Not sure what would have caused that.  But I am able to boot into windows again....  THANKS!!!
You're welcome, glad you can boot Windows again. By the way, I forgot that my boot.ini which I sent you has been modified to include that "grub4dos" option. But unless you decide to install Grub4DOS in windows, that option won't work for you; you might as well delete it so you can just boot directly into Windows. Just open the boot.ini file in some text editor in Ubuntu and delete the last line that says:
```
C:\grldr="Grub4Dos"
```
If you need help with that let me know. Otherwise have fun with Windows and Ubuntu. :)

---

