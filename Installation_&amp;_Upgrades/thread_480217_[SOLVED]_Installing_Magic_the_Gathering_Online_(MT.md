---
title: "[SOLVED] Installing Magic the Gathering Online (MTGO) with WINE"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Slimo on 2007-06-21
I am trying to install the MTGO program using WINE (0.9.39) in Ubuntu 7.04.
The package unzips itself but then comes up with the error:

"Failed to create font resource sserife.fot fontname sserife.fot!!!"

I have seen a few posts advising people to change their .wine/config files - but I cannot seem to find this file!

Any help would be appreciated

---

### Post by Slimo on 2007-06-24
Bump

---

### Post by net_vagabond on 2007-06-27
I have the same problem when trying to install it and would also appreciate some help if possible.

---

### Post by Diabolis on 2007-07-03
I tried to install mtgo and I got the same error. I went to my .wine folder and noticed that the fonts folder (windows fonts) was empty, so I made a copy of a ttf file (ms sans serif.ttf) from a computer with windows xp installed. I placed 2 copies into my fonts folder (wine folder) and renamed each one with the name of the files that appeared in the error message (including the extension fot and fon).  then I tried to run setup.exe which was already in this folder .wine/drive_c/windows/temp.

Seems like it fixed it, but now I got an error message that says "could not find a kickimgs directory". What I did then was to install mtgo in windows xp and after that make a copy of the installation files and just place them in wine program files folder. I think this could work but when I try to execute magic.exe a new error appears... it says "could not find a required directory kickimgs. PLease check that the proper CD is in the drive". I looked for the kickimgs directory and it exists in the main folder of the installation.

I noticed that in the installation folder a I have a magic1.exe file too. I tried to execute it and I got this error "Cannot acces file default/huff.dat. Error=2. PLease make sure the Magic Online V2.0.074.2028 CD-ROM is in the drive". I supposed that default folder is the Magic Online folder, I checked it and I do have a huff.dat file...

I'm thinking that I could fool the system and make it think that I have the CD in the drive, that could fix it, but I don't know how to do that.

---

### Post by Diabolis on 2007-07-18
Just in case someone misses it: [http://ubuntuforums.org/showthread.php?p=3041675#post3041675]("http://ubuntuforums.org/showthread.php?p=3041675#post3041675")

---

### Post by Slimo on 2007-08-30
Thanks everyone!
I recently had to do a fresh install and got MTGO working from scratch by installing the msttcorefonts and copying these fonts to my .wine folder.
Then, using the terminal, I navigated to the folder where the MTGO install file was and used the command "wine mtgodl2.exe".

After this the extractor started running and the setup.exe file ran once it had finished.  No font problems or install problems!!

---

### Post by Slimo on 2007-08-30
Sorry 1 more thing I should mention:
This didn't work for me with the latest version of wine.  From the wine archives I installed version 0.9.29 and it worked fine.  Other versions of wine may work as well but from my experience 0.9.44 didn't work and 0.9.29 did

---

