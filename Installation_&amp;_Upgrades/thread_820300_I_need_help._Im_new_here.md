---
title: "I need help. Im new here"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Q-man on 2008-06-06
Ok im trying to get World of Warcraft on my linux. I have Ubuntu 8.04 and i installed wine 1.0. i got the .dll things i was supposed to get. i copied the files from my WOW DVD to a directory in my tmp folder named Wow. There is no installer.exe when i run commands. Im starting to doubt linux because of this thing. Can someone plz guide me through this??:(. it would make me proud when im able to raid with groups and take down my enemies in the game hehe.

---

### Post by wannadumpwindows on 2008-06-06
Have a look at this.

[https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29%7C%28warcraft%29%7C%28of%29]("https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29%7C%28warcraft%29%7C%28of%29")

---

### Post by Q-man on 2008-06-06
it says it needs to be copied from Wow Cd's. I only have that one DVD that has them all. when i open up the file. it has Installer mpq and Installer.mpq  2 and so on.....what do i do with that? i copied all of the files from the Game DVD to my directory but there is no installer.exe. its the same files from the cd.

---

### Post by wannadumpwindows on 2008-06-06
Did you pay very close attention to this section? Notce the part about getting the proper Installer.exe. It syays you need to mount the disc because it may be hidden otherwise.

Original WoW

The best method, if you have access to the installation discs is to copy the contents to your hard disk and run them from there:

    *

      Create a convenient directory ( 'wow_install' on your Desktop for example)
    *

      Copy all of the files from the first WoW CD to this new directory.
    *

      For each of the remaining WoW CD's, copy just the 'Installer Tome #.mpq' files. In the end, you should have the 'DirectX' directory, and the 'autorun.inf', 'installer.ico', 'Installer Tome.mpq', and 'Installer.exe' files from disc 1, and 'Installer Tome 2.mpq', 'Installer Tome 3.mpq', 'Installer Tome 4.mpq', and 'Installer Tome 5.mpq' from the remaining discs. Note that the 'Installer.exe' file on the first disc is different from the files of the same name on the subsequent discs; if you get the wrong one the install will fail with

      Unrecognized key "options". (AttributeParser::Parse)

    *

      Note that on some WoW DVD's the installer executable is hidden and you need to mount the disc with the 'unhide' option. To do this type in a terminal:

  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

    *

      Start the installation by opening a terminal and running these commands:

       cd /<path-to-directory>/
       wine Installer.exe

      Replace <path-to-directory/> with the right path to the directory where you copied all the files above.

Some dialogs during installation may appear blank or garbled, and the installer may even hang for up to 5 minutes at 100% CPU, while appearing to be doing nothing. Simply wait and click next when possible.

Note: If you have not already done so, you may want to install [WWW] Microsoft's proprietary fonts, because they can solve some text related graphical glitches during installation.

---

### Post by Q-man on 2008-06-06
ok about the Wow Cd's???? What does that mean? when i bought World of Warcraft it came with one cd......thats confusing me. i did all of the steps but there is no installer.ico,or installer.exe, or directx directory....

---

### Post by wannadumpwindows on 2008-06-06
Sounds like you just have a DVD version. I would assume all the same files should be on the one disc. If not, even though it may take forever, you can download the discs from the wow site and get the files you need from there. I don't have a disc here to look at, or I'd be more help, sorry.

---

### Post by wannadumpwindows on 2008-06-06
Do you happen to have a dual-boot set-up alongside windows? If you do, you can just copy over your entire WoW folder from your windows partition and you should be set. It mentions that further down on the documentation, that might be even easier yet . . . . .

---

### Post by Q-man on 2008-06-06
No. I accidently partitioned the whole disk to ubuntu. one of my friends have windows xp and he has World of Warcraft on it. can i use a jump drive to copy the files over from there?

---

### Post by Q-man on 2008-06-06
i started to download Wow from the sites its at 45 % right now i started like at 8:00 last night hehe its taking a while

---

### Post by wannadumpwindows on 2008-06-06
I don't see why not. If you can't get the disc figured out, that would be another way to go. I wish I could throw a disc in my puter to help you out. There shouldn't be any reason that you can't copy them over. As long as you own a copy of the game and all that good stuff, I don't see why there should be any problem.

---

### Post by wannadumpwindows on 2008-06-06
> **Q-man said:**
> i started to download Wow from the sites its at 45 % right now i started like at 8:00 last night hehe its taking a while

Ouch. That's pretty harsh. Is it one big file, or each individual disc? If it's only one huge download, you're probably gonna end up with the same disc you already have. Which would be a H-U-G-E waste of time. But anything you can try might be some help.

---

