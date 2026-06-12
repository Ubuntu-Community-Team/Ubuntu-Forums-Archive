---
title: "Windows XP Pro SP2 to Linux. HOW?"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Jimit87 on 2006-08-28
Dell Desktop.
intel P4 2.00GHz CPU
nVidia MX420 64MB
768MB Ram
120GB HD
Cable internet service.

So now i am thinking about using Linux with my Windows XP Pro. SP2

1) I will first install Windows XP Pro SP2
2) While installing Windows XP Pro SP2, how do i make partition so i can install linux later on? Detail description needed.
3) I will install all the drivers and my internet service, Cable, i will be needing on Windows OS
4) I will then install Linux, Ubuntu 6.06.
5) Will i need to install all the drivers again? Will i need to install drivers for my VGA card, and other hardwares on my comp? (i checked on dell website and couldn't find Linux drivers for any hardware) But i did find the driver for my VGA on nVidia's official website.
6) Will i need to install internet service,Cable on my Linux OS again?
7) How do i dual boot my OS? Will my comp give me option when i turn on my comp autometically, without installing any other software?

Answer them in #s.

Thank you.

---

### Post by tagra123 on 2006-08-28
If you want a dual booting machine:

First install windows.

Second install Ubuntu. The Ubuntu installer will take care of everything for you.

When the install is completed a "grub" menu will give you the option of booting into windows or ubuntu.

Also Google for VMplayer Ubuntu  if you dont want to dual boot and still need access to windows for minimal applications.

---

### Post by MiThRaZoR on 2006-08-28
> **Jimit87 said:**
> 
1) I will first install Windows XP Pro SP2
2) While installing Windows XP Pro SP2, how do i make partition so i can install linux later on? Detail description needed.
3) I will install all the drivers and my internet service, Cable, i will be needing on Windows OS
4) I will then install Linux, Ubuntu 6.06.
5) Will i need to install all the drivers again? Will i need to install drivers for my VGA card, and other hardwares on my comp? (i checked on dell website and couldn't find Linux drivers for any hardware) But i did find the driver for my VGA on nVidia's official website.
6) Will i need to install internet service,Cable on my Linux OS again?
7) How do i dual boot my OS? Will it give me option when i turn on my comp autometically, without installing any other software?

2. You could install Norton PartitionMagic and do it or you could do it from DOS. I'm not sure about this, but I'm sure you could create partitions when you're installing Linux. I'm not sure on that, but it should ask you if you want to partition before it starts installing.

5. Yes, but depending on some Linux operating systems, it might have the drivers already installed by default. But some upgraded parts will need to be updated/installed seperately.

6. You say that you have Cable right? Which means that the internet will be always on. So if I'm assuming correctly, it should be the same with Linux. But you might need to.

7. When you're installing Linux and want to dual boot, make sure you make another partition or have another hard drive to install Linux on. So Windows will be on one partition, and Linux will be on the other. If you choose to install Linux on the partition that Windows is on, Windows will get wiped out. So be careful. Do that part carefully. After you're done with the installation, and you turn on your computer, it'll give you an option to which one you want to boot. Whether it be Windows or Linux.

Hope that helps.

---

### Post by confused57 on 2006-08-28
> **Jimit87 said:**
> Dell Desktop.
intel P4 2.00GHz CPU
nVidia MX420 64MB
768MB Ram
120GB HD
Cable internet service.

So now i am thinking about using Linux with my Windows XP Pro. SP2

1) I will first install Windows XP Pro SP2
2) While installing Windows XP Pro SP2, how do i make partition so i can install linux later on? Detail description needed.
3) I will install all the drivers and my internet service, Cable, i will be needing on Windows OS
4) I will then install Linux, Ubuntu 6.06.
5) Will i need to install all the drivers again? Will i need to install drivers for my VGA card, and other hardwares on my comp? (i checked on dell website and couldn't find drivers for linux for any hardware) But i did find the driver for my VGA on nVidia's official website. 
6) Will i need to install internet service,Cable on my Linux OS again?
7) How do i dual boot my OS? Will it give me option when i turn on my comp autometically, without installing any other software?

Answer them in #s.

Thank you.

Sounds just like my Dell Dimension 4550, which runs Ubuntu flawlessly.  Ubuntu recognized all my hardware without having to install any additional drivers, the "nv" video driver works for me...but there are numerous "howto's" in the forum to installing the nvidia legacy drivers for 3D.  If you have a wired internet connection, you shouldn't have any problems, I also have wired Cable internet(Road Runner)...everything was automatically detected, lucky for me.
You can install Windows on one large partition and the Ubuntu installer "should" be able to resize it, but it'd probably be best to set up a separate partition to be used for Ubuntu...somebody else will have to advise you on that.
When you install Ubuntu, it will install it's grub bootloader to the Windows mbr, which enable you to boot either Windows or Ubuntu.  I circumvented this by installing a 2nd harddrive, installed Ubuntu on it, as described here:


[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Take your time, read some dualboot guides & other "howto's" in the forum:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Jimit87 on 2006-08-29
tagra123, MiThRaZoR, and confused57 thank you for your help.

i will try to combine everyone's feedback and post what i will do later, and you can tell me what should i do and what i shouldn't do.

and confused57, i have dell 4550 as well. how did u figure it out?

---

### Post by confused57 on 2006-08-29
> **Jimit87 said:**
> tagra123, MiThRaZoR, and confused57 thank you for your help.

i will try to combine everyone's feedback and post what i will do later, and you can tell me what should i do and what i shouldn't do.

and confused57, i have dell 4550 as well. how did u figure it out?

Your computer has the very same specs as mine(except for 512 mb ram), so it about had to be a 4550...Ubuntu runs quite well on the one I have.  Run the Live CD & see what you think...you know to press F12 at bootup to select boot from cd?

---

### Post by Jimit87 on 2006-08-29
i had 256MB ram but i upgraded mine to 768MB lol. now its better.

:)

---

