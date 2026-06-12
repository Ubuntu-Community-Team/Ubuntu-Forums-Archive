---
title: "Upgrade Ubuntu Server to Ubuntu Desktop"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by rbaleksandar on 2007-07-20
I have installed Ubunut Server 6.04, because it's faster than the Ubuntu Desktop installation. Now I want to upgrade my server to a desktop Ubunutu. Is it possible and if "yes" - then how?
Oh, and please give me a detailed info, because I am a novice:-)

---

### Post by 5-HT on 2007-07-20
> **rbaleksandar said:**
> I have installed Ubunut Server 6.04, because it's faster than the Ubuntu Desktop installation. Now I want to upgrade my server to a desktop Ubunutu. Is it possible and if "yes" - then how?
Oh, and please give me a detailed info, because I am a novice:-)

You can install the ubuntu-desktop metapackage which will bring everything included in a default ubuntu install with it.
```
 sudo apt-get install ubuntu-desktop 
```
cheers,

---

### Post by Motoxrdude on 2007-07-20
> **5-HT said:**
> You can install the ubuntu-desktop metapackage which will bring everything included in a default ubuntu install with it.
```
 sudo apt-get install ubuntu-desktop 
```
cheers,
Yuep, and if you want to install kubuntu do
```
sudo apt-get install kubuntu-desktop
```
Xubuntu?
```
sudo apt-get install xubuntu-desktop
```
cheers.

---

### Post by lunamystry on 2007-07-20
> **Motoxrdude said:**
> Yuep, and if you want to install kubuntu do
```
sudo apt-get install kubuntu-desktop
```
Xubuntu?
```
sudo apt-get install xubuntu-desktop
```
cheers.

well this is some wonderful news to me!! but I have a question : I have a gnome desktop thingy and I would like to try out KDE thus my question is if I install kubuntu what will happen to the programs that I already have? Will it affect my data? 

:guitar:Thank you for your time. (man! I can sing :-D
)

---

### Post by Motoxrdude on 2007-07-20
> **lunamystry said:**
> well this is some wonderful news to me!! but I have a question : I have a gnome desktop thingy and I would like to try out KDE thus my question is if I install kubuntu what will happen to the programs that I already have? Will it affect my data? 

:guitar:Thank you for your time. (man! I can sing :-D
)

Nope, it doesn't hurt it at all! When you login just select KDE from your sessions menu.

---

### Post by Martje_001 on 2007-07-20
Nope. All your files will be the same (in your homefolder). When you login you can choose gnome or KDE btw.

edit: too late :P

---

### Post by rillip on 2007-07-20
Please keep in mind that this is not really the best way to do this.  The server edition is likely going to have packages like apache, mysql, etc. installed taht you won't need and possibly have daemons enabled/ports allowed that might leave you more vulnerable.  I don't know a whole lot about the server install itself, but it's geared toward a server, so it makes sense that there are going to be a lot of things a desktop doesn't need.

Also note that running an app of DE X in DE Y will be slower; i.e. running Gaim in KDE is going to be slower than running Gaim in Gnome, due to the libraries needed to load, etc.

---

### Post by lunamystry on 2007-07-20
> **rillip said:**
> Please keep in mind that this is not really the best way to do this.  The server edition is likely going to have packages like apache, mysql, etc. installed taht you won't need and possibly have daemons enabled/ports allowed that might leave you more vulnerable.  I don't know a whole lot about the server install itself, but it's geared toward a server, so it makes sense that there are going to be a lot of things a desktop doesn't need.

Also note that running an app of DE X in DE Y will be slower; i.e. running Gaim in KDE is going to be slower than running Gaim in Gnome, due to the libraries needed to load, etc.

well I dont think that will be a problem, I dont even use gaim. 8-[. How do i uninstall KDE if i dont like it? if i like it i'll get kubuntu gusty gibbon whwn it comes out. Which reminds me, I have a Prof. Called George Gibbon. :o:mrgreen:

thank you very much for your time, now i dont need to install opensuse to try KDE.

---

### Post by rillip on 2007-07-20
Uninstalling is a bit more difficult.  Check out this page on how to purge kde if you decide not to keep it.  [http://doc.gwos.org/index.php/Install/remove_(K,X,Ed)ubuntu-desktop_packages]("http://doc.gwos.org/index.php/Install/remove_(K,X,Ed)ubuntu-desktop_packages")  Uninstalling kubuntu-desktop might try to remove things you need - I seem to recal I tried removing Xubuntu by doing ```
sudo apt-get remove xubuntu-desktop
``` and the first thing it tried to remove was apt get.. :o  So check out the instructions above.

---

### Post by lunamystry on 2007-07-20
> **rillip said:**
> Uninstalling is a bit more difficult.  Check out this page on how to purge kde if you decide not to keep it.  [http://doc.gwos.org/index.php/Install/remove_(K,X,Ed)ubuntu-desktop_packages]("http://doc.gwos.org/index.php/Install/remove_(K,X,Ed)ubuntu-desktop_packages")  Uninstalling kubuntu-desktop might try to remove things you need - I seem to recal I tried removing Xubuntu by doing ```
sudo apt-get remove xubuntu-desktop
``` and the first thing it tried to remove was apt get.. :o  So check out the instructions above.

Thanks, I think i would have used the remove kubuntu command aswell,I'll give the link a read.

LINK DOES NOT WORK!!! and now i desperately need it, i cant play multimedia on my PC and i think its because of KDE so i wanna install it and see if its KDE or did i do something wrong.

---

### Post by Motoxrdude on 2007-07-20
Use```
sudo aptitude install *ubuntu-desktop
```
this makes it so you can un-install *ubuntu-desktop by doing
```
sudo aptitude remove *ubuntu-desktop
```
Other wises you will still have all the applications that come with kubuntu, xubuntu, etc.

---

### Post by rillip on 2007-07-23
What do you mean the Link does not work?  It's not loading, or you're getting an error when trying to follow the instructions?  What error?

---

