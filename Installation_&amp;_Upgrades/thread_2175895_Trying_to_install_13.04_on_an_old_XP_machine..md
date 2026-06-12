---
title: "Trying to install 13.04 on an old XP machine."
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by Information_Missing on 2013-09-21
I downloaded the file ubuntu-13.04-desktop-i386.iso from ubuntu.com and burned the image to a DVD. I have checked the MD5SUM of the iso against ubuntuhashes and everything looks fine. I put this dvd into an older Compaq that was lying around gathering dust. The first time it loaded, there were a few hangups, and before it got to the main screen I got error number 5, an I/O error. I restarted the system and tried again. everything went well, I got through the install screens and installation started before the same error occurred. I tried to "try ubuntu" and things went well for the most part. errors would occur on a regular basis, and error reports were sent. The graphic were running extremely slowly. Since windows had been destroyed by the earlier install, I tried to use ubuntu from the cd to run a HDD check. This attempt failed. 

I read that some newer machines will burn a DVD too quickly, since I made the DVD on a newer machine, I tried again. I burned the image at the slowest speed possible using infra recorder. I also heard that some people were having problems with 13.04, so I also made a install DVD of 12.04.3 LTS. 

At this point, no matter which install media I try to use, the following occurs:
The bios screens run their course.
The screen is black with a flashing cursor in the upper left corner. (stays indefinitely)
If the disc is ejected a complaint is printed instructing me to put boot media in the drive and press enter. If I do, the same black screen happens.

---

### Post by sudodus on 2013-09-21
Welcome to the Ubuntu Forums :-)

1. Please specify the computer: Brand name is Compaq, but let us know also the model, and if possible the CPU, RAM size (but it might be hard until you have something working) and graphics card. This information makes it possible to give relevant information.

2. You should probably use a flavour of Ubuntu with a lighter desktop environment, Lubuntu or Xubuntu instead of standard Ubuntu, that is made for fairly new computers with a lot of horsepower (CPU) and memory (RAM). See also this link for details: [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by Information_Missing on 2013-09-21
Sorry about the missing info. 

Compaq Presario sr1215cl
AMD sempron, unknown speed.
512Mb SDRAM
Geoforce FX 5200

---

### Post by santosh83 on 2013-09-21
> **Information_Missing said:**
> Sorry about the missing info. 

Compaq Presario sr1215cl
AMD sempron, unknown speed.
512Mb SDRAM
Geoforce FX 5200

Oops this would be a bit too short on RAM for standard Ubuntu. I think you should give Lubuntu a try, maybe even the alternate installer rather than the standard graphical one.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

---

### Post by Information_Missing on 2013-09-21
Thanks for the advice. Lubuntu installed much easier. I thought that i had reviewed the ubuntu system requirements, but apparently not closely enough.

---

