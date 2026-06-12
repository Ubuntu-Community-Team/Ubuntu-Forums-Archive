---
title: "Installing StarCraft &quot;no CD&quot; patch"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by coolethan on 2008-11-01
instructions i read on how to install the starcraft no cd patch are as such: you need to copy the install.exe file for both starcraft and broodwar expansion and move them into the StarCraft installation directory as well was rename them to "StarCraft.mpq" and "BroodWar.mpq"

```
cp /media/cdrom/install.exe ~/.wine/drive_c/Program\ Files/StarCraft.mpq

cp /media/cdrom/install.exe ~/.wine/drive_c/Program\ Files/Starcraft/BroodWar.mpq
```

these two codes should take the starcraft and broodwar install.exe files and copy them and rename them appropriately. i typed in the first code into the terminal with the regular starcraft cd in the cd drive and i'm pretty sure it worked because i didn't get any error messages when it finished but when i put in the second code with the broodwars disk in the cd drive i get this error message

cp:cannot create regular file `/home/ethan/.wine/drive_c/Program Files/Starcraft/BroodWar.mpq':Premission denied

how do i fix this i presume it worked for the starcraft disk because the curser sat there for while blinking and the cd drive made the regular spinning noises when it reades a disk and after a while the regular directory tag thing popped up again awaiting my next comand.****

---

### Post by prshah on 2008-11-01
> **coolethan said:**
> 

```
cp /media/cdrom/install.exe ~/.wine/drive_c/Program\ Files/StarCraft.mpq

cp /media/cdrom/install.exe ~/.wine/drive_c/Program\ Files/Starcraft/BroodWar.mpq
```


I think you're missing a path; in the second command, you are trying to create a BroodWar.mpq file in a directory called Starcraft; does this directory exist? (Note the case!)```
ls -l ~/.wine/drive_c/Program\ Files
ls -l ~/.wine/drive_c/Program\ Files\Starcraft
ls -l ~/.wine/drive_c/Program\ Files\StarCraft

```

---

### Post by coolethan on 2008-11-01
oops! the first code should be 

```
cp /media/cdrom/install.exe ~/.wine/drive_c/Program\ Files/Starcraft/StarCraft.mpq

and the second

cp /media/cdrom/install.exe ~./wine/drive_c/Program\ Files/Starcraft/BroodWar.mpq
```

and prshah i think you made a small mistake with your codes should they not be 

....\ Files/Starcraft? instead of ....\ Files\Starcraft

When i type in: ls -l ~/.wine/drive_c/Program\ Files/Starcraft i get this

```
ethan@Nertwab:~$ ls -l ~/.wine/drive_c/Program\ Files/Starcraft
total 1027072
-rw-r--r-- 1 ethan ethan    557310 2008-07-25 17:34 battle.snp
-rwxr-xr-x 1 ethan ethan    417792 2008-11-01 04:10 bnupdate.exe
-rw-r--r-- 1 ethan ethan       189 2008-11-01 04:10 bnupdate.log
-rw-r--r-- 1 ethan ethan  23847431 2008-11-01 03:48 BrooDat.mpq
-rw-r--r-- 1 ethan ethan     27648 2008-11-01 03:48 BroodUnits.doc
-r-xr-xr-x 1 ethan ethan 352296960 2008-11-01 04:02 BroodWar.mpq
-rw-r--r-- 1 ethan ethan        66 2008-11-01 03:49 BwarInst.log
drwxrwxrwx 2 ethan ethan      4096 2008-10-30 13:28 characters
-rw-r--r-- 1 ethan ethan     92672 2008-10-30 13:24 EditLocal.dll
drwxrwxrwx 2 ethan ethan      4096 2008-11-01 04:14 Errors
-rwxr-xr-x 1 ethan ethan    662474 2008-10-30 13:24 InstCC.exe
-rw-r--r-- 1 ethan ethan     92375 2008-01-07 18:17 License.html
-rw-r--r-- 1 ethan ethan        23 2008-01-09 18:55 License.txt
-rw-r--r-- 1 ethan ethan     52224 2008-10-30 13:24 Local.dll
drwxrwxrwx 7 ethan ethan      4096 2008-11-01 04:10 maps
-rw-r--r-- 1 ethan ethan   1084068 2008-11-01 04:10 Patch_rt.mpq
-rw-r--r-- 1 ethan ethan     34144 2008-11-01 04:10 patch.txt
-rw-r--r-- 1 ethan ethan      1229 2008-10-30 13:24 Readme.cnt
-rw-r--r-- 1 ethan ethan     32482 2008-10-30 13:24 Readme.hlp
-rw-r--r-- 1 ethan ethan    315392 2008-10-30 13:24 Riched20.dll
drwxrwxrwx 3 ethan ethan      4096 2008-10-30 14:01 save
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditDEU.loc
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditENU.loc
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditESP.loc
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditFRA.loc
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditITA.loc
-rw-r--r-- 1 ethan ethan     65536 2008-07-25 17:34 SEditPTB.loc
-rw-r--r-- 1 ethan ethan     95232 2008-11-01 03:48 Smackw32.dll
-rw-r--r-- 1 ethan ethan    127767 2008-07-25 17:34 standard.snp
-rwxr-xr-x 1 ethan ethan   1220608 2008-07-25 17:34 StarCraft.exe
-r-xr-xr-x 1 ethan ethan 601389682 2008-11-01 03:57 StarCraft.mpq
-rw-r--r-- 1 ethan ethan  66184591 2008-10-30 13:24 StarDat.mpq
-rw-r--r-- 1 ethan ethan      3483 2008-11-01 03:48 StarEdit.cnt
-rwxr-xr-x 1 ethan ethan   1016320 2008-07-25 17:34 StarEdit.exe
-rw-r--r-- 1 ethan ethan    176681 2008-11-01 03:48 StarEdit.hlp
-rw-r--r-- 1 ethan ethan    409600 2008-07-25 17:34 storm.dll
ethan@Nertwab:~$
```

note that it clearly shows a BroodWar.mpq file at the top and a StarCraft.mpq file near the bottom so both files obviously ended up where they should have and with the right rename but i still got that error message.

however when i type: ls -l ~/.wine/drive_c/Program\ Files/StarCraft (note capital C) i get a "cannot open ls -l ~/.wine/drive_c/Program\ Files/StarCraft file or directory does not exist"

---

### Post by prshah on 2008-11-01
> **prshah said:**
> ```
ls -l ~/.wine/drive_c/Program\ Files
ls -l ~/.wine/drive_c/Program\ Files\Starcraft
ls -l ~/.wine/drive_c/Program\ Files\StarCraft

```

> **coolethan said:**
> 
how would i find out if the 'starcraft' file exists because when i search or try to find it i can't so what does that mean?

The three commands posted above will give you an idea of whether or not the directory exists, it's spelling and case.

---

### Post by coolethan on 2008-11-01
> **prshah said:**
> The three commands posted above will give you an idea of whether or not the directory exists, it's spelling and case.

i edited my previouse post, sorry i typed that in before i went and tried out those codes but they did work. check my edited post to see what i got for each of those codes of yours please.

---

### Post by prshah on 2008-11-01
> **coolethan said:**
> 
....\ Files/Starcraft? instead of ....\ Files\Starcraft
```
<snip>
-r-xr-xr-x 1 ethan ethan 352296960 2008-11-01 04:02 BroodWar.mpq
<snip>
-r-xr-xr-x 1 ethan ethan 601389682 2008-11-01 03:57 StarCraft.mpq
ethan@Nertwab:~$
```

note that it clearly shows a BroodWar.mpq file at the top and a StarCraft.mpq file near the bottom so both files obviously ended up where they should have and with the right rename but i still got that error message.

No; no mistake; the point being that I wanted to check if a file called "Starcraft" existed.

Now to your problem; the BroodWar file already exists and it's read-only (r-x) permissions, so cp is not able to overwrite it. You can see it's not the file you tried to copy by just comparing file sizes with StarCraft.mpq in the listing. Since you copied the same "install.exe" file to both files, the file sizes should match.

To resolve this, add writeable permissions to BroodWar.mpq and then run the cp command again.```
chmod u+w ~./wine/drive_c/Program\ Files/Starcraft/BroodWar.mpq
cp /media/cdrom/install.exe ~./wine/drive_c/Program\ Files/Starcraft/BroodWar.mpq

```

---

### Post by coolethan on 2008-11-02
Thanks that worked wonders, i still don't understand why i was able to do it for StarCraft.mpq and not BroodWar.mpq. they're going into the same file so shouldn't i have admin rights for both? Now i tried installing the patch found here [http://us.blizzard.com/support/article.xml?articleId=21149&categoryId=2716&parentCategoryId=&pageNumber=1]("http://us.blizzard.com/support/article.xml?articleId=21149&categoryId=2716&parentCategoryId=&pageNumber=1")
but i get a window popping up that sais

Invalid data file version number rez\CDversion.txt
Program version:17
Datafile version:0

---

### Post by hellfire34 on 2009-05-28
this is great, but how do we do it without the "install.exe" file -.- its weird i always would install it but this time around i didnt... then guess what i lost both disc's original and brood war during my moving of house... so basicly i need a isntall.exe file and i think i'll be fine.. cany anyone help me out?..
 
thanks kieran.
 
 
 
](*,)

---

### Post by coolethan on 2009-05-28
> **hellfire34 said:**
> this is great, but how do we do it without the "install.exe" file -.- its weird i always would install it but this time around i didnt... then guess what i lost both disc's original and brood war during my moving of house... so basicly i need a isntall.exe file and i think i'll be fine.. cany anyone help me out?..
 
thanks kieran.
 
 
 
](*,)
that sucks man, other than the cd i don't know where you can get that file. torrent's are great try that

---

