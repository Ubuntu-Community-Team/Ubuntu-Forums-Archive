---
title: "Installation Problem"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by Rohan Mallya on 2011-03-24
Hello,

I am new to the Linux Line and i wanted some help. I currently have a Windows XP OS which i want to dual-boot with Ubuntu Linux 10.10 . I put the disk in the drive and chose the option to install Linux through Windows. But it hangs in the middle. I am also unable to change my BIOS settings due to which i can"t change my boot preference. My first Boot is the HDD. I want to change it to CD-ROM. Any suggestion? I also have another PC where i can boot through the CD...I tried installing there by booting from the CD but i get this error message after seeing the purple Linux screen with the loading dots.

"(Process:286):Glib warning**:getpwuid:failed due to unknown user id (0)

P.S.- I am not able to see any options while the boot is going on
And please answer to both my questions!

Regards,
Rohan Mallya

---

### Post by Sef on 2011-03-25
1) Did you md5sum the iso?

2) Try reburning the iso, and set the burn to the slowest rate you can.

---

### Post by mathewprince on 2011-03-25
Before you can boot from Boot Live CD you need to change the first Booting device to CD ROM . Get hold of some software which cracks BIOS password. The software to be used will depend on the manufacturer of your PC. Kindly let us know your system configuration. 
For the second try what sef has mentioned.

---

### Post by mörgæs on 2011-03-25
The Glib-problem is described here
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
and post 176 has a solution.

---

### Post by mörgæs on 2011-03-25
And by the way: If you doubt that the CD is burned correctly, there is a self-test in the system. 

During boot you will see the keyboard-man symbol, which means 'push any key'. This gives you a menu, where you can choose 'test CD for defects'.

---

### Post by Rohan Mallya on 2011-03-25
@[COLOR=Blue]sef[/COLOR] the md5sum are the same.

@[COLOR=Blue]mathewprince[/COLOR] My system spec. is as follows:

500 GB HDD
1 gb Nvidia 9400 Gt graphic card
2 GB system RAM
Intel DG31PR motherboard set

@[mörgæs]("http://ubuntuforums.org/member.php?u=939075") I cannot see any of the options as i mentioned before...The loading screen comes and i get this error message after about 10 minutes

And guys, I know my BIOS password but i am not able to change the setting when i enter the BIOS!!

---

