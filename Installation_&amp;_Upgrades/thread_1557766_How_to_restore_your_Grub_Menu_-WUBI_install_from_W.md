---
title: "How to restore your Grub Menu -WUBI install from Windows-"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by lagiosman on 2010-08-21
[CENTER][SIZE=4]**THIS SOLUTION IS FOR THOSE HO INSTALL WUBI FROM WINDOWS**[/SIZE] [SIZE=4]**AND DONT HAVE A CD/DVD DRIVE**[/SIZE]
**(BUT SHOULD WORK ALSO FOR OTHER SITUATIONS)**
[/CENTER]
Hello. a few days ago i have install Wubi 10.04 from windows. 
2 days after that i have make a full update and also the grub is updated.
after that i have reboot the system and i can not login at all, i have this stupid message 
[B]Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.  grub rescue


i have search a lot on the internet, i have found 1000000 solutions but nothing its working because i have installing ubuntu before from windows, so the reinstall of grub is not working because grub can not find a linux system on my hd.
SO THIS GUIDE IS NOT WORKING AT ALL [/B]```
http://ubuntuforums.org/showthread.php?t=224351
```

AND HERE IS THE SOLUTION:
(u must have a second pc to do this steps)
(u musta have a usb memmory stick at least 1 gb)

1. DOWNLOAD THE UBCD FROM [HERE]("http://www.ubcd4win.com/downloads.htm")

2. WHEN THE DOWNLOAD IS FINISHED JUST UNRAR THE ISO IMAGE AND PUT ALL THE FILES & FOLDERS IN A FOLDER WITH THE NAME "ubcd502"

3. MOVE THAT FOLDER TO C:\ DRIVE

4. PUT YOUR USB STICK

5. GO TO START/RUN, TYPE CMD AND HIT ENTER.

6. GIVE THE FOLLOWING COMMANDS:
> cd c:\ubcd502\ubcd\tools\win32\ubcd2usb
ubcd2usb c:\ubcd502 x:
where X: is that drive letter of USB memory stick, which is assumed to be already formatted.

7. START YOUR UNBOOTABLE LAPTOP/NOTEBOOK etc WITH THE USB INSERTED. NOW YOU WILL HAVE A MENU, CHOOSE THE "UBCD FreeDOS R1.38"
(u must have your usb devise as first boot devise from bios menu)

8. NOW CHOOSE "Boot UMBPCI (silent)"

9. CHOOSE "Launch->HDD Boot Management->MBRwork"

10. Now choose option 5 (Install standard MBR code) and hit enter

AFTER THE REBOOT & REMOVE USB STICK & SEE WHAT HAPPENS

I HOPE THIS WORK FOR EVERYONE. I HAVE TRYED A LOT OF SOLUTIONS BUT ONLY THIS HAS WORKING FOR ME. CYA

---

### Post by K.Mandla on 2010-08-27
Moved to Installation and Upgrades.

---

