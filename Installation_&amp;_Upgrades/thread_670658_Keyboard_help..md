---
title: "Keyboard help."
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by motomandd on 2008-01-17
Hello, I have been trying to install several versions of Ubuntu from 6.06 to 7.10, tried geubuntu, kubuntu, gobuntu xubuntu and all the same error. what happens is that i pop in the live CD of ubuntu, press the start or install ubuntu, and whenever it finishes loading, i go to install ubuntu but, keyboard freezes! even the numlock wont turn off, i do not know why, and i really want to install it, any ideas? 

PS: i have tried this with 3 keyboards now.

---

### Post by motomandd on 2008-01-17
Any help would be appreciated, and if you need more info just ask please.

---

### Post by Partyboi2 on 2008-01-17
hi, try updating your bios if you are able too
[http://ubuntuforums.org/showthread.php?t=604346](http://ubuntuforums.org/showthread.php?t=604346)

---

### Post by motomandd on 2008-01-17
I have the latest BIos update so far, and its a PS/2 keyboard.

---

### Post by motomandd on 2008-01-17
I have an HP pavillion a6000n if that helps

---

### Post by motomandd on 2008-01-17
i have now tried fedora, PClinuxOS and mandriva, still same error, but with windows, it works fine!

---

### Post by motomandd on 2008-01-17
Just tried OpenSuSe, ubuntu 8.04 and ubuntu 6.06 again, and the 6.06 gives me a kernal panic. i getting mad, just wanna get stupid ubuntu on my PC...

---

### Post by motomandd on 2008-01-17
no ideas how to fix my problem?

---

### Post by motomandd on 2008-01-17
Im gonna try the AMD 64 bit verion, as i have a 64 bit CPU.

---

### Post by motomandd on 2008-01-19
can anybody please help me???

---

### Post by Partyboi2 on 2008-01-19
Try booting with acpi=off as a boot option
When you are at the main menu press F6
at the end of the line add ```
acpi=off 
```and then press enter. If this works you will need to add it to grub menu.lst
One person suggests:
> if you have a PS/2 keyboard and it's not working, try disabling legacy usb or "direct usb" or whatever it's called in your bios. If you do have a usb keyboard, enable it.Were those 3 keyboards you tried all PS/2 boards or have you tried with a USB keyboard?

---

### Post by motomandd on 2008-01-19
they are all PS/2 keyboards.

---

### Post by Partyboi2 on 2008-01-19
If you are able to get your hands on a usb keyboard or a ps/2 to usb adaptor, you could try that as well.

---

### Post by motomandd on 2008-01-19
will do! thanks!

---

### Post by motomandd on 2008-01-19
will ubuntu amd64 make a difference in my prob...?

---

### Post by Partyboi2 on 2008-01-19
> will ubuntu amd64 make a difference in my prob...?
Pass :) Maybe someone else would know that answer.
Post back if adding acpi=off works and someone will tell you how to add it to grub menu.lst so that it works all the time.

---

### Post by motomandd on 2008-01-20
my live CD is at home right now, but i just downloaded the amd64 version, and it solved my problem, works GREAT! thank you for your help anyways!

---

### Post by rosegarden78 on 2008-01-20
Um...geubuntu and gobuntu are NOT Ubuntu distros ... there are four:

Ubuntu
Kubuntu
Xubuntu
Edubuntu

If you installed anything less backup your /home folder and do a clean install of Ubuntu 7.10 Gutsy Gibbon.  Anything less would uncivilized but of course.  And do you happen to have any Grey Poupon?

---

### Post by motomandd on 2008-01-20
umm, i havnt even installed one yet, i just tried those to see if there would be any difference, and i never said that they were ubuntu distros, i just tried them for the heck of it.

---

