---
title: "problem with install"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by ghost leviathan on 2010-08-14
i recently installed 10.04 on my old laptop and keeps going to black screen. i changed the nomodeset at the install screen and can run from cd just fine but when i go to install it dose its thing then on restart in goes back to black any info would help i am really new to linux and  laymen terms would help alot

---

### Post by Rubi1200 on 2010-08-14
What graphics card do you have installed?
How much RAM does the system have?

Also, take a look here:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

If something is not clear, ask.

---

### Post by ghost leviathan on 2010-08-14
not sure on the graphics card but 512 ram. i used the 1915.modeset=1 on the try before install and it works but after that i get a grub out of disk error

---

### Post by Rubi1200 on 2010-08-14
Try booting the computer and when you get to the GRUB menu press e to edit the entry.

If you do not see a GRUB menu try hitting Shift a few times after the BIOS screen.

Using the cursor find the line that ends with ```
ro quiet splash
```

Remove quiet splash and add the i915.modeset=1 parameter. Then Ctrl + x to boot.

If you get in, post back here and we will try and walk you through making this more permanent.

---

### Post by ghost leviathan on 2010-08-14
now it wont work at all gunna start over i am at the ubuntu install screen right now can we start from there

---

### Post by Rubi1200 on 2010-08-14
You are attempting to reinstall now?

Ok, just proceed with the install and when you restart the computer follow what I suggested in the previous post about editing GRUB at boot time.

But, to make sure you enter the right parameter, we really need to know what graphics card you have.

So, when Ubuntu is installed, **before** you restart, go to the terminal (Applications > Accessories) and post the results of this:

```
lspci | grep VGA
```

---

### Post by ghost leviathan on 2010-08-14
Ok i am doing try without install and putting the i915.modeset=1 in the boot option box thats the only way i can get to the desktop

---

### Post by Rubi1200 on 2010-08-14
> **ghost leviathan said:**
> Ok i am doing try without install and putting the i915.modeset=1 in the boot option box thats the only way i can get to the desktop
Ok, if it works and you get to the desktop then post the results of the code I mentioned in the previous post please.

---

### Post by ghost leviathan on 2010-08-14
intel 82852/855gm integrated graphics device

---

### Post by Rubi1200 on 2010-08-14
> **ghost leviathan said:**
> intel 82852/855gm integrated graphics device
Ok, I suspected it might be something like that.

If Ubuntu is now installed successfully, you can restart the computer and follow what I already posted:

> Try booting the computer and when you get to the GRUB menu press e to edit the entry.

If you do not see a GRUB menu try hitting Shift a few times after the BIOS screen.

Using the cursor find the line that ends with  	Code:
 	ro quiet splash 
Remove quiet splash and add the i915.modeset=1 parameter. Then Ctrl + x to boot.

Then, once you are back in Ubuntu, take a look here for more permanent fixes/workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Read the link carefully, but if I am not mistaken you need to apply Workaround F.

I hope this helps and good luck!

:)

---

### Post by ghost leviathan on 2010-08-14
alright i just installed havent rebooted yet what next?

---

### Post by Rubi1200 on 2010-08-14
See my previous post :)

You can boot the computer and set the i915.modeset=1 parameter in GRUB; that will get you back to the desktop again.

Then read and apply, where relevant, one of the workarounds in the link I posted.

---

### Post by ghost leviathan on 2010-08-14
i get this 
error:out of disk
grub rescue>

---

### Post by Rubi1200 on 2010-08-14
Ok, a bit of searching has come up with a couple of possibilities:

1. BIOS needs to be updated

2. See the information here: [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

Unfortunately, I do not have any experience working with GRUB in rescue mode and would not be the right person to advise you on how to proceed from here.

I hope one of the more experienced forum members will see this and post some suggestions.

Hang in there! 

This can be fixed; it just might take a little more time and effort.

---

### Post by ghost leviathan on 2010-08-14
thanks for all the help i have been searching and cant find anything on this grub rescue but like i said thanks again for helping me get this far

---

