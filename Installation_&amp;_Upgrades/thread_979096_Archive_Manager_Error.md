---
title: "Archive Manager Error"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Trevness on 2008-11-11
Fixed it Read BELOW

---

### Post by Trevness on 2008-11-11
Well when i download something..like i try to download Winzip i downloaded it and when i click the .exe button of Winzip to install it or whatever..it says this.

> **Trevness said:**
> [/home/trevs/Desktop/Winzip/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/trevs/Desktop/Winzip/Setup.exe or
          /home/trevs/Desktop/Winzip/Setup.exe.zip, and cannot find /home/trevs/Desktop/Winzip/Setup.exe.ZIP, period.

Any Help? thanks and if this is in the wrong section..please let me know and if there are moderators move this please..

---

### Post by cariboo on 2008-11-11
You can not install Windows executables on Linux, nor do you need to. IF you need to open a zip file just double click it and File Roller will extract it. To create a zip file just right-click on a file and select create archive. Almost all the programs you will ever need are available at Applications-->Add/Remove Programs. Make sure you have set show: All available Open Source applications, and then when you find a program you want to install put a check mark beside  it and click apply changes. You can mark as many programs for installation as you want, and when you done selecting, click apply changes.

---

### Post by Trevness on 2008-11-11
Noo i dont think you understood or i understood what you said or i said..ok Il give pics this time

Here is the File i want to like...install its a .exe file

[IMG]http://i173.photobucket.com/albums/w73/dehpunisher/TheFile.png[/IMG]

And here is the Error it gives me when i double click it

[IMG]http://i173.photobucket.com/albums/w73/dehpunisher/TheError.png[/IMG]

---

### Post by Roinator on 2008-11-11
Sorry Trevness, cariboo is right, exe files are by no means linux files, they are windows only.  You may be able to install and run xfire if you install wine first though.  I have heard it can be done. [Maybe this will help.]("http://ubuntuforums.org/archive/index.php/t-554629.html")

---

### Post by Trevness on 2008-11-11
whats Wine?

im downloading Call of Duty 4 right now...Will i even be able to play it? cause im having trouble..

Oh yeah..my computer isnt Linux tho.. lol its Windows XP Home edition

---

### Post by Roinator on 2008-11-11
[Wine's Website]("http://www.winehq.org/")
[Wine wiki]("http://en.wikipedia.org/wiki/Wine_(software)")

It is basically a program you can install on ubuntu to run windows programs (not all windows programs though, check [here]("http://appdb.winehq.org/") to see which ones are tested to work).  I think CoD4 works, but I don't really know.

What do you mean by you're not running linux? Your screenshots are of ubuntu aren't they.  Are you dual booting with XP and ubuntu?

If you check the link I gave in the firs post it gives you the necessary commands to install Wine.

---

### Post by Trevness on 2008-11-11
Yes im on Ubuntu Sorry lol

I dont understand what to do..its like i need Step by Step instructions such as

1.
2.
3.
 :( my first day of This Ubuntu and i love it..i really want xfire and i want to play CoD4

I extracted the Wind Folder thing to my desktop..How do i even get this Wine thing to open...all i see is a bunch of files in the folder..what do i double click?

---

### Post by Roinator on 2008-11-11
It's alright, I stated off completely over my head for sure lol.

1. First open a terminal (Alt + F1)
2. Next type in the code below
```
sudo apt-get install wine
```
It will then prompt you for your password.  When you type it in it won't appear in the terminal.  Once you are done typing your password hit ENTER.
This should install wine on your computer.

3. Go [here]("http://ubuntuforums.org/showthread.php?t=879071").  It's a thread telling you how to install CoD 4 once you have wine installed.

You can delete that stuff you just added to your desktop by the way.

---

### Post by Trevness on 2008-11-11
HAAAAA lol im stupid....I actually just right clicked my desktop and clicked Create Launcher Then clicked The type: Application in Terminal so i made the Terminal thing asked me for my password n stuff and it installed Wine

Thanks :D I did put the code in ^

---

### Post by Roinator on 2008-11-11
Oh wow, my bad. Wrong short cut.  Go to Applications -> Accessories -> Terminal

EDIT:
Never mind then.

P.S.

Learning to use a new OS is difficult sometimes. You can always find help on this forum though.  That said, research your topic before making a new thread. Often you will find your question has been asked before.

---

