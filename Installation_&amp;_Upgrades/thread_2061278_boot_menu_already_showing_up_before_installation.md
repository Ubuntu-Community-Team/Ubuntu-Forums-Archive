---
title: "boot menu already showing up before installation"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by adamasuka on 2012-09-22
I am very new and this is my very first time installing ubuntu. I am aiming to dual boot ubuntu with windows 7. I haven't started installing ubuntu yet, But I will start as soon as i get my ethernet cable to use it during the installation for updates and drivers (i am currently using wifi on my laptop). 

So here's what happened: 

-i burned it to disk
-after burning i restarted to see if working
-it didn't boot to live cd so i clicked on the third option "help me to boot from cd"
-i installed the boot cd helper
-booting from ubuntu now worked
-the boot menu shows everytime when restarting computer even without the live cd


My question is how do i get rid of this ? it says in the tutorial that it wouldn't go to boot menu after installation , shouldn't it still need a software to configure the boot settings (Like EasyBCD)? I haven't started installing ubuntu yet but it already shows the boot menu after rebooting without a cd, is this a feature from the "help me to boot from cd" option?

i am following this tutorial 
[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/)

---

### Post by darkod on 2012-09-22
I am not sure what the "help me to boot from cd" option is, but I guess it installed some sort of small bootloader to do that when you used it. I also guess it says it won't be there after install because the grub2 bootloader will be installed and it will overwrite it.

EasyBCD is used for something else, that's for managing windows bootloader. Now, if this "help me" option only added some entry in the windows bootloader, you might be able to remove it using EasyBCD. But if you plan to install ubuntu soon, you might as well not touch anything and simply install uubntu which will set up grub2 on the MBR.

Also, why did you need to use this option? To boot from the cd you either have to use a key to enter the Boot Menu during your computer boot, or enter into BIOS and set the cd-rom to be first boot device, before the hdd.

That way it will boot from cd whenever there is a bootable cd inside.

Using the "help me" is not really necessary, it just caused it to make an entry that is now confusing you.

---

### Post by adamasuka on 2012-09-22
this is the option btw:
[http://imageshack.us/photo/my-images/801/ubuntucd.png/#](http://imageshack.us/photo/my-images/801/ubuntucd.png/#)
At first i thought that only restarting with ubuntu cd inserted will automatically detect the installation during startup (which didn't ) so i presumed it didnt work. After further researching, It was now that realize It was a huge mistake of me of not using the bios key to configure to boot from cd option.

So i'll take your advice and just go on with the installation.

 thanks for clarifying.

---

