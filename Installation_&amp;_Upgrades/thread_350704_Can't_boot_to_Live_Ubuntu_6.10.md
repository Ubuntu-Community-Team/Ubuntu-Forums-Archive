---
title: "Can't boot to Live Ubuntu 6.10"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by linuxmaveric on 2007-01-31
I recently put together a PC. Here are the specs:

1. 300GB PATA Samsung Hard-drive
2. ATA 133 Motherboard
3. 512mg RAM-DDR
4. LG-CDRW
5. WinXP loaded in the hard-drive.

Here's the problem.

I want to install Ubuntu 6.10 and get rid of XP once and for all. However, when I boot up the computer with the live-disc nothing happens. I have 3 copies of live Ubuntu from 3 different linux magazines. It did not make a difference.  I even tried to load federoa 6.0 just to see if my computer would boot to fedora. Nothing happend?  It just boots to XP like nothings in the CDRW.  

I went into bios and made my CDRW the primary boot option, and it still just booted to XP. 

Is this happening because my LG-CDRW does not read the Ubuntu disc? Or does the LG-CDRW not able to read linux althogether.  Should I get a new CDRW or DVD-RW to fix this problem? 

Or is there a driver update out there that anyone knows about? 
I hope someone can help me as I can't wait to install Ubuntu and get rid of my XP.
Thanks.

RR.

---

### Post by meng on 2007-01-31
Is your CD drive working otherwise? For example, can it read a disc from Windows?

---

### Post by linuxmaveric on 2007-01-31
Thanks for the quick reply.

Yes, my CDRW reads my XP disc in a flash with no problem, but not Ubuntu?? Not sure why :(

---

### Post by meng on 2007-01-31
Well it's not because your CD drive "can't read Linux". The CD is just an ISO9660 filesystem that happens to enable the running and/or installation of a Linux system. I can't put my finger on the problem, but I'm not 100% sure that getting another drive is the answer. It would be a different story if the CD started to boot and then stopped, complaining that it was unable to recognize the drive, but that's not what you are reporting.

---

### Post by Sef on 2007-01-31
> I have 3 copies of live Ubuntu from 3 different linux magazines. It did not make a difference. I even tried to load federoa 6.0....

Have you or can you check and see if they boot up on another computer.

---

### Post by linuxmaveric on 2007-02-01
The 3 discs bootup just fine in my laptop computer which is also running XP. However, no permission to install in the laptop.  My wife uses it for work. \

So I guess I cant install for now on my system. Thanks for your help. 
Ubuntu newbie foiled!!

:(

---

### Post by dcstar on 2007-02-01
> **linuxmaveric said:**
> I recently put together a PC. Here are the specs:

1. 300GB PATA Samsung Hard-drive
2. ATA 133 Motherboard
3. 512mg RAM-DDR
4. LG-CDRW
5. WinXP loaded in the hard-drive.

Here's the problem.

I want to install Ubuntu 6.10 and get rid of XP once and for all. However, when I boot up the computer with the live-disc nothing happens. I have 3 copies of live Ubuntu from 3 different linux magazines. It did not make a difference.  I even tried to load federoa 6.0 just to see if my computer would boot to fedora. Nothing happend?  It just boots to XP like nothings in the CDRW.  

I went into bios and made my CDRW the primary boot option, and it still just booted to XP. 

Is this happening because my LG-CDRW does not read the Ubuntu disc? Or does the LG-CDRW not able to read linux althogether.  Should I get a new CDRW or DVD-RW to fix this problem? 

Or is there a driver update out there that anyone knows about? 
I hope someone can help me as I can't wait to install Ubuntu and get rid of my XP.
Thanks.

RR.

Is the CD a Slave device on an IDE channel with no Master?, if so try and make it the Master device (and check any other settings on it).

---

### Post by JoshHendo on 2007-02-01
> **dcstar said:**
> Is the CD a Slave device on an IDE channel with no Master?, if so try and make it the Master device (and check any other settings on it).
Also, check that you can boot up your Windows XP disk to see if it is the drive or Ubuntu.

---

### Post by jameswilmot2000 on 2007-02-01
sorry ... posted before reading full opening post ... silly me

---

### Post by linuxmaveric on 2007-02-04
I did it!! I finally got my Ubuntu installed.  Thanks for everyones help.  I just finished downloading the updates, and Im off to the internet via Linux Ubuntu.  Wow...the firefox browser is lighting fast.

RR

---

### Post by dcstar on 2007-02-04
> **linuxmaveric said:**
> I did it!! I finally got my Ubuntu installed.  Thanks for everyones help.  I just finished downloading the updates, and Im off to the internet via Linux Ubuntu.  Wow...the firefox browser is lighting fast.

RR

If you think that FF is fast, you should install an optimised version of the Swiftfox browser (for your CPU) then......     :)

---

