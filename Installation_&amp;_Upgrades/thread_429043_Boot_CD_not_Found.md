---
title: "Boot CD not Found"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Ozenbac on 2007-04-30
I'm trying to install 7.04 on my desktop and I've done all my backups and fraged the hard drive but the Ubuntu boot cd is never found.  I get a "NTLDR missing" error which is a windows error, which makes me think its a FAT32/NTFS conflict.  But I have an empty box and I don't know how to covert the drive the required format without an os.  Ideas?

(i've also burned the cd twice and run it inside windows successfully)

---

### Post by rsambuca on 2007-04-30
Did you burn it as a CD *image*??  If you open it up in Windows explorer, do you see one large file, or a bunch of files and folders?  You should see the latter.  If not, you probably need to burn another CD, but this time as an iso image.

---

### Post by Ozenbac on 2007-04-30
No it burned correctly.  I even get the Ubuntu DiskTree when I run it on my laptop.

---

### Post by rsambuca on 2007-04-30
I'm not sure what the ubuntu disk tree is, but I'll assume you are correct.  I guess the next thing to check is that your bios is set to boot from the CD drive first.

---

### Post by randell6564 on 2007-04-30
> **rsambuca said:**
> I'm not sure what the ubuntu disk tree is, but I'll assume you are correct.  I guess the next thing to check is that your bios is set to boot from the CD drive first.
I agree!  Not really sure WHAT exactly you are doing 'Ozenbac', but if you wiped your HD and you are attempting to do a clean install of Ubuntu, then 'rsambuca' is right.  There is really no other reason that your box could not find the boot CD.

---

### Post by Ozenbac on 2007-04-30
Sorry, I should have mentioned that in the first post. CD is the first boot device.

---

### Post by randell6564 on 2007-04-30
> But I have an empty box and I don't know how to convert the drive to the required format without an os.  Ideas?
Ubuntu will "convert" the drive.  Did you WIPE your HD? (Format it?)

---

### Post by Ozenbac on 2007-04-30
Entire drive is formatted.

---

### Post by rsambuca on 2007-04-30
Do you have any other bootable CD's you can try in the drive to test it?

---

### Post by randell6564 on 2007-04-30
> **Ozenbac said:**
> Entire drive is formatted.
Check [THIS]("http://support.microsoft.com/kb/314057") out.

---

### Post by randell6564 on 2007-04-30
I use to get this error all the time when I had several test boxes in my garage.  You need to get a hold of a Windows boot disk and do a:
```
fdisk mbr
```

---

### Post by randell6564 on 2007-04-30
[Windows boot disk]("http://www.bootdisk.com/bootdisk.htm")

---

### Post by Ozenbac on 2007-04-30
> **rsambuca said:**
> Do you have any other bootable CD's you can try in the drive to test it?

Thank you for the tip.  I got it working by setting the primary boot as a floppy drive (which I don't have) and loading the cd into the secondary cd-rom.  Who knows why, but hell, it works.  Thank you to everyone, I didn't expect such informed or prompt responses.

---

### Post by randell6564 on 2007-04-30
> **Ozenbac said:**
> Thank you for the tip.  I got it working by setting the primary boot as a floppy drive (which I don't have) and loading the cd into the secondary cd-rom.  Who knows why, but hell, it works.  Thank you to everyone, I didn't expect such informed or prompt responses.
WHA,WHAT???!!  Please post a tutorial on how you got THAT to work my friend! lol!

I'm going to guess that Ubuntu was just not recognizing your Primary cd-rom.  I have two cd-rom's as well,  and one NEVER works, but the other works just fine.  Don't know why, don't really CARE as long as I get done what I WANT to get done!
CHEERS!!

---

