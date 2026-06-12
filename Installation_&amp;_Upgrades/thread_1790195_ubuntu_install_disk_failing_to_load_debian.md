---
title: "ubuntu install disk failing to load debian"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by sk3499 on 2011-06-24
Hey all,
   i have a new system I am trying to install ubuntu on, and it fails to load debian for the install. It gives this error "unable to find a medium containing a live file system".

It works on my other 2 computers? Could it be incompatibility with new hardware, or something like that?

Any suggestions?

Gparted also fails to load for the same reason.

System parts:
Core i7 2600k
3TB Hitachi harddrive on SATA3
ASROCK P67 extreme 4 mobo, with USB3.0

Thanks

---

### Post by dabl on 2011-06-24
In BIOS, you need to enable boot from removable media.  Then also in BIOS you need to set the optical drive as the first boot device on the list.  I think your problem is in BIOS settings.

---

### Post by sk3499 on 2011-06-24
No, i have that set already int he bios, and it starts loading ubuntu then fails because of the error.

I think this is an incompatibility issues. I tried loading Fedora and it says that my chipset is not supported and I should report the bug.

edit: the ironic part is windows actually loaded without problem...

---

### Post by MAFoElffen on 2011-06-24
> **sk3499 said:**
> Hey all,
   i have a new system I am trying to install ubuntu on, and it fails to load debian for the install. It gives this error[COLOR=Red] "unable to find a medium containing a live file system"[/COLOR].

It works on my other 2 computers? Could it be incompatibility with new hardware, or something like that?

Any suggestions?

Gparted also fails to load for the same reason.

System parts:
Core i7 2600k
3TB Hitachi harddrive on SATA3
ASROCK P67 extreme 4 mobo, with USB3.0

Thanks
So this box does not load anyone's LiveCD?  (You mentioned Gparted...) Not even the Isolinux boot menu of the Ubuntu LiveCD?  The reason dabl mentioned (below) your BIOS and CD drive is that the error message above usually comes from your drive having problems reading the  LiveCD live filesystem or an error in creating needed temporary files.
> **dabl said:**
> In BIOS, you need to enable boot from removable  media.  Then also in BIOS you need to set the optical drive as the first  boot device on the list.  I think your problem is in BIOS  settings.
> **sk3499 said:**
> No, i have that set already int he bios, and it starts loading ubuntu then fails because of the error.

I think this is an incompatibility issues. I tried loading Fedora and it  says that my chipset is not supported and I should report the bug.

edit: the ironic part is windows actually loaded without problem...So there is another possibility here.... The question to preface this is--
Which PC did you create your LiveCD from?

Little story-- I volunteer at a computer recyclers.  We test drives by creating one CD on one known good main CD/DVD rw drive and test in on other candidates.  You would be surprized how many drives fail that!!!  Fine if you create a disk on one drive and boot/read it on the same drive-- You mentioned you had 3 desktops... 

Just an idea. First check the checksum of your download... If good, then create it from another PC (Best would be to create it from the drive you are trying to read/boot from.)

Be sure you can Run (Try) the LiveCD on that box first, before trying to install. (from what I see, the hardware "should" be compatible.

---

### Post by sk3499 on 2011-06-24
> **MAFoElffen said:**
> So this box does not load anyone's LiveCD?  (You mentioned Gparted...) Not even the Isolinux boot menu of the Ubuntu LiveCD?  The reason dabl mentioned (below) your BIOS and CD drive is that the error message above usually comes from your drive having problems reading the  LiveCD live filesystem or an error in creating needed temporary files.

So there is another possibility here.... The question to preface this is--
Which PC did you create your LiveCD from?

Little story-- I volunteer at a computer recyclers.  We test drives by creating one CD on one known good main CD/DVD rw drive and test in on other candidates.  You would be surprized how many drives fail that!!!  Fine if you create a disk on one drive and boot/read it on the same drive-- You mentioned you had 3 desktops... 

Just an idea. First check the checksum of your download... If good, then create it from another PC (Best would be to create it from the drive you are trying to read/boot from.)

Be sure you can Run (Try) the LiveCD on that box first, before trying to install. (from what I see, the hardware "should" be compatible.

Gparted Live Cd, Ubuntu Live Cd, and fedora Live CD all fail. The error is the as quoted above for ubuntu and Gparted. The error for Fedora says incompatible chipset... contact them...

I did check all the CDs on other computers first and they work. they were made on my laptop.

---

### Post by MAFoElffen on 2011-06-24
> **sk3499 said:**
> Gparted Live Cd, Ubuntu Live Cd, and fedora Live CD all fail. The error is the as quoted above for ubuntu and Gparted. The error for Fedora says incompatible chipset... contact them...

I did check all the CDs on other computers first and they work. they were made on my laptop.And an ASROCK P67 extreme 4 motherboard is a desktop board, right?  So the CD's were made from your laptop and you are trying to boot thwem on your desktop right?  

Is this desktop running Windows and networked to the other 2?  Where you could go workgoup and burn the CD from that desktop?

---

### Post by dabl on 2011-06-25
I assume the new optical drive is a SATA drive, right?  You might try twiddling the "mode" on the BIOS SATA channel -- if it is set on AHCI, try "Legacy" or "IDE compatibility" or whatever the other option is.

If that doesn't help it read the CD, and you're sure the BIOS settings are all appropriate, then I'm getting suspicious about the optical drive and its cable.  If you have another optical drive that you could swap in, you might be able to narrow down whether the problem seems to relate to the optical drive unit, or is generic to that motherboard with any optical drive.

---

