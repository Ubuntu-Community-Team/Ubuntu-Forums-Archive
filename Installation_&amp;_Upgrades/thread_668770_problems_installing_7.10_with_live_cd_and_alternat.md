---
title: "problems installing 7.10 with live cd and alternate"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by chreezchinfolife on 2008-01-15
I have been trying to install feisty fawn on my computer in a dual boot config for more than a week and have not had any luck with either the live cd or the alternate text based cd.  The live cd will boot into the menu and then after clicking install the screen goes blank and i have to restart my computer which i suspect has to do with my graphics card not being supported.  So i try the alternate cd which sometimes works until i try and install the base system and i encounter corrupt files.  Otherwise, the cd will fail to boot and i have to try and download another.  I have a core 2 duo processor which supports 64 bit processing so i have tried both the 64 bit version and the x86 version but neither works.  Another problem is that i have been unable to download the ubuntu alternate download off the ubuntu website and every time i click the check box for the alternate it just gives me the normal download.  My system includes a intel core 2 duo and a 8800 gts; i am already running xp and vista but i would like to add linux to the mess.  


thanks, 
martin

---

### Post by wolfen69 on 2008-01-15
here [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/) is a link for the alternate cd (towards the bottom of the page)

---

### Post by chreezchinfolife on 2008-01-15
the problem i have had with that is that it says the cd is corrupt during the installation of the base files.

---

### Post by Sef on 2008-01-15
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Checks for a good download.)

2) Did you burn the iso at 4x or less? (Faster can corrupt the burn.)

3) Check the disk, upon boot go down the list to 'Check Disk for Errors' instead of start/install.

---

### Post by chreezchinfolife on 2008-01-15
Which version should I be installing because i have a core 2 duo processor which is 64 bit compatible but is that the right version to get?

---

### Post by chreezchinfolife on 2008-01-26
So i got it installed via the alternate download but now i have another problem and it might be something obvious im missing.  When i start ubuntu the screen is still blank and i know that i need to install the graphics drivers for my 8800 gts but i dont know the method.  So i would really appreciate it if somebody could relay that to me.

---

### Post by Partyboi2 on 2008-01-26
Try getting to a terminal Ctrl+Alt+F1-F6
Login to the terminal
then install this package (this will work if you have a working internet connection)
```
 sudo apt-get install build-essential 
``````
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run
```Install the driver
```
sudo sh NVIDIA-Linux-x86-169.07.pkg1.run
```follow the installer instructions then when finished start x
```
startx
```

---

### Post by chreezchinfolife on 2008-01-26
Can I do this from the command line in GRUB?  If not, then where would I press the keys for the terminal?

---

### Post by Partyboi2 on 2008-01-26
If you are getting the black screen as soon as you have selected what kernel to boot into, I would suggest trying some boot options. From my understanding its later on in the boot process that  the xserver loads and your graphics driver gets loaded. The other day I ran into the same problem while installing and adding noapic to the boot options solved the problem. To try, when you are at grub menu select the kernel you are going to boot and press "e" then select the line that starts with "kernel" and press "e" again then at the end of the line add ```
noapic
``` then press enter and "b" to boot. If this works you will need to add to grub menu.list this boot option.

But to enter a terminal you would try that after you have selected what kernel you are booting into

---

### Post by chreezchinfolife on 2008-01-26
No it didn't work the screen still goes blank.

---

### Post by Partyboi2 on 2008-01-26
change the boot options again and this time remove the word > quiet and change > splash to ```
nosplash.
``` then see where it is stopping.

---

