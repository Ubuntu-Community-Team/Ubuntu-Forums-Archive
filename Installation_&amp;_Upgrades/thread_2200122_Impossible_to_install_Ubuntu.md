---
title: "Impossible to install Ubuntu"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by carlo.zoc7 on 2014-01-17
Good evening to everyone;
I have a problem with my pc, I can't turn out to install Ubuntu 13.10 64bit or other releases (I have tried with some minimal releases but I haven't had any results). When I choose "Try ubuntu" or "install ubuntu" the desktop becomes like in the photo. How can I solve this problem? I have already asked on ubuntu italian forum but they haven't been able to help me. Thanks.
This is my computer's hardware
[TABLE="width: 100%"]
[TR]
[TD="align: left"]VGA Asus nVidia GeForce GTX 660 DC2O-2GD5[/TD]
[TD="align: center"][/TD]
[TD="align: right"][/TD]
[/TR]
[TR]
[TD="align: left"]RAM DDR3 G.Skill Ripjaws-X F3-1600C9D-16GXM 1600MHz 16GB (2x8GB)[/TD]
[TD="align: center"][/TD]
[TD="align: right"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: center"][/TD]
[TD="align: right"][/TD]
[/TR]
[TR]
[TD]CPU Intel Core i5-4570 3.2GHz Socket 1150 84W with GPU HD Graphics 4600 Boxed[/TD]
[TD="align: center"][/TD]
[TD="align: right"][/TD]
[/TR]
[TR]
[TD="align: left"]AsRock Fatal1ty Z87 Professional Socket 1150 Intel Z87
[/TD]
[/TR]
[/TABLE]

---

### Post by Bucky Ball on 2014-01-17
Welcome. I have removed the large image from the body of your post. Spare a thought for those with slow connections and/or vision issues (who may be able to help but won't access the page). ;)

What happens when you either press 'Try Ubuntu' to try Ubuntu, or 'Install Ubuntu' to install it from the screen in the pic? You are installing from a USB dongle?

---

### Post by carlo.zoc7 on 2014-01-17
When I choose one of the two choices, the screen be moved on the right and pink line appears on the left. After some seconds the computer is down and I can't do anything, I have to only shut down by button.
Thank you for your operation on the photo :).
I have tried by USB and CDS. 
Thank you!

---

### Post by carlo.zoc7 on 2014-01-19
bump

---

### Post by Bucky Ball on 2014-01-19
When you get to the normal sized screen before the little blue screen that is in the picture, hit F6. Do you get a pop up menu? If so, choose 'nomodeset'. Proceed. Any different?

---

### Post by carlo.zoc7 on 2014-01-19
While I were writing the code, it was down.

---

### Post by Bashing-om on 2014-01-19
carlo.zoc7; Hi !

Did you do this ?
From a cold boot:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
For now we are interested in the results of "nomodeset" .
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
If you reach this point, then: ->
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

Whatever action is required to boot the LiveMedium must be replicated in the actual install.

So, tell us exactly what procedure you are doing, and what is happening at each step.

Additional help is pending as your needs are realized.

[INDENT][INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by carlo.zoc7 on 2014-01-19
When I put the Boot from the CD, after the purple screen, I have this result (like the photo).
[IMG][[IMG]http://s13.postimg.org/l3cx7uhb7/IMG_20140119_191948.jpg[/IMG]]("http://postimg.org/image/l3cx7uhb7/")[/IMG]

---

### Post by Bashing-om on 2014-01-19
carlo.zoc7; Welp,

Try again, there is a very small window of opportunity for the system to recognize that a key has been hit in some systems.
As soon as your bios screen clears, try repeatedly hitting the left shift key, We must get to the boot options screen to affect the boot parameters.
language screen-> escape to accept the default -> boot option screen -> f6 key .

[INDENT][INDENT]there ain't no getting around it
[/INDENT][/INDENT]

---

### Post by carlo.zoc7 on 2014-01-19
The problem is I don't have the purple screen with the menu. The only purple screen that shows is the first, where we can find the icon down. After the purple screen appears the screen in the photo.
Thank you for your availability:)

---

### Post by Bashing-om on 2014-01-19
carlo.zoc7; YUK !

"CPU Intel Core i5-4570 3.2GHz" : Does that equal windows 8 with UEFI on the mother board ?
Yes ? Going to have to jump through some hoops to get an alternate operating system recognized !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by carlo.zoc7 on 2014-01-20
Sorry but I don't understand what you mean. I don't have windows 8, I have install windows 7 64bit and I don't have hardware problems.

---

### Post by oldfred on 2014-01-20
Did you install Windows 7 in BIOS or UEFI mode. 
Windows DVD only installs in BIOS mode, but you can convert it to UEFI mode on a flash drive.

Your motherboard is UEFI with a BIOS compatibility mode. You want to install Ubuntu in the same boot mode as you installed Windows for ease of dual booting.

This shows boot screens so you know which boot mode you are in.
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Does your system boot with Intel video or the nVidia card? If nVidia you need nomodeset on grub menu if UEFI or press any key and f6 to add nomodeset to installer. After install you have to edit grub menu to add nomodeset.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by carlo.zoc7 on 2014-01-20
Windows it isn't installed in BIOS or UEFI (for now). I try with the guide in your links but I have been having the same result. I can't access in the nomodeset or anymode of ubuntu because the system is down after the purple screen. The system boots with nVidia card.
If I installed Windows in UEFI mode,  would ubuntu start?

---

### Post by oldfred on 2014-01-20
Installing Windows in one mode or the other does not matter. Each is separate. It just is when dual booting you can use grub if both are in same boot mode.

You should be getting the accessibility screen with two tiny icons - person & keyboard which means to hit any key if booting in BIOS mode. Then use f6.
If in UEFI mode you should have grub menu. 
Normally purple screen is when you start to boot after accessibility screen or grub menu.

---

