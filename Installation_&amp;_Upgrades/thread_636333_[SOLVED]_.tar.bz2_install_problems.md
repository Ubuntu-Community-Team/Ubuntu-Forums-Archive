---
title: "[SOLVED] .tar.bz2 install problems"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by antisocialist on 2007-12-09
i am trying to install a theme from gnome-look.com and it is in .tar.bz2

i renamed it to easy.tar.bz2 so its easier in terminal, did the following

```
cd ~/Desktop
tar -jxvf easy.tar.bz2
./configure
```

and got the following
bash: ./configure: No such file or directory

how do i install it i got it from
[http://www.gnome-look.org/content/show.php/..%3A%3AThe+Dark+Theme%3A%3A..?content=66005](http://www.gnome-look.org/content/show.php/..%3A%3AThe+Dark+Theme%3A%3A..?content=66005)

thanks in advance,

antisocialist

---

### Post by antisocialist on 2007-12-09
bump

---

### Post by logos34 on 2007-12-09
if you unzipped it, then cd into the resulting folder, i.e.

user@user-desktop:~/Desktop$ cd easy 
user@user-desktop:~/Desktop/easy$ ./configure

---

### Post by gpredrag on 2007-12-09
You should probably change to directory that you have just extracted before you run configure.

---

### Post by antisocialist on 2007-12-09
i extracted with archive manager and renamed i know have ~/Desktop/easy i did cd ~/Desktop/easy and then ./configure and it said not found, is there a special way you install themes in .tar.bz2 format?

---

### Post by logos34 on 2007-12-09
ok, I just had a look at the package...you just need to unzip/untar, it's not a source pkg...then grab the window borders, controls, panels and whatnot through Appearance/Look and Feel (system>prefs>control center).  REad the gnome help:

System>help&support>Customizing your computer>customizing other aspects of the Desktop>Configuring Your Desktop>Look and Feel>theme preferences

---

### Post by antisocialist on 2007-12-09
k got it, how do i turn off emerald so i can use these themes?

EDIT: turned off emerald, but i wish i still had desktop effects... anyway, thanks so much i have a killer theme now ill attach a picture of it.

---

### Post by logos34 on 2007-12-09
> **antisocialist said:**
> k got it, how do i turn off emerald so i can use these themes?

EDIT: turned off emerald, but i wish i still had desktop effects... anyway, thanks so much i have a killer theme now ill attach a picture of it.

wow, that's sharp! I'm getting back into darker thjemes lately (running studio now, very happy with it)...it kinda reminds me of the noir royale I have on my win desktop...the applique top panel really gives it a nice touch

---

### Post by antisocialist on 2007-12-09
if u want i can give u the files of it, shouldnt take me long, only like 1mb, prob best if i email to you so i dont use up ubuntu servers

check out new one, has a killer bg too

---

