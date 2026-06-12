---
title: "Real Player 10 Installation"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by leshat on 2006-10-04
I have downloaded Real Player 10 to my desktop. The file is in binary format. How do I install?
TIA
Les

---

### Post by bwald on 2006-10-04
What do you mean its in "binary format?"  A good way of telling what type of file something is to use the "file" command.

```
file theFile
```

This will tell you what type of file it is.  If its says something like

> Bourne shell script text executable

its probably an executable file.  They way to run a file like that is to type:

```
./theFileName
``` 

at the terminal (Applications/Accessories/Terminal)

---

### Post by onioneater36 on 2006-10-04
To to a terminal shell window and navigate to the directory it is in (in your case...)

cd /home/youruserid/Desktop

and then you need to make the .bin file executable on your system using...

sudo chmod 777 realplayer.bin

Then execute the file using...

./realplayer.bin

and follow the insructions.  I chose to install in the /opt/RealPlayer directory.  You may want to use realplayer from the repositories instead.  It is much easier to install and more importantly, uninstall.

Go to the Ubuntu Guide website at...

[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

Read the section on adding additional repositories FIRST and then do the section on installing realplayer.  This is a much better method.  If you try to do "sudo apt-get install realplay" without changing your repositories first, it will not work.

---

### Post by ajgreeny on 2006-10-04
You must like doing it the difficult way, unless you just want to practice the harder way for the sake of increasing your linux know-how.  As onioneater says, the easy way is to enable other repositories and then use apt to install it.

---

### Post by navneeth on 2006-10-04
The link to the instructions are right below the download button in Real's site.

---

### Post by leshat on 2006-10-04
Thanks for your help. As a newbie I took the easy route and downloaded from the repository!!!
I must say that although this is a steep learning curve for  me - I am enjoying  every minute!
Thanks to you all.
Les

---

### Post by onioneater36 on 2006-10-04
Keep with it.  I have tried Linux many times in the past and gave up as many.  With Ubuntu, it has stuck.  Ubuntu makes it so you can set up your machine to easily do many useful things.  While you are having fun with the useful stuff (web, multimedia, office apps, etc) you can spend more productive time learning the configuration, programming, troubleshooting and all the other stuff that is good to know.  I still have Windows on my main rig, but when I get to be an Ubuntu Expert, odds are that will go too except a small partition for gaming :mrgreen:

---

### Post by leshat on 2006-10-04
Slight problem!! Perfect pictures but NO sound??
I have checked the volume control is on for the PC speakers.
Any suggestions?
TIA

---

