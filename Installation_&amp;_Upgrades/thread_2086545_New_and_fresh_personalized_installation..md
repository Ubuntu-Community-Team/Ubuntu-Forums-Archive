---
title: "New and fresh personalized installation."
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by eddie3000 on 2012-11-21
Hello there! 
I am not an expert linux person, and I have been using ubuntu variants for a few years now. 
I like to re-install my OS every six months or so, I try new versions for a while and, if I don't like them, re-install previous versions again and wait for another newer version.
To save time downloading and installing my favourite apps again and again, what I do is simply copy the contents in /var/cache/apt/archives to another medium, and then install them using the software center after a fresh install. Now I guess this isn't a very good way to do things as I sometimes get errors and some apps don't work, while others do. 
How can I save all the installed programs with all the files and dependencies so I can reinstall them quickly without an internet connection? And also make it possible to install them independently of the flavour of ubuntu I'm trying?
Thank you.

---

### Post by ibjsb4 on 2012-11-21
One way would be aptoncd, its in the software center.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by eddie3000 on 2012-11-21
Thank you ibjsb4. I have checked it and yes, it seems to be what I want. I have succesfully created an iso of the packages I have, but I do not have a cd drive on my laptop, and APTonCD does not accept iso images. It stays stuck hunting for a CD drive . So I guess this won't work for me at the moment and I do not plan having a cd drive in my laptop. Apart from that little detail, it looks like a very useful program for computers with a dvd-cd drive ;-)
:)

---

### Post by ibjsb4 on 2012-11-21
There are other options.  I can't give you the details since my backup plan includes internet access, but look here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+all+installed+packages+without+internet&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+all+installed+packages+without+internet&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[https://www.google.com/search?client=ubuntu&channel=fs&q=backup+all+installed+packages+without+internet+ubuntuaptoncd&ie=utf-8&oe=utf-8#hl=en&sugexp=les%3B&gs_nf=3&gs_mss=backup%20all%20installed%20packages%20without%20internet%20ubuntua&tok=6GP4sfn3wrF3Xzhg28HaVw&pq=backup%20all%20installed%20packages%20without%20internet%20ubuntuaptoncd&cp=53&gs_id=1m9&xhr=t&q=backup+all+installed+packages+without+internet+ubuntu&pf=p&client=ubuntu&hs=GJB&tbo=d&channel=fs&sclient=psy-ab&oq=backup+all+installed+packages+without+internet+ubuntu&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=b71fae27fb82e0b9&bpcl=38897761&biw=935&bih=904&bs=1](https://www.google.com/search?client=ubuntu&channel=fs&q=backup+all+installed+packages+without+internet+ubuntuaptoncd&ie=utf-8&oe=utf-8#hl=en&sugexp=les%3B&gs_nf=3&gs_mss=backup%20all%20installed%20packages%20without%20internet%20ubuntua&tok=6GP4sfn3wrF3Xzhg28HaVw&pq=backup%20all%20installed%20packages%20without%20internet%20ubuntuaptoncd&cp=53&gs_id=1m9&xhr=t&q=backup+all+installed+packages+without+internet+ubuntu&pf=p&client=ubuntu&hs=GJB&tbo=d&channel=fs&sclient=psy-ab&oq=backup+all+installed+packages+without+internet+ubuntu&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=b71fae27fb82e0b9&bpcl=38897761&biw=935&bih=904&bs=1)

---

### Post by eddie3000 on 2012-11-21
Thanks for your reply. Apart from the terminal command line option (which I think I have used in the past) I haven't seen many more graphically pleasing options. Just copying the /var/cache/apt folder doesn't seem such a bad idea after all. I am just curious to see other methods just in case there is a "perfect" method for me. 
I tried mounting the iso image that APTonCD provides, but I get an error message in Ubuntu's software center when I double click the aptoncd metapackage. 
Thanks anyway, I'll carry looking around if nobody comes up with another way. 
Cheers!:)

---

### Post by ibjsb4 on 2012-11-21
I should of known that Synaptic Package Manager could do this (and Keryx).

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

---

### Post by eddie3000 on 2012-11-21
Wow! How silly can one be! It's been in front of me for years and I hadn't realized. Thanks a bunch. I prefer this to APTonCD. Thanks.:lolflag:

---

### Post by ibjsb4 on 2012-11-21
> **eddie3000 said:**
> Wow! How silly can one be! It's been in front of me for years and I hadn't realized. Thanks a bunch. I prefer this to APTonCD. Thanks.:lolflag:

Same for me  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

