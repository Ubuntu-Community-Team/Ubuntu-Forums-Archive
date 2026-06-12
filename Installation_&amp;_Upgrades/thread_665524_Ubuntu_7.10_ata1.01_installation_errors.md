---
title: "Ubuntu 7.10 ata1.01 installation errors"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Iteo on 2008-01-12
I have installed various versions of ubuntu over the past few years on my dell optiplex gx240, and multiple times i have had problems during installation. I am wondering if my hardware is incompatible. And when i finally got the old installations to work, it could take up to 5 minutes to start when windows(dual boot) starts in one minute. I believe that this problem is likely due to a bad hard drive because when i show the startup process it always hangs at the hard drive even on booted linux cds like Gparted. I'm currently trying to install 7.10, but the main splash screen(after clicking install) cycles for a couple minutes and goes to never ending errors like:

Ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
buffer i/o error on device sdb, logical block 0
ata1.01: exception emask 0x0 sact 0x0 serr 0x0 action 0x2 frozen

I would appreciate any help with the installation as well as the hard drive/startup problem.
Thank you. 
](*,)

(No I am not a novice so don't say it...please)

---

### Post by Iteo on 2008-01-15
Come on I need some help here please. :confused:

---

### Post by Sef on 2008-01-15
Does the Live CD run ok? (If you run it for a few hours.)

---

### Post by Squizz on 2008-01-16
I'm getting a similar problem at the moment - [this thread]("http://ubuntuforums.org/archive/index.php/t-276930.html") advises you to press f6 at the boot menu and change "quiet splash" to "splash irqpoll" - it's not a Gutsy thread, but I tried it and had more luck than last time however it's gone back to being a logical block again now.

I can't run the live CD either - so will let you know if I find a solution.

---

### Post by Iteo on 2008-01-17
Well, its time for an update. Splash irqpoll does not change anything, and i have tried stuff like noapic nolapic noacpi and acpi=ht. FYI it lingers at the splash screen at /scripts/casper-premount before going to the errors. There are various other errors like ones including [sdb]. I can eventually get ubuntu 6.06, but i would like to eventually have this solidly solved. Also, the 7.10 cd works on my other computer. SO i assume the cd is ok. Im wondering though if my cd/dvd drives are the problem. If you have any other suggestions on what to try, i would appreciate any help.:KS

---

### Post by Iteo on 2008-01-19
Another Update! Well i finally got the ubunntu installation to begin using the alternate cd, but now it starts to freeze mid installation around the cd drive checks, and i can only get it to continue by pressing keys, opening/closing drives, etc. Would noapic nolapic or acpi=off help here? or would something else work? Thank you for any help.

---

### Post by Iteo on 2008-01-19
Well i have more infor about the installer. When it tries to detect the cd drives it asks for drivers. (im guessing this is also why it takes a long time to detect devices) I can trick the system into continuing, but when i get to the partitioning, it fails to find the second hard drive while the bios and windows detect it fine. where should i find the drivers for the cd rom drives, and what can i do about it not detecting the second drive.

---

