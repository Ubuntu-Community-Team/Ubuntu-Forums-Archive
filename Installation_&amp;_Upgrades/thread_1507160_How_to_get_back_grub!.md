---
title: "How to get back grub?!"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by amishra123 on 2010-06-11
Hi I previously had ubuntu 10.04 and windows 7 on dual boot with grub. But then I reinstalled Windows 7 and now there is no grub or anything and i cant get into linux!! I am on a netbook so dont have a cd or floppy drive either!!!  
I have had some experience with SGD so i have tried using unetbootin with my usb but i keep getting "Bootmgr missing" when i try to boot from it !!!(i am sure it has worked before) Anyway where to go from now?! I guess i need to get the SGD working on my usb? Any help?
Thank you very much in advance Amishra

---

### Post by darkod on 2010-06-11
You need to boot with a 10.04 ubuntu live usb stick and reinstall grub2 to the MBR of the disk. Detailed instructions are here, and make sure you use the instructions for 10.04:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Ichido on 2010-06-11
When you Install/Reinstall M.S. windows, it will Wipe out everything on the drive.
This is Windows way of trying to be your Only O.S.

---

### Post by amishra123 on 2010-06-12
> **Ichido said:**
> When you Install/Reinstall M.S. windows, it will Wipe out everything on the drive.
This is Windows way of trying to be your Only O.S.

No i had Ubuntu on a different partition so it should still be there!? Shouldn't it??! I selected my windows partition specifically for the install so fingers crossed its still there!!
Amishra

---

### Post by darkod on 2010-06-12
> **amishra123 said:**
> No i had Ubuntu on a different partition so it should still be there!? Shouldn't it??! I selected my windows partition specifically for the install so fingers crossed its still there!!
Amishra

Don't worry, it should be there. It's not true that windows install wipes the hdd, it all depends what you tell it to do during the install.

Did you try to reinstall grub2 to the MBR with the instructions from my previous post?

---

### Post by amishra123 on 2010-06-13
> **darkod said:**
> Don't worry, it should be there. It's not true that windows install wipes the hdd, it all depends what you tell it to do during the install.

Did you try to reinstall grub2 to the MBR with the instructions from my previous post?

Darkod thank you very much!!! Maybe should have found it myself!! Its back to exactly how it was before!!

On a seperate unrelated note, When i first got my netbook (Asus eee pc) there was no splash screen at the begining but after installing linux now there is that ugly Asus splash screen when i put the computer on, is there any way i can stop it from appearing like when i first got the laptop?

Thank you very much anyway! 
Amishra

---

### Post by darkod on 2010-06-13
> **amishra123 said:**
> 
On a seperate unrelated note, When i first got my netbook (Asus eee pc) there was no splash screen at the begining but after installing linux now there is that ugly Asus splash screen when i put the computer on, is there any way i can stop it from appearing like when i first got the laptop?

Thank you very much anyway! 
Amishra

Usually there is setting in BIOS for that. Go into BIOS with F2 or what ever button you need to press during boot, and look at the options there.

Usually they call it Logo and there should be option to disable it. But I can't be sure, it depends on the manufacturer.

---

### Post by amishra123 on 2010-06-13
yeah thanks for your help darko!! I have got BURG now, its really really good!! heres a link to [http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)  
It is really awesome!! I definetly recommend it if you can get it to work!!

---

### Post by darkod on 2010-06-13
> **amishra123 said:**
> yeah thanks for your help darko!! I have got BURG now, its really really good!! heres a link to [http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)  
It is really awesome!! I definetly recommend it if you can get it to work!!

I actually don't recommend other bootloaders than the official one. It also helps avoid confusion if you need help later but forget to specify that you are not using grub.

I'm happy with my grub2, it works great. It just needs to boot my OS, nothing fancy. :)

---

