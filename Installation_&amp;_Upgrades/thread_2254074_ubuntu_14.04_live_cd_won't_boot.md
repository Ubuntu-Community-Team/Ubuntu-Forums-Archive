---
title: "ubuntu 14.04 live cd won't boot"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by Edward_Nigma on 2014-11-24
Hello everyone, I recently installed window 10 technical preview, but decided I don't like it. I just burned an ubuntu disk, but whenever I try to load it in the disk tray, nothing comes up, why won't it boot?

---

### Post by yancek on 2014-11-24
You should have a method of setting boot priority in the BIOS when you boot.  Usually, at the bottom of the screen there will be a message telling you which key to tap to enter 'setup' and from there usually a boot tab and an option to set the DVD drive to first boot priority.  Are you using a DVD or a flash drive?  If a flash drive, you should see the name of the drive under the hard drive options and set it before the actual internal drive.  More info on exactly what you did would help.  What was on the computer for an operating system before you decided to test windows 10?

---

### Post by Edward_Nigma on 2014-11-25
Ok, so I tried setup, but I didn't find boot priority in the BIOS anywhere. I have a Dell Inspiron 17R, and I was running Ubuntu 14.04 before I installed Windows 10. Is that helpful?

---

### Post by flaymond on 2014-11-25
just think BIOS as a bootloader or 'Operating System manager'. It will give you choice to boot with what kind of OS? and where you will boot it from...


so.


for Dell click F2 after when BIOS menu appear....(mine F12 for Acer)...then choose your boot options (following where the location of the burned image). If you using CD to boot...click 'arrow down' until you find DVD/CD Optiarc or similar like that. If you use USB, then maybe it will be on the last place....or arrow down until your find your USB name (HDD or something similar)


* I don't think my post is what you looking for, sorry :(

---

### Post by jhay2 on 2014-11-25
there is plop bootmngr for windows i dont know if it will work on windows 10 tech preview but it might work .  just install plop bootmgr and then you can boot your usb without touching your bios :)

---

### Post by flaymond on 2014-11-25
Another reason it failed to show up because the cd is damaged or old. Maybe you can check in the cd. And sew if it contain extracted files of iso image....or if it wont work..try reburn your cd with slowest speed you can

---

### Post by yancek on 2014-11-25
> Ok, so I tried setup, but I didn't find boot priority in the BIOS  anywhere. I have a Dell Inspiron 17R, and I was running Ubuntu 14.04  before I installed Windows 10. Is that helpful? 				

Most Dells use the F2 key to get to the BIOS.  You will have to look for a Boot tab or just explore the various options as the menus in the BIOS change all the time.  It doesn't matter what you had on it before.  If you haven't resolved this, you might post some info on your computer hardware and whether you were using UEFI or not previously.

The windows 10 is a test version and I know this doesn't help in your situation but, you would have been better off installing it in VirtualBox or some other virtual machine which would have avoided this problem.  Installing test systems on your primary computer often leads to problems like this.

---

### Post by flaymond on 2014-11-26
I believe, you need to use UEFI method (It worked on majorities Windows 8 and plus user)...

---

