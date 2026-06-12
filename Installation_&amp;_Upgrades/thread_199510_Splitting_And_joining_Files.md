---
title: "Splitting And joining Files"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by PoisoN2003 on 2006-06-18
Hey im not sure where to post this but im wondering how can i split and join files easly like winrar does?? is there something like that for linux (splitting files at like 90mb a piece)

---

### Post by Mirrorball on 2006-06-18
Yes, 7zip does that.

---

### Post by SlugO on 2006-07-26
It might be helpful to give you some advice on using 7zip from the command line since Linux frontends don't have options for creating multi volume 7zips (or any other archives).

First install 7zip:```
sudo apt-get install p7zip
```

If you want to have your files split to 90M then I'd use a command like this: ```
7z a -mx9 -ms=on -v90M stuff.7z folder
```Stuff.7z is the name of the archive (you can also use .zip but .7z compresses them better) and folder is the name of the folder (or file) you want to pack. Now I'm not sure how many programs can handle multi volume archives created by 7zip, atleast file-roller can't. That's why you have to extract them with: ```
7z x stuff.7z.001
```In Windows you can extract them with the [graphical 7-Zip]("http://www.7-zip.org/").

---

### Post by PoisoN2003 on 2006-07-27
thx man its very usefull

---

### Post by Johnny B on 2008-06-03
if you cant use the command 7z you need the code
```
sudo apt-get install p7zip-full
```

---

