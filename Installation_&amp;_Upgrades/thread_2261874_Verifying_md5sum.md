---
title: "Verifying md5sum"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by Morten_Fjellheim on 2015-01-21
Like the tiltle says, this is about verifying the md5sum! First of all, the guide says open a terminal, am i guessing correct if i think it means command prompt? Second question, i am using english command but running on a system set with norwegian text. Is it posible that the computer doesnt understand the command because of this, should i change the system so that it has english language set?

---

### Post by sudodus on 2015-01-21
1. Yes command prompt alias terminal window alias command line interface (CLI).

2. Most commands work with the same options and parameters independent of the selected language and keyboard setting. But the output of some commands will be in your language.

Try and find out :-)

You find several links with tips at this wiki page

[https://help.ubuntu.com/community/CategoryCommandLine](https://help.ubuntu.com/community/CategoryCommandLine)

---

### Post by Morten_Fjellheim on 2015-01-21
One more question. I have checked the md5sum with the program "winMd5sum" and the sum is the same. Is this enough to verify the iso file? The procedure i have used is explained in the "[B]MD5SUM on Windows[SIZE=5]"[/SIZE][SIZE=2] in this guide [/SIZE][COLOR=#222222][FONT=Verdana]https://help.ubuntu.com/community/HowToMD5SUM#Check_the_iso_file. Is this sufficient or do i have to go through any of the other steps to verify the iso integrity?

The guide says this should be used on the cd but i have used it on the iso file in the downloads directory. Does it work on the iso file as well?[/FONT][/COLOR][/B]

---

### Post by sudodus on 2015-01-21
Yes, I think you can rely on that Windows tool and it should be enough for the iso file. [COLOR=#696969]I use md5summer in Windows, it is probably similar to the tool you use.[/COLOR]

Burning to a DVD is prone to fail. Burn at the lowest possible speed. Check with the checking tool at the boot screen (an option below 'Install Ubuntu'). This is to check that also the the install media is correct after burning.

Flashing to a USB pendrive is more likely to succeed (so only if you have problems you can check at the boot screen).

---

### Post by Morten_Fjellheim on 2015-01-21
Alright, i have chosen the usb stick method. Should i download the iso file directly to it, or is it enough to send the file from the downlodas directory and to the usb stick?

---

### Post by ajgreeny on 2015-01-21
No you do not just copy the iso file to a USB; you must use a special tool to transfer the iso fle and make the USB bootable.  What tool you use will depend on the OS you are using and as I know nothing of windows except that **unetbootin** is available for both Windows and Linux, that is the tool I suggest you use if Windows is all you can use at the moment.
[http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe](http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe)

---

### Post by sudodus on 2015-01-22
Unetbootin should work for you. If you want or need more details, see this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

