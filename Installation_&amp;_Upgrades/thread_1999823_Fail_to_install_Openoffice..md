---
title: "Fail to install Openoffice."
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by GwibberFooey on 2012-06-08
I have recently migrated to Ubuntu 12.04 and I have mostly got it configured to my liking.  But in one aspect I am still running into major major problems. 

I tried to install Openoffice by going: 

   sudo add-apt-repository ppa:upubuntu-com/office

   sudo apt-get update

   sudo apt-get install openoffice


Now I have icons in the Applications menu (I am using Classic Gnome) that indicate Openoffice is installed, including Base, Calc, Draw, Impress, Math and Writer.  But when I select one of them then the application fails to load.

---

### Post by OpenSourceRules on 2012-06-08
I believe it is now Libreoffice.  Open Office was the old name, I believe.

---

### Post by wilee-nilee on 2012-06-08
If you want openoffice you need to completely purge libreoffice, including doing a file search to get every single file, and remove it from the .config in home.

Libreoffice really has more to offer at this point I think

Both doc writers have some same files and have to be completely wiped to move from one to the other.

---

### Post by GwibberFooey on 2012-06-08
On my previous operating system I had Openoffice not Libreoffice.  When I brought over my office documents to my new system, the spreadsheets (.ods) and the text (.odt) files worked fine in Libreoffice but the database (.odb) files did not work.  That is why I chose to uninstall Libreoffice and try to install Openoffice. 

I have no preference between Openoffice and Libreoffice.  My goal is to be able to use my files.  So I would be just as happy to get Libreoffice to read my .odb format database as I would be if Openoffice did it.

---

### Post by wilee-nilee on 2012-06-08
> **GwibberFooey said:**
> On my previous operating system I had Openoffice not Libreoffice.  When I brought over my office documents to my new system, the spreadsheets (.ods) and the text (.odt) files worked fine in Libreoffice but the database (.odb) files did not work.  That is why I chose to uninstall Libreoffice and try to install Openoffice. 

I have no preference between Openoffice and Libreoffice.  My goal is to be able to use my files.  So I would be just as happy to get Libreoffice to read my .odb format database as I would be if Openoffice did it.

Understandable, you just have to do a full purge to get openoffice.

I don't really know about the docs needing read though sorry. ;)

---

### Post by GwibberFooey on 2012-06-08
I am willing to work with Libreoffice.  From what I have read today it seems like it is better than Openoffice.  Does Libreoffice have the ability to read and modify a .odb database that was created in an older version of Openoffice?

---

### Post by Enigmapond on 2012-06-08
Yes it should do fine. Have you tried it? You already have Libre installed by default. Just give it a go and you will have your answer.

---

### Post by GwibberFooey on 2012-06-08
The .odb database did not work in Libreoffice.  That was the reason why I wanted to install Openoffice.

---

### Post by Enigmapond on 2012-06-08
Well it saves as .odb just the same and I have some very old openoffice db's  that open just fine. You tried by opening Librebase and then opening an existing odb file?

---

### Post by GwibberFooey on 2012-06-09
It works because I started Libreoffice before the database file.  But it still does not work if I select the database file without first launching Libreoffice Base.  Clicking on the database file results in a error window saying "Archive type not supported."  Therefore I realized it is trying to use Archive Manager to open the file.  So I went to Properties for the database file and set the default application for opening this and all files of type .odb to Libreoffice Base.  Problem solved.

---

