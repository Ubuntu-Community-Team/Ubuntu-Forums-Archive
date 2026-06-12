---
title: "Trying to install 9.10 is driving me crazy"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by b4t3m4n on 2009-11-20
I have 9.10 on my laptop, it install perfectly, all was well.

I then glanced at my desktop, and decided windows 7 was boring me, why not.  

No matter what I do, the partitioner will not detect my harddrive.  Now this is only made more comical by the fact that I can mount the drive and do anything I want on it perfectly fine within the livecd.  

I am running a modern intel gigabyte board (I have a migraine and have built this computer long enough ago that I can't remember the exact version off the top of my head).

I have a 500 GB Sata drive and have tried both a livecd, and a usb install, neither could detect the drive in the partition step of the install, but both could mount it and manipulate it outside the installer.

Right now, I have the bios set to legacy IDE mode, but AHCI didn't work either.

Any suggestions would be helpful.

---

### Post by b4t3m4n on 2009-11-20
yikes, no replies :S

---

### Post by Spookster on 2009-11-20
Can't help much, but have you tried the alternate install CD? It often seems more robust in situations like this.

---

### Post by b4t3m4n on 2009-11-20
> **Spookster said:**
> Can't help much, but have you tried the alternate install CD? It often seems more robust in situations like this.


I will give it a try

---

### Post by phillw on 2009-11-20
> **b4t3m4n said:**
> I have 9.10 on my laptop, it install perfectly, all was well.

I then glanced at my desktop, and decided windows 7 was boring me, why not.  

No matter what I do, the partitioner will not detect my harddrive.  Now this is only made more comical by the fact that I can mount the drive and do anything I want on it perfectly fine within the livecd.  

I am running a modern intel gigabyte board (I have a migraine and have built this computer long enough ago that I can't remember the exact version off the top of my head).

I have a 500 GB Sata drive and have tried both a livecd, and a usb install, neither could detect the drive in the partition step of the install, but both could mount it and manipulate it outside the installer.

Right now, I have the bios set to legacy IDE mode, but AHCI didn't work either.

Any suggestions would be helpful.

Get Yourself a Live Gparted CD, slice it manually - then you can simply tell ubuntu where you want it pop itself. Not sure why you can't slice from the LiveCD - But the Gparted one should allow you to slice.  

The other thing that could, of course, be messing it up is that your BIOS is set to IDE and you have a SATA drive. I've never tried running a SATA drive like that.

Regards,

Phill.

---

### Post by noelvh on 2009-11-20
> **phillw said:**
> Get Yourself a Live Gparted CD, slice it manually - then you can simply tell ubuntu where you want it pop itself. Not sure why you can't slice from the LiveCD - But the Gparted one should allow you to slice.  

The other thing that could, of course, be messing it up is that your BIOS is set to IDE and you have a SATA drive. I've never tried running a SATA drive like that.

Regards,

Phill.

That is what I was going to say. Gparted Live CD is great!!!

Noel

---

### Post by b4t3m4n on 2009-11-20
> **phillw said:**
> Get Yourself a Live Gparted CD, slice it manually - then you can simply tell ubuntu where you want it pop itself. Not sure why you can't slice from the LiveCD - But the Gparted one should allow you to slice.  

The other thing that could, of course, be messing it up is that your BIOS is set to IDE and you have a SATA drive. I've never tried running a SATA drive like that.

Regards,

Phill.

gparted does not detect the drive

SATA is SATA, how you control it is either IDE or AHCI, the latter being the prefered method for the future.  Irregardless, neither work.

---

### Post by b4t3m4n on 2009-11-20
Its a kernel issue.  Linux Mint 7 detects the drive fine, and the only major difference between that and 9.10 when it comes to something a basic has harddrive detection would be the kernel.

shrug

add me to the list of people hating 9.10 kernel I guess

---

