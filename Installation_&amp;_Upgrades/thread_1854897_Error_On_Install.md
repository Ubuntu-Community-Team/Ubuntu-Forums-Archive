---
title: "Error On Install"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by paulb7873 on 2011-10-05
First time trying ubuntu. Heard nothing but good. My problem is i get this error twoards the end of the install.
 
[http://tinypic.com/r/2vl0d4k/7](http://tinypic.com/r/2vl0d4k/7)
 
Pls any help? THANK YOU

---

### Post by paulb787 on 2011-10-05
Also when i boot up i get "error dont have hardware to run unity

run clasic on login screen" However i have no option to do that 

on my login screen?

---

### Post by Rubi1200 on 2011-10-05
Hi and welcome to the forums :)

Which version of Ubuntu are you trying to install?

Did you check the integrity of the image before installing?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also post the specifications for the computer ans whether this is a fresh install or an upgrade.

---

### Post by paulb787 on 2011-10-05
Im trying to install 11.04 the latest. i get the error i posted in the picture link durring install then when i boot up i get hardware cant run unity switch to classic on login. However there is option too?

---

### Post by paulb7873 on 2011-10-05
Ok I used the alternate cd and am good with no errors. However I still can't login.
There is no option to go to clasical mode.. anyone

---

### Post by paulb7873 on 2011-10-05
ok i figured out how to log in to classic. the option was not on my screen as my monitor i. i just have a blank desktop. i need to figure out how to get my graphics driver going? if any1 could help.? i have a gtx 470 and have seen some tutorials but i only have a blank desktop.??

---

### Post by mörgæs on 2011-10-05
This thread might help:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by 450rOOST on 2011-10-06
Folks,

I had the same problem last night.  New install of 11.04.  At first login it said, 'dont have hardware for unity, run classic'  what hardware is it talking about and what do I need to do?

I read in another thread that I may need to install graphics card drivers, I'll try that.

01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

---

### Post by mörgæs on 2011-10-07
Ubuntu 11.04 switches automatically to the old/classic Gnome desktop, if it deems the hardware to be not strong enough. 

This works most of the time, but I would recommend installing Xubuntu in stead.

---

### Post by MAFoElffen on 2011-10-07
> **paulb7873 said:**
> ok i figured out how to log in to classic. the option was not on my screen as my monitor i. i just have a blank desktop. i need to figure out how to get my graphics driver going? if any1 could help.? i have a gtx 470 and have seen some tutorials but i only have a blank desktop.??
Thanks for refering my sticky mörgæs... This will help 450rOOST also as he is also nvidia.

Either go: System > Administration > Additional Drivers > select your driver > Activate. "paulb7873" would select nvidia-current. I don't know what "450rOOST" woild select as 0x0df5 is not a valid nVidia GPU ID number. 

Or to install the binaries from nVidia instead, look at Post              #[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280") of my sticky...  I'll chexk back to see if you had further questions or such.

Note to 450rOOST: 
Please post results of:
```

lspci -vmm | grep VGA

```Next-  Both of you have already started Ubuntu , without your drivers unstalled, so it fell back to the gnome fllback (Ubuntu Classic)... So after you install your drivers and you reboot...

At the GDM Logo Screen > Select a User with your mouse > When the password dialog popups up, look down at the bottom of your screen to the Bottom bar. On that bar, about halfway across should be a pulldown menu. > Select the pulldown menu with your mouse. > Select Unity ... 

Enter your password and continue logging in.  GDM will remember your last selection as the default for the next login.

---

