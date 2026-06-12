---
title: "I need help installing tar.bz2"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by monkeystuner on 2008-10-03
I am wanting to install Cube 2. I just searched for a free linux game and this popped up so I figured I would try it. I downloaded the file and it is compressed as a tar.bz2. I extracted it and now I am not sure where to go from here.This folder and its contents were created as a result of the extraction

dave@dave-desktop:~/sauerbraten$ ls
bin_unix/ 
 CVS/ 
 data/ 
 docs/
 packages/ 
 README.html 
 sauerbraten_unix 
 src/

I looked around online and I kept finding 'use ./configure' so I guess that is the next step but what do I configure and how? Some step by step instructions would be appreciated. Thank you.

Dave

---

### Post by tspan on 2008-10-03
Just double-click on "sauerbraten_unix" icon or type in terminal:```

cd ~/sauerbraten
./sauerbraten_unix

```

Make sure that it is executable first - right-click on "sauerbraten_unix" -> Properities ->  Permissions -> Allow executing file as program.

Also, check this [thread]("http://ubuntuforums.org/showthread.php?t=898140") for more info on installing the game in Ubuntu.

---

### Post by Sef on 2008-10-03
Read [Compiling Software]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by monkeystuner on 2008-10-03
Well.. thanks for your help... I figured it out.. I did what you said only to find that I was missing so libraries needed so I got them and all is well Thanks

Dave

---

