---
title: "wine doesn't work ? please help me to fix the problem that I have with Wine..thanks"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by alialen on 2010-07-12
I have ubuntu 10.04, and I have to design a website for my friend,  therefore, I downloaded Dreamweaver cs5 from adobe website. I found out  that I have to install Wine in order to be able to install .exe files on  Obuntu, after wine installation I edited the properties of the .exe  (dreamweaver) file (execution allowing and opening the program with  Wine) . when i click on the file there is a default for extracting adobe  Dreamweaver  "C:\users\alialen\Desktop\Adobe CS4\Dreamweaver" so i  choose the default folder and then it starts loading the file and  extracting it. After it is done loading in about 2 minutes i get a  program error in which it says : 

[B]"The program setup.exe has encountered a serious problem and needs to  cloes. We are sorry for the inconvenience. 
  
This can be caused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running  this application 
If this problem is not present under Windows and has not been reported  yet, you can report it at http://bugs.winehq.org"[/B]

I wanted to make sure that I installed Wine correctly therefore, I  removed it completely from the directory, and installed it through the  terminal . 

I tried to explain the problem in details and I am very new to ubuntu so  please if you know what causing the problem or how to fix the problem, I  would appreciated to read your comments, please explain your answer and  comments in details. 

Thank you.

---

### Post by lechien73 on 2010-07-12
According to the WineHQ app database, Dreamweaver CS5 gets a "Silver" rating for installing on Wine. The information says that it doesn't install correctly on Lucid, but there is a workaround:

> I copied the program files, common files, and user appdata from a vista installation. I also imported the registry keys for adobe in current user and local machine /software.

The program needs the c++ 2008 redistributable installed, but it must be downloaded and installed from microsoft. The one in winetricks does not work. odbc32.dll and odbcint.dll are required as well. gdiplus.dll must also be manually copied into the /system folder.

You can find the information here: [http://uri.tl/9](http://uri.tl/9)

---

### Post by gottsc33 on 2011-03-08
I am currently having the same issue.  Were you able to solve it, the instructions above were unsuccessful for me?

---

### Post by DexterBrylle on 2011-06-28
i have the same issue. I installed this copy of dreamweaver cs5 from a video in [http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

---

