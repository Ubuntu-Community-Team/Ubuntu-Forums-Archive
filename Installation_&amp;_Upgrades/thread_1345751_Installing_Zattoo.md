---
title: "Installing Zattoo"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Eterniam on 2009-12-04
Hi, I've had Ubuntu for about 2 weeks now, and it's my first non-microsoft operating system, so I'm quite new to installing programs on it. I've installed most of the stuff I need with the software centre of synaptic package manager, but now I want to install Zattoo.

I tried installing the windows EXE with WINE, but I got an error saying

"The program Zattoo1.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org."

So I went to winehq.org and I found this post about installing it:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17343](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17343)

However, I'm only on the first line and I'm already having trouble :)

I enter "sh winetricks flash ie6 dotnet20" into the terminal (I think I'm meant to be entering it there), and it comes up with "sh: Can't open winetricks". If you could tell me what to enter and where, that'd be a great help because I don't understand the wine post. :) Cheers

---

### Post by phillw on 2009-12-04
> **Eterniam said:**
> Hi, I've had Ubuntu for about 2 weeks now, and it's my first non-microsoft operating system, so I'm quite new to installing programs on it. I've installed most of the stuff I need with the software centre of synaptic package manager, but now I want to install Zattoo.

I tried installing the windows EXE with WINE, but I got an error saying

"The program Zattoo1.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org."

So I went to winehq.org and I found this post about installing it:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17343](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17343)

However, I'm only on the first line and I'm already having trouble :)

I enter "sh winetricks flash ie6 dotnet20" into the terminal (I think I'm meant to be entering it there), and it comes up with "sh: Can't open winetricks". If you could tell me what to enter and where, that'd be a great help because I don't understand the wine post. :) Cheers

Hi, you need to first install WINE -->  [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Regards,

Phill.

---

### Post by Lampi on 2009-12-04
- there used to be a linux application from zattoo, it no longer works
- please visit [http://zattoo.com/](http://zattoo.com/)
- create an account (it's free)
- watch zattoo live in your browser with the flash plugin

---

### Post by davidmohammed on 2009-12-04
... if you want to use zattoo in your browser you still need to install the tech preview version of zattoo first.

As to winetricks - [download]("http://www.kegel.com/wine/winetricks") winetricks first before following the sh winetricks instructions - remember use the latest version of wine first (from winehq) - the ubuntu repository version is out of date.

---

### Post by Eterniam on 2009-12-04
Sorry! I'll clarify what I meant. I have installed Zattoo by opening the windows binary (with the stable version 1.0.1 of WINE already installed), but when I tried to run Zattoo I got the error I posted before. I posted in the installation forum because I thought Zattoo needed to be reinstalled, because the installation instructions at WineHQ are very different to how I installed it. At the moment, Zattoo is not installed on my computer, because I removed it to try installing how WineHQ instructed, I just don't understand how to do that.

I have the latest version of WINE already. I have winetricks saved as "winetricks" on my desktop, and it's marked to "Allow executing file as program". However, sh winetricks still gives me a message saying "sh: cannot open winetricks". Anyone know why?

---

### Post by davidmohammed on 2009-12-04
You need the latest wine version from WineHQ - 1.33.  The "stable" 1.0.1 is not good enough.

As to your sh winetricks - I presume you are within the ~/Desktop folder before you type "sh winetricks"?  Stupid question I know - but just checking...

---

### Post by Eterniam on 2009-12-04
Haha, it wasn't a stupid question at all :) It worked after I updated WINE to 1.1.33 and was in the ~Desktop folder. Now the next instruction is to add a key to the WINE registry:
3. regedit
4. create the key HKCU\AppEvents\Schemes\Apps\Explorer\Navigating\.current

Unfortunately I can't find any information on how to create a key. Anybody know where I can find out how to make that key?

---

### Post by phillw on 2009-12-04
> **Eterniam said:**
> Haha, it wasn't a stupid question at all :) It worked after I updated WINE to 1.1.33 and was in the ~Desktop folder. Now the next instruction is to add a key to the WINE registry:
3. regedit
4. create the key HKCU\AppEvents\Schemes\Apps\Explorer\Navigating\.current

Unfortunately I can't find any information on how to create a key. Anybody know where I can find out how to make that key?

Hi - I don't have knowledge of WINE, but I know the forum area for all things wine --> [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)  Pop over to that section & they'll get you up and running.

regards,

Phill.

---

### Post by Eterniam on 2009-12-04
Ok, thanks for your help guys!

---

