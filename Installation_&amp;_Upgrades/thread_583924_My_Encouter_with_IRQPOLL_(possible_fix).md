---
title: "My Encouter with IRQPOLL (possible fix?)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by timothyyip on 2007-10-20
I not expert enough to comment on why/how, however I'm hoping some of you may find it useful.  I will try to list out the events I have encountered:

Some hardware that may be in the question:
No floppy drive
1xSATA Plextor DVD burner
2xSATAII HDD
Abit AB9 P965 M/B
Core2Duo E6300 + 2gb RAM (overclocked but shouldn't be related)

Trying to install Gutsy.

- First Installation attempt:
Got multiple error message while trying to boot live CD, error message is along the line of
[high int no.] ata[1,2,3or4].00 xfermode error
[high int no] Buffer I/O error on device fd0, logical block 0

Went into Bios and where it asks what is on Floppy A, I changed it from 3.5Floppy to None.(I never had floppy drive, but i never bothered to change it)

-Second Attempt
The amount of error message seems to have cut down, but it still won't boot

Apparantly this is a common problem and the community suggested using IRQPOLL command before booting, it worked.  

-Third Attempt
Installed Gutsy and everything was fine, I was expecting having to insert IRQPOLL again after installation in the /boot/grub folder but there was no problem at all.

Afterwards I was messy about with configurations and testing things out (and destroying stuff), and decided it was time to reinstall.  This time I went into BIOS again to see if I missed anything out and noticed there was the FDC option (FDC=Floppy Disk Controller) which I left on, I turned it off and booted the CD.

-Fourth attempt
Booted Live CD without IRQPOLL!!!  Installed as usual but....
Similar message after installation when booting from HDD

i went into BIOS again knowing it had to be my DVD drive as suggested by others.  This time, where it lists the Drives detected, I disabled the SATA port which my DVD drive is connected, so the BIOS won't load/detect my DVD drive at all.  At this point I'm just trying to get it to boot so I can insert IRQPOLL option in the /boot.

Rebooted, the BIOS screen clearly didn't detect the drive at all, Gutsy booted fine but....
When I put a CD in, Ubuntu detects it and mounts it?!?!?!?!  I currently have no explanation for this.  

I will go into windows later tonight and see if Windows can see the DVD drive (dual boot machine), but seriously, this is going into the X-File zone :lolflag:

---

### Post by timothyyip on 2007-10-21
update:

Doesn't work after cold reboot, same problem.

Tried booting from Fiesty CD, same problem.

Dapper booted fine though.

Window couldn't boot too, got the NTOSKRNL corrupted message when trying to boot windows.  Fixed it using fixmbr in recovery console but it seems like it I got alot of other corrupted files/index entries too which I'm currently trying to fix using chkdsk.

After a bit more searching it seems like the incompatability issue points towards the JMicron SATA controller on my AB9 M/B.  Reasons and reference I posted here in another thread specifically on the issue of AB9:
[http://ubuntuforums.org/showthread.php?p=3587913#post3587913](http://ubuntuforums.org/showthread.php?p=3587913#post3587913)

---

### Post by austinjh on 2007-10-21
I also have had similar problems but I gave up using the Live CD and so used the alternate-amd64 CD to do a text based install.

I have an integrated JMicron SATA controller also.

After rebooting I got the Ubuntu splash loading screen but this halted at first stages of loading. After about 5 minutes the splash screen disapeared and I was left with an INITRAMFS prompt.

I removed the "splash" boot option from the grub loader and caught an error with "IRQ 19 nobody cares".

Oddly enough this only happened about 4 out of 5 five times attempting to boot.

adding IRQPOLL option to the boot options in grub clears this problem so I have now permanently added this into my menu.list.

---

