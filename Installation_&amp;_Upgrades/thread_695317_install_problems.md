---
title: "install problems"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by lpaulstudio on 2008-02-12
I very recently took apart my computer and  upgraded one of the hard drives to 160 gb. I had xp on it but wanted ubuntu instead. Somehow I completely lost windows xp that was on the other drive. No worries though cause I'm getting ubuntu anyway. But I can't seem to get ubuntu to work. It tells me to enter the sstem disk and press enter. I do so and it repeats the message. ??? Am I supposed to install ubuntu from window or can it boot by itself. I'm new to this and am really confused.

---

### Post by Partyboi2 on 2008-02-12
ubuntu boots by itself, Once you have burn't the iso to a disk as a iso at x4 or less and made sure the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") matches, you would set the bios to boot from cd first. Then you will be presented with a ubuntu main menu screen where you have a few options.

Edit: check that your hard drive is being detected in bios correctly

---

### Post by lpaulstudio on 2008-02-12
ok. How do I set it to boot from cd? I know how to get to the BIOS or whatever it is called. You can set like supervisor password and check if your hard drives are being recognized, etc. Where should I go to make it boot from cd? I am REALLY new to this; sorry if I am like annoying or anything.

---

### Post by Partyboi2 on 2008-02-12
> **lpaulstudio said:**
> ok. How do I set it to boot from cd? I know how to get to the BIOS or whatever it is called. You can set like supervisor password and check if your hard drives are being recognized, etc. Where should I go to make it boot from cd? I am REALLY new to this; sorry if I am like annoying or anything.
If you were annoying I would turn my pc off :lolflag:
You should see something like Advanced setup or Advance Bios Features etc. (All depends on what type of motherboard you have) Go into that and change the order so that cd is first floppy 2nd and hard drive is 3rd. then save and exit

---

### Post by lpaulstudio on 2008-02-12
Ok. I got it to boot from cd by changing the boot sequence to cdROM first. Anyway, it says: "booting from CDROM ..." and then prints: "Failure" What went wrong. I downloaded the Ubuntu installer onto a CD, was that the ight way to do it? Do I have to request one for it to work?

---

### Post by abyssius on 2008-02-12
An exact answer to your question depends on the particular BIOS your motherboard utilizes. What you have to do is scroll through your BIOS menus until you find a menu item  like [ Boot Priority]. With some BIOS types, you'll see [BOOT] as its own menu. When you find the menu item you will be able to select from a list of boot devices, like 1st Hard Disk, Floppy, CD-ROM, etc. Obviously, you want to select CD-ROM. Usually you select the first boot device by placing it at the top of the list. The BIOS help function will aid you in exactly how to accomplish this.  When you're sure you've assigned the CD-ROM as the first boot device, then exit and save the BIOS settings. WARNING: Don't change anything you don't understand. And, don't set a Supervisor Password.

---

### Post by lpaulstudio on 2008-02-12
Ok so I changed the boot sequence but it says Failure when it tries to boot. Was this cause I have supervisor password? I have NO clue why it is'nt working. :confused:

---

### Post by abyssius on 2008-02-12
Did you burn a disc image to the cd or copy the file you downloaded to the cd?

---

### Post by Partyboi2 on 2008-02-12
did the md5sum match up? If unsure how to, check my first post.

---

### Post by lpaulstudio on 2008-02-13
I just pressed the download button with the default setting and saved it to the cd. What's this image thing about? And no I didn't check the md5sum thing yet.

---

### Post by Partyboi2 on 2008-02-13
[Here]("https://help.ubuntu.com/community/BurningIsoHowto") is how to burn. In short you need to check the md5sum to make sure it matches. If they match, then you would burn the image to a disk as a iso not data at about x4 or less. See the link I have provided for more info on how to.

---

### Post by lpaulstudio on 2008-02-13
Oh, I didn't know you had to download software and save it as image. That helps a lot. thanks.

---

### Post by lpaulstudio on 2008-02-14
well the CD didn't load right but I think it got messed up in instalation process. I gonna try and reinstall it on new disk and check the md5sum thing. About that, do you check after you download it to your computer or after you get it onto disk. Or does it even matter? I such a nube!:lolflag:

---

### Post by lpaulstudio on 2008-02-14
so i burned the image to the disk. Is it normal that it will say it's empty when I look at it in my computer? I open it and there are no files inside.

---

### Post by Partyboi2 on 2008-02-14
You check the md5sum after you have downloaded it and before you burn to disk. Try using something like [imgburn]("http://www.imgburn.com/") at x4 or less speed to burn the iso to disk

---

### Post by lpaulstudio on 2008-02-15
K. Yeah I was using InfraExpress at x8 cause that's the slowest it goes. I checked the md5sum and it kept saying that they were different even after I reinstalled the ubuntu installer multiple times. I'll try the program you recommended.

---

### Post by Partyboi2 on 2008-02-15
if the md5sum does not match then you will need to download a new image of ubuntu and make sure the md5sum matches before burning to disk. If you used a torrent program to download the ubuntu image all you need to do is click on your current iso and use the torrent program to download the missing bits.

---

