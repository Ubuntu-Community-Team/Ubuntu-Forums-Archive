---
title: "cant activate nvidia driver"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by SurferGTO on 2009-11-15
After updating to 9.10 (regreeetttttt) i cant activate my nvidia driver in syste>admin>hardware drivers. it tells me installation failed, and tells me to look at jockey.log but i have no idea what im looking at in there or what any of that means.

---

### Post by SurferGTO on 2009-11-16
bump, ive searched and so far as far as ive found no workarounds are helping... anyone have any suggestions? even a redirect i could care less, but i cant find anything that is helping me activate my graphics card.

---

### Post by darkod on 2009-11-16
Have you tried EnvyNG package? Really good package for handling video drivers, both ATI and Nvidia. Might help. Helped me for my HD3200.

---

### Post by SurferGTO on 2009-11-16
yes i tried EnvyNG but i cant seem to get the prog to run. it shows that its installed, and perhaps im not using it correctly, but i click the appl in system tools folder, and it asks for a password for admin priv... then the dialog box dissapears and nothing seems to happen...

---

### Post by darkod on 2009-11-16
it can be run in text mode with
envyng -t

Try it in terminal. Don't know if you need sudo, you might as well try.

PS. Just in case it didn't install correctly in terminal it can be installed with
sudo apt-get install envyng-core envyng-qt

---

### Post by SurferGTO on 2009-11-16
it loads in terminal, and i can uninstall the nvidia driver, but upon attempting to install the following error message occurs: 

> Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 322, in driverMenu
    self.driverPage(driver)
  File "interface.py", line 216, in driverPage
    candidateLen.append(len(details['candidate']))
TypeError: object of type 'NoneType' has no len()


and it returns to the terminal prompt

---

### Post by darkod on 2009-11-16
Sorry, no idea. It worked for me even without deinstalling the older driver.

---

### Post by SurferGTO on 2009-11-16
after uninstalling (successfully) the ATI driver, and attempting to install that. i get this message:

> 
 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+



i know some people were having issues with their kernel, either not updating or what have you but as far as i could tell mine was up to date.. whats the code to check the kernel again? ill post that output as well...

---

### Post by SurferGTO on 2009-11-16
2.6.27-14-generic

---

### Post by darkod on 2009-11-16
You said you upgraded to 9.10, shouldn't that be kernel 2.6.31? Maybe that's your problem?
Sorry but personally I don't know the answer, that's why only a question/idea. :)

---

### Post by SurferGTO on 2009-11-16
i think youre right, im reading somwhere now that its at least linux kernel 2.6.30.... i have linux kernel package thingie installed (i forget the whole name, as i just did it tho i know it was done) and im pretty sure ive done everything needed to update the kernal, as i originally thought this may have been the problem, but it looksl ike it hasnt updated?

---

### Post by SurferGTO on 2009-11-16
from the 9.10 release notes:

> However, if you choose to "keep the local version currently installed," your system will not be set up to boot from any newly-installed kernels. Manual action is required on your part to ensure that your system is running the current, security-supported kernel after upgrade. If you have local changes to your bootloader config that you want to keep, it is recommended that you follow these steps:   

    * Choose "keep the local version currently installed" at the prompt.  
    *

      Open /boot/grub/menu.lst with a text editor (e.g., sudo gedit /boot/grub/menu.lst).  
    *

      Apply any changes you've made to the kernel boot options to the commented variables (e.g., groot, kopt, defoptions) above.   
    *

      Move any manually-added boot options for other operating systems so that they are above the line   

      ### BEGIN AUTOMAGIC KERNELS LIST

      or below the line   

      ### END DEBIAN AUTOMAGIC KERNELS LIST

       
    *

      Save the file, and run sudo update-grub from the commandline.  
    * Choose "install the package maintainer's version".   


since i opted to keep the local version currently installed, im assuming that is why it did not update the kernel to the newest version. now with all the tinkering and coding and everything ive done in the past to make ubuntu work on this machine, im sure i did edit some lines in the menu.lst, however exactly what ive added/edited i have no freakin clue. so i understand what this is telling me to do, above, but i dont know what exactly i have to move around, can anyone offer some help?

---

### Post by SurferGTO on 2009-11-16
in attempting *sudo update-grub* as mentioned above im not given an option to install package maintainers version. this is the output:

> sudo update-grub
sudo: unable to resolve host master-laptop
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-20-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin


---

### Post by SurferGTO on 2009-11-16
output of uname -a:

> laptop:~$ uname -a
Linux master-laptop 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux


---

### Post by SurferGTO on 2009-11-16
so it looks like i have the current kernel installed (2.6.31-15-generic) but that grub is loading an older version (2.6.27-14-generic)

---

### Post by SurferGTO on 2009-11-16
however the GRUB kernel list doesnt show the current kernel to boot off of.. my head hurts...

---

### Post by SurferGTO on 2009-11-16
so does anyone know how to activate/upgrade/install/use/fix to the newest kernel? im assuming thats where most of my problems are coming from (audio/graphics card)

---

### Post by SurferGTO on 2009-11-16
one would think reinstalling or upgrading the kernel would not be a difficult task... am i completely missing something??? come on gurus

---

### Post by SurferGTO on 2009-11-17
SOLVED:

as mentioned before it was because i opted to use the current version of menu.lst during the install process rather than go with the new one. this made grub boot off the older kernel which apparently caused problems with both my graphics card and sound card. 

this was fixed in another post, for the sound problem, by user magnesium:

[http://ubuntuforums.org/showthread.php?p=8201048#post8201048]("http://ubuntuforums.org/showthread.php?p=8201048#post8201048")

after following instructions for the appropriate build, i rebooted, than was finally able to activate the drivers through system>admin>hardware Drivers

---

