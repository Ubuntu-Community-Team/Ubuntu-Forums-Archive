---
title: "dreamweaver wine issue"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by kiddd_ on 2011-04-29
Hello everybody ! 

 I decided to post a new thread regarding this issue because even If I read other similar posts , either I could not find exactly what I was looking for , either it didn't really help me.

After many hours I managed to install photoshop cs5 and dreamweaver cs3 ( I would have liked cs5 better though ) on my system. Photoshop did not give me such a big headache , dreamweaver did.In my Applicagtions-->Wine-->Programms--> I can see Photoshop , but I cannot see dreamweaver. I installed dreamweaver cs3 and dreamweaver 8 beacause I thought that maybe it was some software issue and decided to try both of them, still with both I have the same problem. So if I type " locate -i dreamweaver.exe " it can find it's location but I CAN'T ACCESS IT no matter what ! :(

If I copy-paste the location in shell ,  the software runs fine , but as I  can't access the folder in order to create a shortcut on my desktop as well as in my wine-->Programms tab.

kiddd@kiddd-VGN-FW56M:~$ sudo su
root@kiddd-VGN-FW56M:/home/kiddd# locate -i dreamweaver.exe
/home/kiddd/.local/share/Trash/files/Dreamweaver.CS3/Keygen/Crack/Dreamweaver.exe
/root/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3/Dreamweaver.exe
/root/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe
root@kiddd-VGN-FW56M:/home/kiddd# ^C
root@kiddd-VGN-FW56M:/home/kiddd# "/root/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3/Dreamweaver.exe"

As I type this Dreamweaver runs fine.
I tried to access the folder manually ( open root folder as admin -- though , nothing there )

gksudo (I write the location -- nothing )

Alt+F2 ( still -- nothing )

I'm really running out of ideas and I'm having a killing headache.

I'd really appreciate any help ! Thank you before hand !

---

### Post by sg1efc on 2011-04-29
Not sure if this is the cause of your problem, but some of us have discovered some type of bug in Ubuntu 11.04 that prevents Wine from correctly loading some programs.  I'm sure people are already working to fix this bug and an update will probably be available soon.   :)

---

### Post by ZazzyE on 2011-04-29
> **kiddd_ said:**
> 
/home/kiddd/.local/share/Trash/files/Dreamweaver.CS3/Keygen/Crack/Dreamweaver.exe

Might I suggest that instead of piracy, have you explored the packages that Linux offers?  

Here's a thread that'll give ya some ideas on what programs are available, compatible, and offer you the freedom to do with them as you wish:  [http://ubuntuforums.org/showthread.php?t=1524582](http://ubuntuforums.org/showthread.php?t=1524582)

GIMP is a possible alternative to Photoshop, if you find it necessary in the future.

Other than that, I personally can't offer much help with WINE. It can be temperamental, so I can understand a "try before you buy" approach, depending on what [http://www.winehq.org/](http://www.winehq.org/) has to say about that particular program's usability in WINE.  However, you have to understand that emulation and cracks tend to be slow processes.  Piling both on top of each other isn't likely to give you much of a usable permanent solution.

---

### Post by kiddd_ on 2011-04-30
Managed to access the folder. By entering root folder as admin and doing a stupid thing like hitting ctrl+h to see hidden folders..DONE !.So now I can access the folders I wanted to access in the first place....though..STILL it does not let me copy the .exe file or create a shortcut even with full privileges. What to do ?

---

