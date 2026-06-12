---
title: "Error installing Ubuntu 12.10 using my USB stick"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by saintsinners on 2013-01-19
I got this error message while installing Ubuntu 12.10 32bit

"The system log from your installation  contains error. The specific error commonly occurs when there is an  issue with the media from which you were installing. This can happen  when your media is dirty or damaged or when you've burned the media at a  high speed. Please try cleaning the media and or burning new media at a  lower speed. In the even that you continue to incounter these errors it  may be an issue with your CD/DVD drive."

I used USB flash drive stick to boot it.
Anyone know how to fix this problem? I will really appreciate your help.

---

### Post by powerwave on 2013-01-19
> **saintsinners said:**
> I got this error message while installing Ubuntu 12.10 32bit

"The system log from your installation  contains error. The specific error commonly occurs when there is an  issue with the media from which you were installing. This can happen  when your media is dirty or damaged or when you've burned the media at a  high speed. Please try cleaning the media and or burning new media at a  lower speed. In the even that you continue to incounter these errors it  may be an issue with your CD/DVD drive."

I used USB flash drive stick to boot it.
Anyone know how to fix this problem? I will really appreciate your help.

Have you tried it also with another USB flash drive stick?

~

---

### Post by saintsinners on 2013-01-19
no i have not try that and also I use sourceforge to have a USB boot stick.

---

### Post by Aergan on 2013-01-19
Do a full format to Fat32 on the USB stick with Gparted or Diskpart if you have windows. From there I would use Unetbootin to extract the ISO contents to the USB stick and make it bootable.

---

### Post by saintsinners on 2013-01-19
I don't have OS, the ubuntu 7 give me a problem it deleted my Windows 7 and i've tried to install Ubuntu 12.10 to my Ubuntu 7 OS and unfortunately it was failed.
and now the real problem comes up I can use my computer when I'm using the USB that can boot Ubuntu 12.10 teh USB I'm using to install Ubuntu 12.10 but got the same error everytime, so i came up using it but by choosing the Try Ubuntu 12.10 without installing it every time I'm using my computer.

Sorry for my bad english, i hoped you understand it.

---

### Post by saintsinners on 2013-01-19
I can only use my computer if I'll use the USB that has the Ubuntu 12.10 ISO and boot it every time.

---

### Post by oldfred on 2013-01-19
From your live install to a flash drive download and run BootInfo report.


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by saintsinners on 2013-01-19
yes i will inform you, thanks for this steps.. I will tell if this works.

---

