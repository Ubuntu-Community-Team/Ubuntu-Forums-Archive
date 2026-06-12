---
title: "Help with Installation"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by swalihmz1 on 2012-01-18
I have all the requirements for XP and Ubuntu.I have XP already with me. Yesterday, i have downloaded Ubuntu 11.10. Now i want both the OS on my computer. On installing, i don't see the option of side to side installing the OS. I have Samsung HDD and have 4 partitions. Ubuntu can't see Windows installed on my Desktop PC and says my Hard Drive is unallocated. It can't see my partitions. I used USB to install Ubuntu. 

If you want anymore information, ask me? What is the problem?

---

### Post by sudodus on 2012-01-18
Welcome to the Ubuntu Forums!

If you have four primary partitions you cannot create any more partition. A solution might be to delete one partition and make an extended partition, which can contain several partitions. But before you start doing something like that, backup your system to an external hard disk drive or at least backup your personal data (documents, emails, pictures, videos etc).

I suggest that you give us more information about your computer. A starting point could be to post the output of the following commands showing info about the partitions on your hard drive(s).

Run the commands from a live session booting from the installation CD or USB drive
```
sudo fdisk -lu
```
```
df
```

---

### Post by nipunshakya on 2012-01-18
Is your windows partitions primary or dynamic? Check it once from the disk management utility of your xp. Make sure that your partitions are **primary  **and not dynamic. Because if the partitions are dynamic, you cannot install ubuntu in it coz u will see unallocated space instead of your actual partitions.


Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-18
@swalihmz1: i would suggest you look at the following to repair or install grub to your external harddisk.
[http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/)
Hope that helps. If you have confusions, let us know.

Regards,WinuxUser

---

### Post by swalihmz1 on 2012-01-18
Thanks for your replay's, 

It's type shows basic. Not primary or dynamic. I didn't get Error 21.
Sudodus, i'm trying to install Ubuntu in the same partition of windows xp. I have enough space in that. And where i want to type those 2 commands that you gave me? It's the first time I'm using an OS other than Windows.

**Reinstalling or fixing Grub after error 21: **
 
[LIST=1]
[*]Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
[*]Open up a terminal and type **sudo su**
[*]Type **fdisk -l** and locate your Linux boot partition from the list **Example**: **sda1** or **hda1**
[*]Type **grub-install /dev/sdx** or **grub-install /dev/hdx** to reinstall or repair Grub!
[*]Reboot and test!
[/LIST]
I don't understand this. Where is terminal. Please help.

---

### Post by sudodus on 2012-01-18
> **swalihmz1 said:**
> Thanks for your replay's, 

It's type shows basic. Not primary or dynamic. I didn't get Error 21.
Sudodus, i'm trying to install Ubuntu in the same partition of windows xp. I have enough space in that. And where i want to type those 2 commands that you gave me? It's the first time I'm using an OS other than Windows.

**Reinstalling or fixing Grub after error 21: **
 
[LIST=1]
[*]Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
[*]Open up a terminal and type **sudo su**
[*]Type **fdisk -l** and locate your Linux boot partition from the list **Example**: **sda1** or **hda1**
[*]Type **grub-install /dev/sdx** or **grub-install /dev/hdx** to reinstall or repair Grub!
[*]Reboot and test!
[/LIST]
I don't understand this. Where is terminal. Please help.
Terminal can be either a fullscreen text 'terminal' that you get via  pressing 'ctrl + alt + F3' (at the same time) or a terminal window via  pressing 'ctrl + alt + t'.

You enter the commands writing the line(s) into the terminal and finish with the enter key, similar to what you do with the 'dos-prompt' or 'command' window in Windows. Then you can copy and paste the text into this message editor and tag it as code with the # icon at the top of this editor window.

---

### Post by nipunshakya on 2012-01-19
> **swalihmz1 said:**
> Thanks for your replay's, 

It's type shows basic. Not primary or dynamic. I didn't get Error 21.
Sudodus, i'm trying to install Ubuntu in the same partition of windows xp. I have enough space in that. And where i want to type those 2 commands that you gave me? It's the first time I'm using an OS other than Windows.

**Reinstalling or fixing Grub after error 21: **
 
[LIST=1]
[*]Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
[*]Open up a terminal and type **sudo su**
[*]Type **fdisk -l** and locate your Linux boot partition from the list **Example**: **sda1** or **hda1**
[*]Type **grub-install /dev/sdx** or **grub-install /dev/hdx** to reinstall or repair Grub!
[*]Reboot and test!
[/LIST]
I don't understand this. Where is terminal. Please help.
Sorry. I didn't know it was your first time. You mentioned that you want to install windows xp and linux on same partition. But, i strongly don't suggest you to do that. if you have separate partitions for your separate OSs, you will avoid problems regarding your booting and others in nearby future. Before installation, i would suggest you make changes to your partitions and move on with installation process. As time passes by, you can well partition according your requirements. Even i didn't like the ubuntu 11.10 and now i have just finished my installation of ubuntu 11.04 with fresh partitions.I don't know how much your hard disk's size is, but hope u get some rough idea about partitions as; 1 primary partition for win xp(size as u want), 1 primary NTFS partition for data sharing between win xp and linux, and finally 1 extended partition for linux so that you can have more logical partitions within it.
Inside your extended partition, u can create 3 logical partitions viz. a / for root(size around 10-15 gb), a /home (so that you don't have to worry about loosing preferences and keep your data in it, size as u want), and a swap area(mostly equal to size of your computer ram)

My personal suggestion,[B] don't install ubuntu and xp on same hard disk. Consider rearranging your partitions first and then go for installation.Goodluck.

And regarding your side by side installation, hope this fresh partition scheme will solve your issues with dual boot


Regards,WinuxUser
[/B]

---

### Post by swalihmz1 on 2012-01-19
Thanks WinuxUser. I have got a new problem now. On starting Ubuntu it shows prefix error. What is it?

---

### Post by nipunshakya on 2012-01-19
Did u get this error while booting from the LiveCD?One possible error might be that you had 32 bit version of your os and now booting a 64 bit? not sure about that reason though..

And yes, it would be nice if you explain what u did in your machine to install ubuntu...or the procedures you followed too....thanks

Regards,WinuxUser

---

### Post by swalihmz1 on 2012-01-19
I didn't get this error from LiveCD. I have downloaded its 32-bit version, not 64-bit.

---

### Post by nipunshakya on 2012-01-20
sorry mate. i cant spin my head around your prefix error. I previously assumed that you had ubuntu installed from wubi when u said u had both OS in your same partition of xp...(just a guess from me though.)
So,It would be nice if you post an image of the error you get..lets see what your actual error is..

And yes, it would be nice if you explain what u did in your machine to  install ubuntu...or the procedures you followed too....thanks


Regards,WinuxUser

---

### Post by sudodus on 2012-01-20
> **WinuxUser said:**
> sorry mate. i cant spin my head around your prefix error. I previously assumed that you had ubuntu installed from wubi when u said u had both OS in your same partition of xp...(just a guess from me though.)
So,It would be nice if you post an image of the error you get..lets see what your actual error is..

And yes, it would be nice if you explain what u did in your machine to  install ubuntu...or the procedures you followed too....thanks


Regards,WinuxUser
+1
The more you tell about your system, the greater chance that we can help :-)

---

### Post by ilmkidunya on 2012-01-20
> **swalihmz1 said:**
> I have all the requirements for XP and Ubuntu.I have XP already with me. Yesterday, i have downloaded Ubuntu 11.10. Now i want both the OS on my computer. On installing, i don't see the option of side to side installing the OS. I have Samsung HDD and have 4 partitions. Ubuntu can't see Windows installed on my Desktop PC and says my Hard Drive is unallocated. It can't see my partitions. I used USB to install Ubuntu. 

If you want anymore information, ask me? What is the problem?

Why don't you try the Vmware workstation for that

---

### Post by nipunshakya on 2012-01-20
> **ilmkidunya said:**
> Why don't you try the Vmware workstation for that

The Thread starter has said that he wants both OS in his machine and talks about partitions, which clearly states that he wants both as installations and not as a playstation.


:D:D:D

---

