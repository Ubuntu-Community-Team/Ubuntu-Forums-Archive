---
title: "Apache openoffice"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by Jim_Dodds on 2016-01-29
How do I install apache open office rpm?

---

### Post by ajgreeny on 2016-01-29
The simple answer is that you don't.

Ubuntu uses .deb packages not .rpm so you can either forget about Apache OpenOffice completely and use LibreOffice instead which is in the repos and installed by default in many of the *ubuntu family OSs, or if you must have AOO you go to [http://www.openoffice.org/download/](http://www.openoffice.org/download/) and choose the appropriate 32 or 64bit version of the 4.1.2.

Why do you want OpenOffice instead of LibreOffice?

---

### Post by mastablasta on 2016-01-29
you don't .

1. you can use Libre Office.

2. if you really must have Apache open office follow instructions for installing indo Debian based systems: [http://www.openoffice.org/download/common/instructions.html#linux-deb](http://www.openoffice.org/download/common/instructions.html#linux-deb)

---

### Post by vasa1 on 2016-01-29
And I don't know whether having both installed may cause problems. If you're on Ubuntu, you'll probably have LibreOffice already installed.

---

### Post by Jim_Dodds on 2016-01-29
Apparently for some reason LibreOffice will not open my school documents for some reason

---

### Post by ajgreeny on 2016-01-29
> **Jim_Dodds said:**
> Apparently for some reason LibreOffice will not open my school documents for some reason
In which case it is likely that AOO will not open them either as LibreOffice is a fork of OpenOffice from a few years ago.

What file type are those that will not open?

---

### Post by yancek on 2016-01-29
A specific example might help someone help you.  What exactly happens when you try to open the 'school document' and what type of document is it?

---

### Post by vasa1 on 2016-01-29
And if it doesn't open in LibreOffice, the chances are pretty slim that Apache Openoffice will oblige.

---

### Post by Jim_Dodds on 2016-01-29
Libreoffice is now working. I now have another problem. I tried installing yesterday apache openoffice rpm and it halfway installed. I then tried to install it with the deb file. It said installed but was nowhere to be found. I now have a file on my desktop named en-US and it is locked. It says I need to have root privileges and I can't delete it. When I try to delete it and change it to root it is grayed out. How do I delete this file on my desktop? It is driving me nuts!! I tried unistalling it and I think it partially unistalled.

---

### Post by ajgreeny on 2016-01-29
I have no idea what you mean by the rpm version half installed; I would not expect it to be installed in any way at all, but I admit I have never tried to do that in Ubuntu.

However if the en-US file is just a single file on your desktop you can remove it with command ```
sudo rm Desktop/en-US
```

Be very careful when using **sudo rm** that you get the whole command exactly correct or you might do huge damage to your system by removing some system files.  Therefore it is best to copy my command above by highlighting it in the usual way then middle clicking in terminal with your mouse; that pastes the temporary buffer into terminal for you, which can be a huge time saver.

For future reference remember that you can not copy from, nor paste to terminal with **Ctrl+C** and **Ctrl+V**; you have to use **Ctrl+Shift+C** and **Ctrl+Shift+V** instead.

---

### Post by Jim_Dodds on 2016-01-31
It won't remove it. It says it is a directory

I got it. I guess for directory's you have to [COLOR=#000000][FONT=Ubuntu Mono]sudo rm -r Desktop/en-US thanks for the help.[/FONT][/COLOR]

---

### Post by ajgreeny on 2016-02-01
Great! 
Please mark as SOLVED from the Thread Tools menu at the top.

---

