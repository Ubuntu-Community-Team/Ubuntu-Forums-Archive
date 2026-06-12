---
title: "Problem Backuped files"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2011-09-13
Hello friedns, i backup all .deb files in dpkg-repack folder. Now this folder is full of package. But i want to install kubuntu in my system, and i want to install the package which i backup in dpkg-repack folder. Now i am confused, there are many many package, how can i recognize them, which is audio,video codec, which is virtualbox,which is google earth. Please help me. I cant recognize them, there are too many package. Also tell me, the audio,video codec can installed in kubuntu from backup? Virtualbox can install in kubuntu from backup? Please help me.

---

### Post by mörgæs on 2011-09-13
I don't quite understand... why do you back up these packages? 

If you do a plain install of Kubuntu and an update after that, your system will have all the newest packages. After that you can install extra applications from the repositories, which also contain only new packages.

---

### Post by SBMN7 on 2011-09-13
I have not good internet service. So, i cant upgrade it. So, i want to install it from backup. I backuped files from ubuntu & now i delete ubuntu & install kubuntu on my system . I saved all backuped files in another directory. Now i want to install them in kubuntu. But i have no idea how to install them. Please help me.

---

### Post by Elfy on 2011-09-14
Open the file manager as root - I think it's dolphin in kubuntu, tkae great care when using a file manager as root - you could cause a lot of damage.

kdesudo dolphin

Go to where the debs are and copy them to /var/cache/apt/archives

then do an update

sudo apt-get update

---

