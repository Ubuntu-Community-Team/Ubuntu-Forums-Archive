---
title: "missing ubuntu after installing fedora"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by rampage3 on 2010-11-11
Hello there 
i have a probleme with my linux system and i think there is no place better than here so please help me:
In my system i had windows xp SP3 and ubuntu 10.04.I wanted to teste the fedora 12 environment so i installed that in different partition but after installation i have only options for choosing fedora and and windows and ai cant see ubuntu ?What should i do now?

---

### Post by coffeecat on 2010-11-11
The Fedora installer is very anti-social in that it ignores other Linux OSs also installed to the system, even though it will detect the presence of Windows and make a dual-boot menu for you - as you have found. Also Fedora still uses legacy grub, whereas Ubuntu 10.04 uses grub 2.

You have two options.

1 - You can boot into Fedora and edit its grub /boot/grub/menu.lst file to add an entry for Ubuntu. If you are not comfortable doing that, then...

2 - Boot up with the Ubuntu 10.04 live CD and have a look at this link.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Read those paragraphs carefully. With the 'sudo grub-install --root-directory=/mnt/ /dev/sdX' command (changing sdX for, probably, sda) you reinstall grub2 stage 1 to the MBR of the hard drive. Now reboot and you will see the Ubuntu grub menu, but no menu entry for Fedora just yet. Don't worry - that's easily added. Once you are in the Ubuntu desktop (your hard drive installation, not the live CD), run this terminal command:

```
sudo update-grub
```This will regenerate your Ubuntu grub menu to include an entry for Fedora. You will now have a triple-boot menu.

By the way, Fedora 12 is nearly obsolete and will not be supported for long. Fedora 14 has just been released and you might want to try that instead. And here's a useful Fedora guide for you:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

---

### Post by rampage3 on 2010-11-13
> **coffeecat said:**
> The Fedora installer is very anti-social in that it ignores other Linux OSs also installed to the system, even though it will detect the presence of Windows and make a dual-boot menu for you - as you have found. Also Fedora still uses legacy grub, whereas Ubuntu 10.04 uses grub 2.

You have two options.

1 - You can boot into Fedora and edit its grub /boot/grub/menu.lst file to add an entry for Ubuntu. If you are not comfortable doing that, then...

2 - Boot up with the Ubuntu 10.04 live CD and have a look at this link.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Read those paragraphs carefully. With the 'sudo grub-install --root-directory=/mnt/ /dev/sdX' command (changing sdX for, probably, sda) you reinstall grub2 stage 1 to the MBR of the hard drive. Now reboot and you will see the Ubuntu grub menu, but no menu entry for Fedora just yet. Don't worry - that's easily added. Once you are in the Ubuntu desktop (your hard drive installation, not the live CD), run this terminal command:

```
sudo update-grub
```This will regenerate your Ubuntu grub menu to include an entry for Fedora. You will now have a triple-boot menu.

By the way, Fedora 12 is nearly obsolete and will not be supported for long. Fedora 14 has just been released and you might want to try that instead. And here's a useful Fedora guide for you:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)




thank you alot you,i could return my ubuntu and i have dual boot with windows but now how i can add fedora 12 to my menu?

---

### Post by 00110111 on 2010-11-13
I went into the grub shell, then did the following: (not sure if it will work anymore, but meh) 

rootnoverify
map (hd#,#) (hd#,#) /number of hard drive, partition number for ubuntu, then that of the fedora install
map (hd#,#) (hd#,#)/same thing, but the other way round
makeactive
chainloader +1
boot.

It has been a while since I've done it, so it may be slightly wrong, correct it if there's anything wrong, but that's basically it. It will boot into ubuntu, and the next time you boot up, grub should recognise the ubuntu partition. (I've not used fedora, I'm basing this on the assumption that fedora also uses grub)

---

### Post by coffeecat on 2010-11-13
> **rampage3 said:**
> thank you alot you,i could return my ubuntu and i have dual boot with windows but now how i can add fedora 12 to my menu?

Re-read my earlier post. This bit:

> **coffeecat said:**
> Once you are in the Ubuntu desktop (your hard drive installation, not the live CD), run this terminal command:

```
sudo update-grub
```This will regenerate your Ubuntu grub menu to include an entry for Fedora. You will now have a triple-boot menu.


---

### Post by coffeecat on 2010-11-13
> **00110111 said:**
> rootnoverify
map (hd#,#) (hd#,#) /number of hard drive, partition number for ubuntu, then that of the fedora install
map (hd#,#) (hd#,#)/same thing, but the other way round
makeactive
chainloader +1
boot.

Sorry, but that won't work. Three reasons:

1 - You don't need the map command for Linux, only Windows if it is on a drive other than the first one.

2 - Ubuntu's grub would need to be installed to the partition boot sector of its own root partition for chainloading to work. There is no evidence that this is so.

3 - Even if the OP were to try to install grub to the partition boot sector, it very likely still wouldn't work. You get an error with grub2 if you try, and usually the write fails. It's very frustrating because in most cases chainloading is out of the question chainloading into grub2. I've managed to chainload legacy grub to grub2, but not the other way around. Except on one machine.

---

