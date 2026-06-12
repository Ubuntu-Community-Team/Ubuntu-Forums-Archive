---
title: "ubuntu installation error"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by maxwille on 2013-03-05
Hello,
 
I asked my friend to install ubuntu on my hard drive (the cd drive on my computer does not work), he took the hard drive and tried to install ubuntu on his computer, but he could not install it, he got all the files on the hard drive, but it does not boot up.
I tried re-installing ubuntu, but I can not delete the files from the hard drive and the other computer which I am using does not even recognize it!
Is there a way to delete the files?

Thank you in advance,
Victor

---

### Post by carl4926 on 2013-03-05
> [COLOR=#000000]I tried re-installing ubuntu, but I can not delete the files from the hard drive and the other computer which I am using does not even recognize it![/COLOR]

You are trying to re-install - so why was it you gave the HD to  a friend?
What OS are you using to work on the HD?

---

### Post by varunendra on 2013-03-05
Can you create a live usb and boot from it?

How are you trying to delete the 'files'?

If you can create a live usb ([unetbootin]("http://unetbootin.sourceforge.net/") is recommended tool for that), try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to fix the booting (assuming rest of the installation is complete and error free).

---

### Post by maxwille on 2013-03-05
[SIZE=2][FONT=Times New Roman][COLOR=#000000][COLOR=#222222][FONT=Verdana][SIZE=3]I ga[/SIZE][/FONT][/COLOR][/COLOR][/FONT][COLOR=#000000][COLOR=#222222][FONT=Tahoma][SIZE=3]ve the hard drive to my friend because I was not sure what to do (he told me to put the hard drive in another computer after I gave it to him)!
I am trying to install ubuntu 12.04.[/SIZE][/FONT][/COLOR][SIZE=3]
[FONT=arial]The computer is old and can not boot from a usb.
I am trying to get rid of all the filles and re-install ubuntu (The setup writes that I do not have enough space to install ubuntu).[/FONT][/SIZE][/COLOR][/SIZE]

---

### Post by varunendra on 2013-03-05
> **maxwille said:**
> I am trying to get rid of all the filles and re-install ubuntu
..and you are attempting that on the other computer from which you are posting this ? What OS does it have ?

Be careful if you attempt to install Ubuntu on the 'other' computer, because one wrong action can render that one unbootable as well !

How are you trying to install ubuntu on that drive now?

---

### Post by carl4926 on 2013-03-05
> **maxwille said:**
> [SIZE=2][FONT=Times New Roman][COLOR=#000000][COLOR=#222222][FONT=Verdana][SIZE=3]I ga[/SIZE][/FONT][/COLOR][/COLOR][/FONT][COLOR=#000000][COLOR=#222222][FONT=Tahoma][SIZE=3]ve the hard drive to my friend because I was not sure what to do (he told me to put the hard drive in another computer after I gave it to him)!
I am trying to install ubuntu 12.04.[/SIZE][/FONT][/COLOR][SIZE=3]
[FONT=arial]The computer is old and can not boot from a usb.
I am trying to get rid of all the filles and re-install ubuntu (The setup writes that I do not have enough space to install ubuntu).[/FONT][/SIZE][/COLOR][/SIZE]
Start the installer and select to erase everything and install ubuntu
[https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing](https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing)

---

### Post by maxwille on 2013-03-05
The computer from which I am posting this is another computer, the one I am using to install ubuntu is not really useful.
I started the installer but could not select erase everything and install ubuntu because it writes that my hard drive does not have enough space to install ubuntu and when I press continue nothing happens.

---

### Post by carl4926 on 2013-03-05
Boot the live cd
Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by varunendra on 2013-03-05
Which version are you trying to install ?

Not sure about 13.04, but 12.04 and 12.10 have Gparted included on the installation cd/dvd.

Run it and post back its screenshot while it is showing the drive in question.

To avoid confusion or any chance of accidental trashing of the current OS/bootloader, I'd recommend to disconnect the other drive from which the current computer boots.
Leave only the one connected which you want to install ubuntu upon. Then boot your live media, run gparted and try to delete -> recreate the partition(s) as you need them. In case of errors, post back its screenshot.

---

### Post by maxwille on 2013-03-05
The pictures of Gparted are on the next page.

---

### Post by maxwille on 2013-03-05
Here are the pictures of Gparted.

---

### Post by carl4926 on 2013-03-06
Similar issue here
[http://ubuntuforums.org/showthread.php?t=2103472](http://ubuntuforums.org/showthread.php?t=2103472)

---

### Post by maxwille on 2013-03-06
I looked at the thread but it did not solve my problem.
I still can not delete the partition with the files!

---

### Post by varunendra on 2013-03-06
Is this (/dev/zram0) the only device listed in the drop-down device list in gparted?

I think we do need to see output of **sudo fdisk -l** as well .. :|

---

### Post by maxwille on 2013-03-07
I opened terminal and typed "sudo fdisk -l" but it just wrote "ubuntu@ubuntu:~$ " and nothing happened.
I attached the screenshot.

---

### Post by carl4926 on 2013-03-07
So no HD is present
Please make sure it is properly connected by remaking the SATA cable connections and power connections

---

### Post by maxwille on 2013-03-08
I will try to re-connect the hard drive but, I think my computer does not recognize it!

---

### Post by carl4926 on 2013-03-08
> **maxwille said:**
> I think my computer does not recognize it!
Or it's Jeffed

---

### Post by maxwille on 2013-03-08
I found out that my computer does not recognize the hard drive, whene I unpluged it the filles were the same.
 I thought the filles were from the hard drive but they were from the cd!
I attached some screenshots...

---

### Post by carl4926 on 2013-03-08
Try connecting it to a different computer
Can you feel it spinning?

---

### Post by maxwille on 2013-03-08
Here is one more screenshot of gparted.
It was actually scaning the disc not the hard drive!
(The picture is Gparted without the hard drive)
Yes, it spins whene connected.
I will try to connect it to my laptop...

---

### Post by carl4926 on 2013-03-08
You might want to be looking to purchase a new HD IMO

---

### Post by maxwille on 2013-03-08
I tried to boot from a Sony vayo but it did not boot.
By the way can a hard drive stop working?

---

### Post by black veils on 2013-03-08
yes a hard drive dies eventually. a bump could break one.

---

