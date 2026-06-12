---
title: "Dual boot grub problem"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Octol on 2007-02-18
I just installed ubuntu on my desktop and when I start it up I get a mesage that says "Error no operating system found".  Grub is installed on hd0.  I have 3 hard drives this is the output of fdisk -l

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       39166   314600863+   7  HPFS/NTFS
/dev/sdb2   *       39167       48253    72991327+  83  Linux
/dev/sdb3           48254       48641     3116610    5  Extended
/dev/sdb5           48254       48641     3116578+  82  Linux swap / Solaris

```

I am currently using the cd and I have no idea what to do now.

---

### Post by Kateikyoushi on 2007-02-18
Try to change which HDD to boot in BIOS maybe you are trying to boot one where grub isn't installed.

---

### Post by Octol on 2007-02-18
Ok Grub now boots but I get an error 22.  How do I fix that?

---

### Post by confused57 on 2007-02-18
Here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

Here's something you might try, with the live cd booted up first, open a terminal, enter:
```
sudo grub
```
then at the grub prompt, enter"
```
find /boot/grub/stage1
```
make a note of where the root partition is(e.g. (hd2,1)
to exit grub, enter:
```
quit
```

Remove the cd & boot to the hard drive which has grub on the mbr, highlight the Ubuntu entry, press "e" to edit, then change the line with root to the partition the above command found, then press "b" to boot...this change is temporary, you'd need to make it permanent in your /boot/grub/menu.lst.

Which drive has Windows installed?   There may be a better way to get your system to boot, if you could furnish this info...

---

### Post by Octol on 2007-02-18
Grub is on the mbr of hda(hd0). Windows is on hda1 and ubuntu is on sdb2.  Also when I boot from hda all I get is grub error 22 and then I can't do anything.

---

### Post by confused57 on 2007-02-18
What you can try is to install grub to the sdb mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Once you've installed grub to sdb mbr, then in bios,  set sdb as your first boot device and hda(with Windows) as your second boot device.  Then boot to the grub menu on the sdb mbr, highlight the entry to boot Ubuntu, press "e" to edit, change the root line to (hd0,1), then press "b" to boot...if it works this change is temporary, you can make it permanent in your /boot/grub/menu.lst.
You can add an entry to boot Windows, similar to the one in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If these suggestions work, no guarantees, you might want to restore your Windows mbr, so that you can boot the drives independently of each other, if you ever need to:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or you can use the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Someone else may have an easier way of solving your grub problem, if you'd rather wait for a better solution.

---

### Post by Octol on 2007-02-18
I got grub to load and I am in ubuntu right now.  Now what do I need to edit in the menu.lst file so I can boot windows?  The link you gave me said to copy this into the menu.lst.  Do I need to change anything for my setup?
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

Also do I make it permenant by changing 
```

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet splash

```

to

```

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet splash

```

---

### Post by confused57 on 2007-02-18
Yes, both should work...also, while you're in your /boot/grub/menu.lst, you might want to change the groot line to (hd0,1), as described here:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

There is a kernel update available, that will change everything back to the way you first had it, if you don't.  Update-grub looks at this line to make new kernel boot entries, when the kernel is updated.

---

### Post by Octol on 2007-02-19
I made all of the changes, rebooted and tried to run windows, It gave me this error:
```

NTLDR not found
pres Ctrl-Alt-Del to restart

```

So I rebooted and intead of going to the menu it went strait to the same error message.  I then reverted menu.lst to it's backed-up copy and rebooted, and it still gives me that same error without showing the menu.  It just goes from a black screen to that error.

---

### Post by confused57 on 2007-02-19
It looks like you may need to repair your Windows mbr and possibly ntldr...

See this guide for restoring your Windows mbr, set your drive with Windows as the first boot hard drive:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Basically, what you'd do is bootup with your Windows installation cd(not a recovery cd), press "R" for recovery mode, then the command **fixmbr** would repair the mbr, and **fixboot** "should" repair the ntldr.
I've never had to do this before, but I've read it as solutions to restore booting to Windows, you may want to do a forum search for repairing ntldr.

After, you're able to boot Windows from your Windows drive, then you can go back to booting from grub.

You might also want to look into the Super Grub Disk(approx 500 kb download):

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It can be used to boot Windows or Ubuntu, or to restore Windows mbr or boot Ubuntu.

Here's someone who had a similar problem, without having to restore Windows mbr:
[http://www.ubuntuforums.org/showthread.php?t=343578&highlight=ntldr](http://www.ubuntuforums.org/showthread.php?t=343578&highlight=ntldr)

Added:
I don't know if you've tried anything yet, but I just thought of something you can try:
if you can boot into Ubuntu, open a terminal, enter:
```
gksudo gedit /boot/grub/device.map
```
if you're continuing to boot to your Ubuntu drive first,change your device map so that your Windows drive is (hd1).

also, in your Windows entry, try replacing the line:
```
root (hd1,0)
```
to
```
rootnoverify (hd1,0)
```

You also might want to try this entry to boot Windows:

```
title              Windows XP
rootnoverify     (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader +1
```

Also, when you make changes to your Ubuntu entries, change only the line with root (hd0,1), leave everything else as it is for the kernel entries.

---

