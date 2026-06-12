---
title: "How to copy a file to a Windows directory?"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by danny71 on 2007-05-10
Hello,

I would like to know how to copy a file from CD to a Windows directory that can be seen by Wine.

---

### Post by dannyboy79 on 2007-05-10
> **danny71 said:**
> Hello,

I would like to know how to copy a file from CD to a Windows directory that can be seen by Wine.

well, all you should have to do is put the cd in your cdrom within ubuntu, a little disc should pop up on your desktop, then simply double click it, then just drag and drop the file from the cd to your desktop or where ever you want to store it. if you need help running wine, there are plenty of threads within this forum to ehlp you with that. or you could just use the terminal.

ubuntu normally maps the cdrom to a folder called /media/cdrom or /media/cdrom0.

so this is the code you would use within a terminal (terminal is known as the command line interface)

```
sudo cp /media/cdrom/nameofexehere /home/username/
```

( NOTE: nameofexehere basically means that you should enter the exact name of the .exe file in it's place. ie text.exe would be: sudo cp /media/cdrom/test.exe /home/username/ )
This is if you want to make a copy of the file and store a copy of it within your user's home directory. by leaving no name on the end of the command, it'll copy the file and leave the same name as what it was on the cd. good luck

---

### Post by danny71 on 2007-05-10
The problem is that I cannot see the directory in C:\

Even if I can get the file from CD, I cannot find the destination folder!

---

### Post by dannyboy79 on 2007-05-10
> **danny71 said:**
> The problem is that I cannot see the directory in C:\

Even if I can get the file from CD, I cannot find the destination folder!

you'll need to be a little more specific. I have no idea what you mean?? please inform me exactly what you're trying to do so I can help.

OH, are you talking about the c:\ within wine? it's located within your users home dir under .wine/drive_c/ if I remember right.

---

### Post by danny71 on 2007-05-10
I want to copy a file from CD to a directory that can be seen only with Wine, because is a Windows application.

The destination folder should be C:\Program files\New Folder.

My question is simple:

How can I go to this folder with Ubuntu, to paste in it the file stored in the CD?

---

### Post by dannyboy79 on 2007-05-10
> **danny71 said:**
> I want to copy a file from CD to a directory that can be seen only with Wine, because is a Windows application.

The destination folder should be C:\Program files\New Folder.

My question is simple:

How can I go to this folder with Ubuntu, to paste in it the file stored in the CD?

i've already answered your question!  wine programs are stored within your user's home directory under .wine/drive_c/Program Files/New Folder. You would use the places pull down menu and pick Home, which will bring up nautilus, which is a file browser. you may need to show hidden files, which is under the view pull down.

i also don't appreciate your comment that your question is simple. You came here for help, i helped you and you make this condesending comment? NOT COOL. anyway, you should be set if you put the .exe file in the location I have informed you of. 

Also, you can run a wine and he windows .exe from anywhere, put it anywhere on your computer and just run

wine /path/program.exe

---

