---
title: "&quot;error loading operating system&quot;"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by ksukat on 2006-09-11
greetings,
I downloaded a burned an iso of the ubuntu-6.06.1-desktop-i386.
I booted from the iso image and it loaded ubuntu.  I then ran the install (clicked on the install icon).  I have two hard drives in this computer. 1 is a scsi drive, the other is an IDE drive.

I installed on the scsi hard drive, told it to erase the disk and install on it.  Installed just fine with no errors.  Reboot the computer and install to the IDE hard drive this time.  Same error.  Simply "Error loading operating system".

I had the BIOS boot sequence set to SCSI,CDROM,Floppy.  On the IDE attempt, I had it set to CDROM,C,Floppy.

So what am I missing ?

thanks in advance,
D

---

### Post by ajgreeny on 2006-09-11
So do you mean you installed onto the scsi and ide drives in two separate installs on the same computer?  Is this because the first attempt onto the scsi drive failed to boot?  And the same with the ide drive?

If that is the case you should check that the download was OK with the md5sum, just in case the iso file is faulty.

---

### Post by ksukat on 2006-09-11
The download was fine.
The install on the SCSI went without error (no errors during
install), but when rebooted, gave the "Error loading...". 
Then, thinking it was related to which disk was seen, I installed
on the IDE drive.  This too went with no error, but when rebooted generated the "error loading..." error.

Thanks for any guidance.

-D

---

### Post by ballen12 on 2006-09-11
i'm getting the same error.  i have an asus A8N-SLI Premium mobo with an AMD X2 64-bit 3800+ processor with 1 gig of RAM and dual nvidia GeForce 7600 GT's and a 400gig western digital hard drive.  i boot the live cd (6.06 64-bit edition) and it runs fine.  i use the install icon on the desktop and it runs through without any errors.  when it reboots, the computer POST's and then just says, "error loading operating system".  i've used several different downloads of 6.06 and this one is the only one that loaded all the way through but it won't boot off the hard drive for some reason.  any assistance would be wonderful.  i really would like to try ubuntu.

---

### Post by ballen12 on 2006-09-12
ok, it must just be the SATA drive.  i had a spare 80 gig western digital PATA drive laying around, made it the primary boot disk and loaded ubuntu on it just fine.  if anyone has any idea why the SATA drive would not boot, let me know.  until then, guess i'll use ubuntu on my 80 gig drive... :)

---

### Post by randell6564 on 2006-09-12
I'm going to guess that Ubuntu installed the grub bootloader to your IDE HD and does not recognize your S-ATA device.

Check out this link [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

Good luck!

---

