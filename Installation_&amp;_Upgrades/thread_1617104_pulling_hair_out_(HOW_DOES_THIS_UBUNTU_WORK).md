---
title: "pulling hair out (HOW DOES THIS UBUNTU WORK)"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by bellamia on 2010-11-09
:confused::confused::confused::confused:
 
I have downloaded from the home page and i have made a cd and usb copy and neither will open or extract or anything. I am used to windows windows and windows. I want to be free of the bs of windows and thought linux would be a good alternative. But if just posting a post is any indication of the problems i am to face.......give me hope in a simpler system
How do i install ubuntu and what else do i need to run ubuntu programs like ms office. Would love to install this and learn more. Anyone out there wishing to point me in the right direction i would appreciate it.

---

### Post by jocko on 2010-11-09
You'll probably find what you need here:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

But basically what you need to do is:

1a) Burn a cd from the iso. Don't just copy the file to a cd. An iso is an image of an entire cdrom filesystem, so it should be burned with the "burn image" option.
1b) Use [UNetbootin]("http://unetbootin.sourceforge.net/") to create a bootable usb from the iso. Again; it's not enough to just copy the iso to the usb, it needs to be unpacked and installed properly to the usb. UNetbootin will do this for you.

2. Insert the cd (or usb stick) and reboot your computer. If it does not automatically boot from the cd/usb, reboot again and enter the bios setup. You need to press a specific key during the first seconds after the computer powers on. Which key you need to press is different between different motherboards, but Del or F2 are very common. Usually there will be a message on the screen about which key to press. Otherwise you'll need to find your motherboards manual.

3. Once you are in the bios setup you need to find a setting for which order the computer should look for bootable disks. You need to set the cd (or usb drive) before the hard drive in the list. Save the changes and reboot again. Now your computer should start from the cd or usb.

4. The rest should be almost self-explanatory, but follow the instructions on my link above if it helps (but it may not be completely up-to-date so some steps may be slightly different).

---

### Post by Quackers on 2010-11-09
Welcome to UF.
So, you have downloaded an .iso file which is the Ubuntu system and its installer. This .iso file must be burned to a disc (or usb stick possibly) but it must be burned as an image. If you just burn it to disc normally it won't work. There are free programs for Windows that can do this (eg ImgBurn).
Before you actually burn the image it is a good idea to check the MD5SUM of the downloaded image file, to make sure the download is not corrupted. See here

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

When you have checked the MD%SUM and burned the image to disc you can then insert the disc, shutdown your computer then boot from the Ubuntu Live CD.

There is a choice on the Live cd to "try Ubuntu" rather than install it. You can use this to make sure that all your hardware will work beforehand.

If there is anything you are not sure about just ask. It's better to ask how to do something than ask how to fix it after you've done something :-)

---

