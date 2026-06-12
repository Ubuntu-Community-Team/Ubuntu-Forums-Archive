---
title: "Problem installing on external hard drive"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by Brennagan on 2008-09-20
I go through the installation and when it asks where to install i choose manual so i can select my external hard drive. It has no information on it i wiped it clean and i format it how it wants it but then when i press forward it says, "No root file system is defined. Please correct this from the partitioning menu." And ive tried every format any ideas? thanks

---

### Post by overdrank on 2008-09-20
> **Brennagan said:**
> I go through the installation and when it asks where to install i choose manual so i can select my external hard drive. It has no information on it i wiped it clean and i format it how it wants it but then when i press forward it says, "No root file system is defined. Please correct this from the partitioning menu." And ive tried every format any ideas? thanks

Hi and when you are setting up the partition you will need to  set the  / symbol for the root.

---

### Post by Brennagan on 2008-09-20
Ill try that but ive kinda got myself in quite a predicament lol. Any help is appreciated

I was told earlier to just install ubuntu as an program in Vista (internal hard drive) so now anytime I boot up just the internal hard drive i get that option ubuntu and vista even tho i no longer have uubuntu is there anyway to get rid of that?

And second problem is i wiped the external hard drive and just tried to install it on the clean version and it kinda works if i mess around a little i can eventually get into ubuntu but it requires a lot of resets and get a lot of "GRUB error 21" and need to fix it any help?

---

### Post by overdrank on 2008-09-20
> **Brennagan said:**
> Ill try that but ive kinda got myself in quite a predicament lol. Any help is appreciated

I was told earlier to just install ubuntu as an program in Vista (internal hard drive) so now anytime I boot up just the internal hard drive i get that option ubuntu and vista even tho i no longer have uubuntu is there anyway to get rid of that?

And second problem is i wiped the external hard drive and just tried to install it on the clean version and it kinda works if i mess around a little i can eventually get into ubuntu but it requires a lot of resets and get a lot of "GRUB error 21" and need to fix it any help?

Hi and for the first, I believe when you uninstall Ubuntu from within vista that should be removed. I have not use that method Wubi
Second it appears there is a issue with the grub and where it is installed. If you install ubuntu on a external drive and install the grub there then I believe this is the proper way. If you installed the grub to the internal drive then without the external drive installed this error will occur. 
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by Brennagan on 2008-09-21
First, thats what i thought too but it is uninstalled from within vista but its still there. What could i do to fix it? and ill look into the grub error while awaiting another post.

---

### Post by Brennagan on 2008-09-21
would super grub disk help?

---

### Post by Brennagan on 2008-09-21
update: not exactly sure how to use it but it didnt help

---

### Post by overdrank on 2008-09-21
> **Brennagan said:**
> update: not exactly sure how to use it but it didnt help

Hi and I am sorry but I have not installed on a external drive so I am not of much help. Did you have any luck with the link I post previously? If not then you may look here.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Brennagan on 2008-09-21
Ill keep looking but for right now im just trying to figure out how to get my laptop back to normal. If the external hard drive is unplugged i get a error 21 and cant get passed that if its plugged in i can choose vista (on internal hd) or 3 different ubuntus which 1 works but i was wondering how to get rid of the error 21 and the ubuntu choice for now so that it will work just like it did. I tried repairing and system repair from the vista disk.

---

### Post by overdrank on 2008-09-21
> **Brennagan said:**
> Ill keep looking but for right now im just trying to figure out how to get my laptop back to normal. If the external hard drive is unplugged i get a error 21 and cant get passed that if its plugged in i can choose vista (on internal hd) or 3 different ubuntus which 1 works but i was wondering how to get rid of the error 21 and the ubuntu choice for now so that it will work just like it did. I tried repairing and system repair from the vista disk.

Hi and you have 3 choices of ubuntu which should be the first which is the latest kernel update. Second which is recovery mode and third is memtest. This is normal and you can edit your grub menu list to change that but I would recommend not as you may need recovery mode to recover some data or your system. As I stated earlier if the drive is not connected you will receive that error. That is because the grub is installed on the internal drive and should be installed on the external.

---

### Post by Brennagan on 2008-09-21
Yep i get those options and windows longhorn loader or something like that and if i select that one it goes to one thats just Vista/Ubuntu which i also want to get rid of. How do i unistall grub from the internal and get rid of the other menu. thanks btw for all the help thus far im very grateful

---

### Post by Brennagan on 2008-09-21
any ideas?

---

### Post by Brennagan on 2008-09-22
I keep looking and cant figure out how to fix it

---

### Post by meierfra. on 2008-09-22
I recommend  EasyBCD (see my signature)

For further help, post the output of

```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by Brennagan on 2008-09-23
OK new issues. Vista boots and loads just fine but whenever I set my external hard drive as first and get to the grub menu all of the ubuntu options give me a grub error 17. When i installed i made sure to put the boot on the external usb. Thanks in advance.

---

### Post by meierfra. on 2008-09-23
Boot from the external drive. Select the ubuntu entry. But do not press enter, press "e" instead. At the new screen press "e" again.   Change

"root (hdX,Y)" to "root (hd0,Y)" 

So change the first number to "0" and do not change the second number. Press "enter" and then "b" to boot.

This should boot you into Ubuntu.

To make these changes permanent:

```
gksudo gedit /boot/grub/menu.lst
```

Change 

"# groot=(hdX,Y)" to "# groot=(hd0,Y)"

Save the file. Back in the terminal

```
sudo update-grub
```

Reboot and you should be able to boot into Ubuntu.

If this did not work post your "menu.lst" and the output of "sudo fdisk -l"

---

### Post by Brennagan on 2008-09-23
Thank you that worked perfectly but now I have another question. The vista loader wont work through grub so i prolly have it wrong also would i do it the same way but insead of 0 make it 1 since its on the internal hdd?

---

### Post by meierfra. on 2008-09-23
> would i do it the same way but insead of 0 make it 1 since its on the internal hdd?

yes.

---

