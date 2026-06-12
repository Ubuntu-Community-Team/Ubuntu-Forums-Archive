---
title: "Install kde on ubuntu"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by saeedmar on 2010-03-11
Hi
 I want to have a KDE desktop on my ubuntu OS, I mean that I want to have a switching system between Gnome and KDE! And I don't know how to do that? And if you are writing an answer please tell me if it will make problem for me or not?
Thanks

---

### Post by zvacet on 2010-03-11
In terminal type 

```
sudo apt-get install kubuntu-desktop
```

Restart after installation is finish and you will see option to choose desktop.

---

### Post by saeedmar on 2010-03-11
> **zvacet said:**
> In terminal type 

```
sudo apt-get install kubuntu-desktop
```Restart after installation is finish and you will see option to choose desktop.


Hi 
Thanks for your kindness and answering my question
I've just downloaded the CD version of kubuntu from [www.kubuntu.org](www.kubuntu.org), is it possible to install KDE from that CD and have Gnome and KDE both? :p

---

### Post by Sef on 2010-03-11
>  I've just downloaded the CD version of kubuntu from [www.kubuntu.org]("http://www.kubuntu.org/"), is it  possible to install KDE from that CD and have Gnome and KDE both? :razz:

That would overwrite Ubuntu, so you would be left with just Kubuntu.  To have both on there, read [Psychocats kde]("http://www.psychocats.net/ubuntu/kde").  

> Quote:
 	 	 		 			 				 					Originally Posted by **zvacet** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8949046#post8949046") 				
 				In terminal type 

 	Code:
 	sudo apt-get install kubuntu-desktop 


Actually the correct code is 

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

You always want to have your repositories up-to-date before installing any software.

---

### Post by uRock on 2010-03-11
I know that when I added LXDE I just installed the LXDE package, not the desktop version. Doing it this way allows you to choose which desktop environment you want to use when logging in.

Here is a great tutorial on how to add KDE to Ubuntu. Please read it. [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

> **Sef said:**
> You always want to have your repositories up-to-date before installing any software.
Especially being there is a dpkg update today.

---

### Post by saeedmar on 2010-03-12
> **iRock said:**
> I know that when I added LXDE I just installed the LXDE package, not the desktop version. Doing it this way allows you to choose which desktop environment you want to use when logging in.

Here is a great tutorial on how to add KDE to Ubuntu. Please read it. [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)


Especially being there is a dpkg update today.

Thanks Man
it was really nice, and the most easiest way, really thanks

---

