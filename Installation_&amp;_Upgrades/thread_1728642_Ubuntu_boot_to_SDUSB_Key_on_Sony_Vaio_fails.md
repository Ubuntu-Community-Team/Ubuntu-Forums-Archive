---
title: "Ubuntu boot to SD/USB Key on Sony Vaio fails"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by flana on 2011-04-14
Hello, I am trying to install Ubuntu on SD of Sony Vaio - VCPEA36FM. I dont have any luck with booting from either SD or USB Key. Any way around this issue? 

I would think that the windows bootloader that gives you the option to either boot to Win7 or Ubuntu, has SD or usb drivers that it can access should you select ubuntu. 

Should this not work? 

I installed ubuntu from within Windows. No, no hard drive partitions were created. Rather the win7 boot.ini was created that simply points to ubuntu in the SD path, in addition to the win7 in hard drive. 

Any clues?

Oh and so BIOS should not have anything to do with this. BIOS simply loads the windows boot loader. This bootloader then presents an option to either boot to Win7 or Ubuntu (it gets its information from the boot.ini file), and simply should boot to the path selected.

---

### Post by grvsaxena419 on 2011-04-14
> **flana said:**
> Hello, I am trying to install Ubuntu on SD of Sony Vaio - VCPEA36FM. I dont have any luck with booting from either SD or USB Key. Any way around this issue? 

How did you try to install ubuntu ? using wubi I suppose ? 
After inserting ubuntu cd in windows you selected install inside windows ?

> 
I would think that the windows bootloader that gives you the option to either boot to Win7 or Ubuntu, has SD or usb drivers that it can access should you select ubuntu. 

Actually ubuntu creates grub in a file for windows and wubi creates an entry in windows boot loader so that you can select to boot into ubuntu.

> 
Should this not work? 

I installed ubuntu from within Windows. No, no hard drive partitions were created. Rather the win7 boot.ini was created that simply points to ubuntu in the SD path, in addition to the win7 in hard drive. 

Any clues?

I think you would have done it correctly just choose the right options in the wubi installer and you are up with a working ubuntu installed inside windows :)
Could you tell exact steps of what you did ?

> 
Oh and so BIOS should not have anything to do with this. BIOS simply loads the windows boot loader. This bootloader then presents an option to either boot to Win7 or Ubuntu (it gets its information from the boot.ini file), and simply should boot to the path selected.

Yes BIOS has nothing to do with this . It can just load boot loader.

---

### Post by flana on 2011-04-14
OK so My machine is running Win7 - 64 bit. SO I thought of downloading the 64bit ISO - "ubuntu-10.10-desktop-amd64". I used virtual CD to invoke the installation. Windows Autoplay option presented an option to run Wubi.exe. I selected that. Then I get an Ubuntu Menu dialog box and I select "Install inside Windows" option. I then get another dialog box - Ubuntu Installer. I select the following options - G Drive(59GB free), Installation size - 17G, Desktop environment - Ubuntu, Language - English, username and password. I then hit the install button. The SD was formated with extFAT.

Installation suceeded and aksed for a reboot. Upon reboot, I was presented with an option to boot to Win 7 or Ubuntu. I selected Ubuntu but then I get an error that it could not find the mbr path..

---

### Post by flana on 2011-04-14
Og the error I get is missing or corrupt application \ubuntu\winboot\wubildr.mbr

Hope someone can tell what is it that I am doing wrong...

---

### Post by grvsaxena419 on 2011-04-14
> **flana said:**
> OK so My machine is running Win7 - 64 bit. SO I thought of downloading the 64bit ISO - "ubuntu-10.10-desktop-amd64". 

Does yours is an Amd system ? you should download the 32-bit version , which is recommended.

> 
I used virtual CD to invoke the installation. Windows Autoplay option presented an option to run Wubi.exe. I selected that. Then I get an Ubuntu Menu dialog box and I select "Install inside Windows" option. I then get another dialog box - Ubuntu Installer. I select the following options - G Drive(59GB free), Installation size - 17G, Desktop environment - Ubuntu, Language - English, username and password. I then hit the install button. The SD was formated with extFAT.

How does format of a partition taking place. Wubi creates a file in C: drive wuilder and wuilder.mbr It should also create a folder in G: drive with the name ubuntu . Could you post the contents of ubuntu folder . May be some file is missing I could see that then.

> 
Installation suceeded and aksed for a reboot. Upon reboot, I was presented with an option to boot to Win 7 or Ubuntu. I selected Ubuntu but then I get an error that it could not find the mbr path..
Some copy paste of files may work.

---

### Post by flana on 2011-04-14
So this is an Intel Core i3 laptop. I did check the contents of the installation the .mbr file does exist.

Let me try the 32-bit version.

---

### Post by flana on 2011-04-14
32bit ISO fails in the same way.

---

### Post by grvsaxena419 on 2011-04-16
> **flana said:**
> 32bit ISO fails in the same way.

You getting the same error ?
Did you check the contents of ubuntu folder in your G: drive ? Does it contain the required files in boot folder and also does your C: ie the windows boot partition contails wbuilder and wbuilder.mbr files ?

Try installing in a different partition . Your antivirus may also prevent it from installing check that also . Try uninstalling it using wubi and then install it again .

---

### Post by flana on 2011-04-20
Same error... I also tried an external usb hard drive instead of the USB key.

All required files and folders are there in the install path.

does your C: ie the windows boot partition contails wbuilder and wbuilder.mbr files ? - I need to check this. let me check.

---

### Post by flana on 2011-04-21
Yes I do see the wubildr and wubildr.mbr in root c:

---

### Post by Quackers on 2011-04-21
It might be worth having a look here for suggestions
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by flana on 2011-04-21
OK so saw the light, It's not the train...

So now I installed the 32bit version on the external HD, that worked although the touch pad does not work. 

But I need to get the intsalltion working for 64bit in the SD... I will keep trying...

---

