---
title: "Ubuntu vs. Kubuntu"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by aristotlewilde on 2006-06-29
Ok, so I got fancy and tried installing the Kubuntu Desktop so I could choose between Gnome and KDE.  

Everything works, but I miss the old Ubuntu splash screen while teh system is initializing. Now I am stuck with the blue Kubuntu screen.  

How do I get back to the original Ubuntu?

---

### Post by Dr. Nick on 2006-06-29
i think this will work, not sure though. If you attempt it please check to make sure it is not removing anything critical

Open synaptic and search for "usplash" make sure usplash is installed, and mark kubuntu-artwork-usplash for removal.


That seems like a logical solution, hope it works.

---

### Post by aristotlewilde on 2006-07-01
This is the screen I am trying to change.  I've removed Kubuntu and KDE altogether...  Doesn't help.

[IMG]http://www.geocities.com/aristotle_wilde/IMG_0094.JPG[/IMG]

---

### Post by aysiu on 2006-07-01
Try ```
sudo update-alternatives --configure usplash-artwork.so
```

---

### Post by user1397 on 2006-07-01
here's the exact solution to your problem ( I had the exact same problem not too long ago.)

Open a terminal and copy and paste this: ```
sudo update-alternatives --config usplash-artwork.so
```  Choose usplash-default.so for the brown Ubuntu splash.
Then do```
sudo dpkg-reconfigure linux-image-`uname -r`
```and you're set

EDIT: you didn't have to remove kde for this little problem.  if you want to try it out again, follow my guide down in my signature called "install kde, gnome, or xfce"

---

