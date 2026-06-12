---
title: "Moving apps from ubuntu pc to another"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by zombieguy85 on 2013-01-16
Heres my setup my laptop i bring to work to download apps and play with ubuntu my computer at home has ubuntu on it as well same with same version. 

Is there a way to clone my apps and settings to the desktop so i can use the apps at home my internet connection sucks at home so i wanna download games at work and bring it to the house .

PS i live in the country so my internet is POOP
Thanks :p

---

### Post by ibjsb4 on 2013-01-16
I think your talking about this:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en)

I also use Zotero to view web pages off line.

[http://www.zotero.org/](http://www.zotero.org/)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=view+web+pages+off+line&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=view+web+pages+off+line&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by zombieguy85 on 2013-01-16
> **ibjsb4 said:**
> I think your talking about this:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en)

I also use Zotero to view web pages off line.

[http://www.zotero.org/](http://www.zotero.org/)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=view+web+pages+off+line&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=view+web+pages+off+line&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Im sorry what i ment is i wanna copy apps that i have on my laptop like games or apps that i download on ubuntu .  So that i can copy them to my desktop. Lets just pretend my internet at home does not work

---

### Post by MG&amp;TL on 2013-01-16
> **zombieguy85 said:**
> Im sorry what i ment is i wanna copy apps that i have on my laptop like games or apps that i download on ubuntu .  So that i can copy them to my desktop. Lets just pretend my internet at home does not work

How have you installed said games/apps? If you just downloaded and saved them in your home folder, just copy them across. If you installed them via a debian package or via a source compile, it's a bit more complicated.

---

### Post by zombieguy85 on 2013-01-16
> **MG&TL said:**
> How have you installed said games/apps? If you just downloaded and saved them in your home folder, just copy them across. If you installed them via a debian package or via a source compile, it's a bit more complicated.

Well they were downloaded thru deb on the software manager

---

### Post by MG&amp;TL on 2013-01-16
> **zombieguy85 said:**
> Well they were downloaded thru deb on the software manager

Well...if they were on the software manager, they're likely cached. Assuming you have no internet on the target machine, on the machine with the apps, look in:

File System ('/')
->'var'
-->'cache'
--->'apt'
---->'archives'

Now you'll see a whole lot of ".deb" files. Select the ones you want (probably only a couple), and copy them to a USB stick or other media.

Then put them on your target PC, and double-click on them to open in the software manager. 

Note that this is a hit-and-miss approach (for instance, the installed programs may need other programs or libraries to function correctly). If you have a decent internet connection anywhere, there are [better ways to do it.]("http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline")

Have fun!

---

### Post by ibjsb4 on 2013-01-16
Maybe "dpkg-repack" is what your looking for.

[http://www.debianadmin.com/put-an-unpacked-deb-file-back-together-using-dpkg-repack.html](http://www.debianadmin.com/put-an-unpacked-deb-file-back-together-using-dpkg-repack.html)

[http://www.webupd8.org/2010/02/repack-deb-packages-for-installed.html](http://www.webupd8.org/2010/02/repack-deb-packages-for-installed.html)

[https://www.google.com/search?client=ubuntu&channel=fs&q=dpkg-repack&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=dpkg-repack&ie=utf-8&oe=utf-8)

Its in the software center.

---

