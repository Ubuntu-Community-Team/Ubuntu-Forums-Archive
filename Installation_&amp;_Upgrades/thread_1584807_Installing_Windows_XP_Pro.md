---
title: "Installing Windows XP Pro"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by skumnull on 2010-09-29
I have Ubuntu 10.04 LTS installed, But i want to also Install Windows XP Pro. 

Ive done research for days and nothing is working. I tried Booting from the Windows XP cd. It starts to install then says a fatal error had occured and windows had to shut down. Can somebody help me out?

---

### Post by cooprocks123e on 2010-09-29
That's probably a problem with your computer or your XP disc. If you can, be more specific.

---

### Post by 0N3 on 2010-09-29
Installing XP after Ubuntu will wipe out your Ubuntu grub you going to have to install grub again ideally you should install XP first
How new is this computer and and at what point exactly does this happen
As the previous post above said a bit more specifics would really help

---

### Post by skumnull on 2010-09-29
I put the XP CD in the dvd drive. 

I restart the computer.

I boot from CD.

Windows XP begins set up in the bluescreen.

20 seconds later, it says there was a fatal error and windows had to shutdown.

It might be the cd. It was given to me by a friend. Im gonna try to burn a new one and see how it works out.

But, could it be doing that because of ubuntu?

---

### Post by Mark Phelps on 2010-09-29
> **skumnull said:**
> But, could it be doing that because of ubuntu?

Generally ... no.  But, if you have your whole drive dedicated to Ubuntu, XP won't find any free space to format. Unless you have free space already or an NTFS-formatted partition available, I believe that XP will not install.

---

### Post by skumnull on 2010-09-29
> **Mark Phelps said:**
> Generally ... no.  But, if you have your whole drive dedicated to Ubuntu, XP won't find any free space to format. Unless you have free space already or an NTFS-formatted partition available, I believe that XP will not install.


How do I create a NTFS partition?

I tried formatting the entire HDD into NTFS, but it erased ubuntu and still gave me the fatal error message.

---

### Post by skumnull on 2010-09-29
So i made a new XP setup CD. 

Same error. 

when in the XP setup bluescreen, when it says "setup is starting windows" i get this

STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)

Im sure it has to do with the partitioning. can somebody help me out? How do i format my HDD to setup Windows XP?

---

### Post by wilee-nilee on 2010-09-29
The first part of the error message has links on the web here is one.
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---

### Post by skumnull on 2010-09-29
thanks. I figured it out though. I had to switch the SATA operation from RAID Auto/AHCI to RAID Auto/ATA.

I am dual booting windows XP/Ubuntu 10.04 right now because Internet on Windows XP isnt working. 

Now i have to install all of the drivers for windows. 

This is just one pain in the *** after another. But it will be worth it in the end.

---

### Post by Mark Phelps on 2010-09-30
> **skumnull said:**
> How do I create a NTFS partition?

Was going to respond but see you already have it installed.

Glad to see you got through that.

---

