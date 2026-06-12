---
title: "triple boot grub question"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by mikej_96 on 2007-03-22
Hi, 
I am about to install Xubuntu 6.10 on an older machine in which i currently dual boot to Windows XP and Ubuntu 6.10. I am wondering if the new Grub that Xubuntu installs will allow me to boot to all 3 operating systems. (that is, will the new Grub detect Ubuntu automatically as well as Windows XP). I do not want to install Xubuntu and then suddenly not be able to boot back to Ubuntu. 

(im pretty sure that this new grub will overwrite the old one)

Any help would be appreciated. Thanks

---

### Post by confused57 on 2007-03-22
> **mikej_96 said:**
> Hi, 
I am about to install Xubuntu 6.10 on an older machine in which i currently dual boot to Windows XP and Ubuntu 6.10. I am wondering if the new Grub that Xubuntu installs will allow me to boot to all 3 operating systems. (that is, will the new Grub detect Ubuntu automatically as well as Windows XP). I do not want to install Xubuntu and then suddenly not be able to boot back to Ubuntu. 

(im pretty sure that this new grub will overwrite the old one)

Any help would be appreciated. Thanks

When installing Xubuntu, grub "should" recognize your other OSes and include entries to boot all 3.  
The live cd can be used to install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You might also want to consider installing Xubuntu's grub to it's root partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

then just add an entry to your Ubuntu grub to boot Xubuntu, using chainloading.

---

### Post by mikej_96 on 2007-03-22
thanks for the suggestions. Im going to see if it sees other other OS's like its 'supposed to....

---

### Post by mac.ryan on 2007-03-22
You might know already, but unless you really need to have two totally independent and different linux systems, you could also install in ubuntu the package called "xubuntu-desktop", and you would then be able to choose at the login splash screen whether load with Gnome (ubuntu) or Xfce (Xubuntu).

This way you would save disk space, (and bandwith/time for system updates).

---

### Post by mikej_96 on 2007-03-22
I actually did know that. I was thinking about doing that but I wanted to see if Xubuntu was faster overall. I wasn't sure if there was any other differences between Ubuntu and Xubuntu besides just the desktops. But thanks anyway. 

And also, I just installed Xubuntu and the Grub did automatically detect all OS's. Yay.

---

