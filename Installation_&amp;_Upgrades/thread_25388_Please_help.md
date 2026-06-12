---
title: "Please help"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by ZetSabre on 2005-04-10
I've tried to install Ubuntu a few times now. While "Installing the base system," there is a "debootstrap error," and it can't retrieve bsdutils. Even when I try to skip this step for a while, many other steps do not work. I have tried booting ubuntu and kubuntu several timeswith the same problem every time. For some reason, the live CD works fine, but i'd like to do a full install. Does anyone know what this problem is, and/or how to fix it?

PS: I could never get warty to work either.
      And I don't think it's the CD, I recorded it at 4x speed.

---

### Post by orion_114 on 2005-04-10
Did you check the MD5 checksum of the disc ?
Check out this utility:
[http://www.fourmilab.ch/md5/](http://www.fourmilab.ch/md5/)
It will allow you to check the integrity of your downloaded iso file.

---

### Post by bjeezus on 2005-04-10
[QUOTE=ZetSabre]I've tried to install Ubuntu a few times now. While "Installing the base system," there is a "debootstrap error," and it can't retrieve bsdutils. Even when I try to skip this step for a while, many other steps do not work. I have tried booting ubuntu and kubuntu several timeswith the same problem every time. For some reason, the live CD works fine, but i'd like to do a full install. Does anyone know what this problem is, and/or how to fix it?

PS: I could never get warty to work either.
      And I don't think it's the CD, I recorded it at 4x speed.[/QUOTE]
 I was having the same error yesterday. Somone on the forum suggested I download a program called Jigdo and use that to find a working copy of the corrupted files. There's also a disk integrity checker on Hoary's install disk set-up itself, run that and make sure you take down the path of the corrupted files(s).

What I did was download [Jigdo](http://atterer.net/jigdo/) and started downloading some Hoary files from the jigdo file on the ubuntu site (you can find it in the list that has the Bit Torrent files at the bottom of the download page). After one or two files were downloaded, I stopped it and went into the jigdo folder. You'll find a folder there the same name as the file you started to download. Open that and navigate into the folder that has the "pool" directory and delete everything in it. Then copy all those working files from the iso (delete the currputed one/ones) over to that debian folder and start jigdo again. It will recongize the already present files and search for the ones you're missing. Once that's done, it checks the integrity of the iso. You know what to do from there...

Hope this helps.

---

### Post by Magneto on 2005-04-11
man what's the deal with these images????????????

i downloaded the live dvd and burned it - the live aspect works fine no errors at all beautiful
so i go to install and alsa errors and aspell errors  basically a bunch of corrupted files and the beautiful red screen of frustrastion 
debootstrap error

so i download an hoary cd iso- bad checksum :\
so i check the md5 on the original hoary dvd iso - its perfect- please no burn speed remarks
what's the deal? im not wasting more DVDs or CDs on this until I'm sure I can get it to work-
let me try to burn it in linux - had a similar issue with fedora a few years back - i will use a rw this time

---

### Post by Magneto on 2005-04-11
pretty stupid- burn the dvd with nero in windows - corrupt files even with a good md5 
burn it with k3b  comes out fine

I would really like to know the difference in how the discs are being written

reminds me again of why I hate winblows

---

