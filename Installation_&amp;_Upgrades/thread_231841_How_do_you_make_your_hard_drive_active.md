---
title: "How do you make your hard drive active?"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by joople on 2006-08-07
Hi all,
Can someone please give me information on making my hard drive active? Thanks

---

### Post by hopstah on 2006-08-07
i'm not quite sure what you mean, but if you want to read / write to your hard drive, you need to mount it.

you do this by creating a folder where you want the drive to be - for me, my music hard drive is mounted at /media/music/

next, you need to tell the computer that you want to mount the drive.  for me, this is done by ```
sudo mount /dev/hdd1 /media/music
```

obviously you need to change 'hdd1' to your hard drive and partition.

to get it to automatically mount at boot, you need to add a line to your /etc/fstab file.  search the forums for details on doing that as well as the proper syntax of that file.

i hope this helps a bit!

---

### Post by joople on 2006-08-07
thanks,  the problem is i think that it is not mounting my Ubuntu hard drive on boot because I get the Disk Boot Failure message.  So could I sudo on the Live CD and get it to configure right. Obviously I have no other option, then to use the terminal on the Live cd since i can't get into my installed Ubuntu.

---

### Post by confused57 on 2006-08-07
Isn't there an option when the Live CD starts "Boot to Hard Disk" or something similar?  I've seen other people try this & are able to boot into their Linux install...a temporary fix, but you can try.
Also, you could try reinstalling grub from the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Are you using SATA drives or IDE?  If you could tell us a little more about your system, if IDE, did you install Ubuntu to master drive...how you installed?  Jumper settings correct, IDE controllers enabled in bios, etc?

The more info you can furnish, the better chance someone might be able to help you come up with a solution.

From the Live CD, what is the output of:
```
sudo fdisk -l
```
The -l is a small "L"

---

### Post by joople on 2006-08-08
Yes there is an option to Boot from first Disk on the Live CD.  But when I do that I get this: 
Booting from local disk...
isolinux: Disk error 80, AX = 0201, drive 80
Boot failed: press a key to retry...

I have already re-installed GRUB a dozen times to the MBR.

I'm using ATA IDE drive.

It is on the master cable, Jumper set to cable select. by the way I have configured this to all sorts of ways. I've been down that road already.  And it shows up in the BIOS. more info on my problem here...[http://www.ubuntuforums.org/showthread.php?t=231773]("http://www.ubuntuforums.org/showthread.php?t=231773")

---

### Post by joople on 2006-08-08
Oh Here is what my Sudo fdisk -l looks like:

```
Disk /dev/hda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2389    19189611   83  Linux
/dev/hda2            2390        2495      851445    5  Extended
/dev/hda5            2390        2495      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       15504   117210208+   7  HPFS/NTFS

Disk /dev/sda: 1014 MB, 1014497280 bytes
250 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8000 * 512 = 4096000 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         248      990704    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 249, 32) logical=(247, 169, 32)
```

---

### Post by confused57 on 2006-08-08
If you are able to boot Windows connected as the master drive and the Ubuntu drive disconnected, you might want to consider reinstalling Ubuntu using this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Using this method, your Windows installation will remain bootable...

I don't know which methods you used to reinstall grub, but I've used the method I linked you to, with great success.

Added: You might want to try a different brand of blank CD to burn the iso to.
A long shot, but some bios have an anti-virus built-in(so I've read)...may want to check for this in your bios...it would prevent grub from being correctly installed.

---

### Post by joople on 2006-08-08
Thanks you for the reply.  I have looked at your thread many times already and used those examples too, and nothing will work, but I'm now only using one drive to install Ubuntu.  I have the other hard drive unhooked from the computer when I try to install Ubuntu just because I want to rule out any problems involved with dual booting.  Believe me when I tell you I've tried eveerything. 

P.S. It only showed that I had windows because at the time that I Sudo fdisk -l  I had the other hard drive plugged in because I needed to use Windows.

Like I had in my other thread.  I need to somehow think outside the box on this one. I've done everything. 

Maybe Ubuntu just doesn't like this hard drive or something. Right now that is my own explanation at this point.  I know the hard drive works because I had Windows Xp on Before.  Damn this sucks A#@!

---

### Post by joople on 2006-08-09
*BUMP* Sorry, I'm still unbelievably stuck!:confused:

---

### Post by joople on 2006-08-09
Oh by the way I used Kponnix to see if my partitiion was active and  it was.  And i still have a problem I guess I'll post a new question on a new thread. I guess no one has a clue just like me.

---

### Post by confused57 on 2006-08-09
I honestly don't know what's going on with your system...if you want to try installing with the alternate cd and installing grub to a floppy instead of the mbr, you can try this:
[http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy)

The desktop live cd doesn't give you the option of where to install grub, it automatically installs to the mbr.

Did you check if your bios has some kind of anti-virus that would possibly prevent grub from being installed?  I'm probably way out in left field on that idea.

---

### Post by joople on 2006-08-09
yea i've used the alternate cd and installed to floppy before and it still didn't work.  You're not way out in left field.  That's exaclty what I want to think out side the box i appreciate the idea. but no there is no anti-virus that i am aware of and ive looked all in BIOS.

---

