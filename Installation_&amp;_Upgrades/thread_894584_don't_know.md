---
title: "don't know"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by nik1990 on 2008-08-19
i want to download the game pirates of the Caribbean online so some guy gave me this site [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622) but i don't know how to download from it if some one knows i will be happy if you will tell me

---

### Post by oldos2er on 2008-08-19
> **nik1990 said:**
> i want to download the game pirates of the Caribbean online so some guy gave me this site [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622) but i don't know how to download from it if some one knows i will be happy if you will tell me

 That isn't a download site, it's the Wine applications database. I suggest you use Google to locate a download site.

---

### Post by manishtech on 2008-08-19
> **nik1990 said:**
> i want to download the game pirates of the Caribbean online so some guy gave me this site [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3622) but i don't know how to download from it if some one knows i will be happy if you will tell me
The link which shows there is actually a page which keeps track whether the application can be run using wine or not. Download the game as you did it for Windows and run it under wine.

**Install wine:** Open Application>Accessories>Terminal and type
***sudo apt-get install wine***

Its a big file, may take time to download depending on your internet speed. Now to launch the game using wine, download the installer file in your home directory. If the filename is say setup.exe, then
goto terminal and type **wine setup.exe** and the installer will be launched. 

If this fails, try installing using root privileges, using the command **sudo wine setup.exe** , though running with root is dangerous, should be used as last resort.


N.B. Its a kind request to please choose a proper topic title for your post. Titles such as "Dont know", "help", "please help me" don't attract much people to read your post.

---

