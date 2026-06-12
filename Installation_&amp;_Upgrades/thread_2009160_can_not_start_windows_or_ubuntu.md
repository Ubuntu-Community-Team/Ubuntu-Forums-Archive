---
title: "can not start windows or ubuntu"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by vistanarvas on 2012-06-24
while i was installing ubuntu something went wrong and now i cant open ubuntu or windows
i try d to install ubuntu on D:\ and windows is on C:\ so if i can open the disk i can edit it and it will work fine but i don't know how 
i have try ed to boot from usb but that dint work cuss it does not get to the boot menu
the only thing i see is a whit blinking -

i can however start asus express gate cloud and open the disk throe Google chrome
but i cant edit files

if i click on go to OS in asus express it says can not find windows
and if i want to execute the windows installation assistant

i hope someone can help I've tried to give as much info as possible

---

### Post by vistanarvas on 2012-06-24
bump

does nobody know what i can do?

---

### Post by drs305 on 2012-06-24
If you can boot to an Ubuntu Desktop via LiveCD/USB install and run Boot Repair. Open it and click on 'Recommended Repair'.

If it is a bootloader issue, BR can probably fix it. If it isn't and BR cannot repair it, run the boot info script from BR and post the link so we can take a look at your system.

There is a link to BR in my signature line.

---

### Post by vistanarvas on 2012-06-24
> **drs305 said:**
> If you can boot to an Ubuntu Desktop via LiveCD/USB install and run Boot Repair. Open it and click on 'Recommended Repair'.

If it is a bootloader issue, BR can probably fix it. If it isn't and BR cannot repair it, run the boot info script from BR and post the link so we can take a look at your system.

There is a link to BR in my signature line.

thanks for replying
but i cant use a live usb because my laptop does not get to the boot menu
when i turn it on it only shows a blinking white -

---

### Post by darkod on 2012-06-24
First of all, you said you tried to install on D: which implies installing on ntfs partition, in other words, wubi.

Did you try to install wubi inside windows?
Or ubuntu on its own partition?

There is a difference so you should specify. And if it's wubi try not to call it ubuntu since often different tools are used and people need to know. If you say ubuntu everyone thinks on the standard install on its own partition, not a wubi inside windows.

As for the laptop not booting from usb, that has nothing to do with ubuntu or wubi. Have you double checked that USB-HDD is before HDD in the boot device selection in BIOS?
Also you can try using the boot menu if the laptop has one and select to boot from the usb.

On top of all that, are you sure it doesn't boot from the usb? Or it tries to boot but fails? Blinking cursor on black screen can be a video driver issue, so in fact maybe the usb is booting but not loading the live mode because of video driver issues.

Also, when you said "something went wrong" can you be more specific? Any error message? What exactly happened?

---

### Post by vistanarvas on 2012-06-24
> **darkod said:**
> First of all, you said you tried to install on D: which implies installing on ntfs partition, in other words, wubi.

Did you try to install wubi inside windows?
Or ubuntu on its own partition?

There is a difference so you should specify. And if it's wubi try not to call it ubuntu since often different tools are used and people need to know. If you say ubuntu everyone thinks on the standard install on its own partition, not a wubi inside windows.

As for the laptop not booting from usb, that has nothing to do with ubuntu or wubi. Have you double checked that USB-HDD is before HDD in the boot device selection in BIOS?
Also you can try using the boot menu if the laptop has one and select to boot from the usb.

On top of all that, are you sure it doesn't boot from the usb? Or it tries to boot but fails? Blinking cursor on black screen can be a video driver issue, so in fact maybe the usb is booting but not loading the live mode because of video driver issues.

Also, when you said "something went wrong" can you be more specific? Any error message? What exactly happened?

i did not try to install inside windows i installed it on a different hard drive
my laptop does not show something of BIOS
when i turn it on it shows ASUS and than the white blinking -
or i can boot in the asus express gate cloud but i cant do anything there

---

### Post by vistanarvas on 2012-06-24
bump

---

### Post by darkod on 2012-06-24
> **vistanarvas said:**
> i did not try to install inside windows i installed it on a different hard drive
my laptop does not show something of BIOS
when i turn it on it shows ASUS and than the white blinking -
or i can boot in the asus express gate cloud but i cant do anything there

All laptops should have BIOS. But sometimes they have some express setting activated where it boots little faster and it doesn't show you the option to enter BIOS. Check the manual.

It's usually F2, F10, or similar. You have to have an option to select boot priority.

How did you try to install on another hdd, laptops usually have only one? Do you have two disks or this is an external disk?

It might be best to boot ubuntu in live mode (either from cd or usb, like you did when installing it) and run the boot-repair program. You can generate the boot info with boot-repair and post the link it gives you. It will show us more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vistanarvas on 2012-06-24
> **darkod said:**
> All laptops should have BIOS. But sometimes they have some express setting activated where it boots little faster and it doesn't show you the option to enter BIOS. Check the manual.

It's usually F2, F10, or similar. You have to have an option to select boot priority.

How did you try to install on another hdd, laptops usually have only one? Do you have two disks or this is an external disk?

It might be best to boot ubuntu in live mode (either from cd or usb, like you did when installing it) and run the boot-repair program. You can generate the boot info with boot-repair and post the link it gives you. It will show us more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I've try ed f2 and f10 but dint do anything
so i tryed other fnumbers and when i pressed f9 it says multiple active partitions some text and at the end it says reboot and select proper boot device
or insert boot media in selected boot device and press a key
(i think i need to make a usb)
and when i boot normal it also says this instead of the white blinking -

---

### Post by vistanarvas on 2012-06-24
ok i made a live usb with the normal ubuntu iso (i still had it on my PC so why not)
and delleted the files i thought where te problem but it dint help
i replaced the bootmgr (or something) but that dint help
i try ed to use the [boot-repair-disk.iso]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download") and the [boot-repair-disk-dev.iso]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk-dev.iso/download") from the link you gave me but if i try to put it on my usb it says invalid version string 'GNU/linux'

so maybe if some one knows what the problem can be tell me because i try ed what i think was wrong

---

### Post by darkod on 2012-06-24
You don't necessarily need to make a cd (usb) of boot-repair. It can also be added as a program in ubuntu, even in live mode.

Can you boot this ubuntu usb you made into live mode (Try Ubuntu)? Can it boot the live desktop OK?

If you can boot it, you can install boot-repair using the instructions in that link, and create the boot info results.

---

### Post by vistanarvas on 2012-06-25
> **darkod said:**
> You don't necessarily need to make a cd (usb) of boot-repair. It can also be added as a program in ubuntu, even in live mode.

Can you boot this ubuntu usb you made into live mode (Try Ubuntu)? Can it boot the live desktop OK?

If you can boot it, you can install boot-repair using the instructions in that link, and create the boot info results.

i try ed to run the commands  in the 2nd option from the link ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))

but it dint work

i also went to the guys from ICT at school thay ran a windows 7 repair thing but it dint work there saying i need to reinstall windows

---

