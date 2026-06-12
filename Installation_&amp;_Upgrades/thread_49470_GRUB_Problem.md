---
title: "GRUB Problem?"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by Copter on 2005-07-16
hi!

first i have to say that im total linux n00b.

ive installed Kubuntu on USB HDD (had to add ehci_hcd to intrid). everything worked fine until i tried to boot kubuntu from my USB HDD on some other computer (with gentoo / winxp installed). system was booting really slow and after all it said that it will not load X because it hasnt got proper display drivers. but shell and everything was working fine.

ive mounted HDD back to my computer (where system was installed) and now something strange happens. it shows GRUB 1.5 sign for about 1 sec and then it reboots. it doesnt even show 'press ESC for menu' sign.

ive booted form Kubuntu DVD and enterd rescue mode.mounted as root sys my USB drive. in /boot/grub/menu.lst i found something about boot: (hd0,0). maybe thats the problem. dunno...

please help,
thanks very much for any tries
Copter :]

---

### Post by javiadip on 2005-07-16
wat kind of usb hard drive do you have? coz Ubuntu kernal have problems loading Ubuntu from western digital hard drive....

---

### Post by Copter on 2005-07-16
its 3,5" ata100 40gb drive in 3,5" external usb case. cant remind manufactuer but everything was fine until i tried to boot from another compuer. ive installed loads of stuff on it. it just doesnt want to start now :(

---

### Post by WildTangent on 2005-07-17
you cant just switch all your hardware around and expect it to work. when Ubuntu is looking for the devices corresponding to its drivers for computer A, when you have it attached to computer B, there will be problems

-Wild

---

### Post by jerome bettis on 2005-07-17
i can't really help you, but this guy ^ sounds like he's on to something.  ubuntu works on your computer, not everybody else's.

i'm trying to do the same thing now, and i can't get both my usb drive and my internal drive to boot.  i made a thread here  [http://www.ubuntuforums.org/showthread.php?p=258639#post258639](http://www.ubuntuforums.org/showthread.php?p=258639#post258639)

also if you could explain how you added the usb stuff to the initrd here i would be very thankful, because i still have to do that after i get both drives booting seperately.

---

### Post by Copter on 2005-07-17
i did it [this](http://www.ubuntuforums.org/showthread.php?t=20522&highlight=pivot_root+file) way on hoary kubuntu. worked fine until i booted from this drive from another mashine. i think _some_ config files were changed but i have no idea which ones :(

copter :]

---

### Post by Copter on 2005-07-17
[QUOTE=WildTangent]you cant just switch all your hardware around and expect it to work. when Ubuntu is looking for the devices corresponding to its drivers for computer A, when you have it attached to computer B, there will be problems

-Wild[/QUOTE]

ok, now i know that. i thought that the worst thing that could happen is that i will not be albo to boot the system from my drive on other computer. i tied that and i see that something else has been messed :(

anyway thanks for advise

copter :]

---

