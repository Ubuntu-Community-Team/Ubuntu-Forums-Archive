---
title: "Java Fixed in Beryl/Desktop Effects Here..."
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by leinuz.basher on 2007-07-29
1.Fixed Java in Beryl
Edit ~/.bashrc and add the following at the beginning of the file:

export AWT_TOOLKIT=MToolkit 

2.Fixed Java in Beryl
Open the environment file in the etc directory. To do this just open a terminal and type the following:-

gksudo gedit /etc/environment

Now the file is open add the line below the path line then save and exit:-

AWT_TOOLKIT=”MToolkit”

Thats it, happy coding

3.If Using One is not enough Use Both...

                                                       leinux.Meivince

---

### Post by mocoloco on 2007-09-18
Worked for me just in .bashrc. I've been looking for something like this.  Thanks!

Edit: I mean it did NOT work for me editing .bashrc but did adding the line in the environment file.

---

