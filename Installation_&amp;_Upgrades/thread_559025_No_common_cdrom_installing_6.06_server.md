---
title: "No common cdrom installing 6.06 server"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by starkey on 2007-09-24
While attempting to verify the CD and/or install to hard disc, I get a 6.06 server error saying "no common cdrom drive found."

I'm installing from a DVD R/W drive, to be precise a Lite-On IT Corp. DH-20A3P.  Can anyone tell me where I can find a driver?  /dev on the install cd doesn't have a cdrom or anything I'd guess to be a cd drive.

Thanks,
Starkey

---

### Post by ddrichardson on 2007-09-25
I haven't tried this personaly but apparently passing this option:```
libata.atapi_enabled=1
```helps.

---

### Post by starkey on 2007-09-27
Thanks for the suggestion.  I added the "libata.atapi_enabled=1" to the boot options but the kernel said, "Not a valid boot option, ignoring" and continued to the same result as before: the install script continued through selection of language, country and keyboard, then failed to mount the cdrom drive.

The script asks for cd drivers on floppy, but I don't know what it wants.  There's no cd* or sg* driver in /dev on the install cd so I'm in the dark as to where to go.

Best regards,
Starkey

---

### Post by ddrichardson on 2007-09-27
[More]("http://www.togaware.com/linux/survivor/SATA_CD_DVD.html").

---

### Post by starkey on 2007-09-28
Thanks for the reference to the didactic dissertation.  I'm not sure whether I can do the edits on the ramdisk to accomplish the installation, or those changes need to be made for a hard disk install.

I think I may have simply bypassed the problem by trying 7.04 Server.  I successfully downloaded *almost* all the iso file and burned a disc.  Though the iso was incomplete and thus deemed corrupt, it nonetheless booted the kernel and successfully mounted the DVD drive, so I think if I can just get a clean download it will work.

Thanks again for your assistance - I'll let you know how it all turns out.
Best regards,
Starkey

---

