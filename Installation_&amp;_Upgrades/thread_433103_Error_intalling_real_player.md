---
title: "Error intalling real player"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by karlos66 on 2007-05-04
Help

I am still finding my way around with linux and I am not altogether sure as to what I can download. I have Ubuntu 7.04 and have just downloaded realplayer 10 gold.bin from their web site, which from what I can gather is suitable for linux but I keep getting the following error message can any one explain what I am doing wrong. "Cannot open /home/karlos/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file." is there another program that I need to download first? :confused: 

Karlos

---

### Post by chicken101 on 2007-05-04
Right click the bin file and go in the permissions tab to make sure you have execution rights over the file.  Open the terminal and run  realplayer 10 gold.bin...just drag and drop the file into the terminal window.

---

### Post by karlos66 on 2007-05-05
thanks I gave that a go but got the following message
Cannot open /home/karlos/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.
any more ideas I really am struggling with linux:(

---

### Post by wawa on 2007-05-10
In a console, go to directory where the bin file is downloaded, then:
```

$ chmod 755 RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin
```

and follow the instructions. When asked where to install:
```
$ /usr/bin
```

---

### Post by nanceconfer on 2007-05-10
Ummm. . . OK, I have no idea what a console is, although I do know that I saw the bin notation when I downloaded RealPlayer. Is there a "Downloading RealPlayer for dummies" section here? 

Thanks.

Nance

---

### Post by wawa on 2007-05-10
Console or Terminal, where you type commands. You can find it in main menu > System or ALT+F2 and type "konsole" if you are using kubuntu

---

