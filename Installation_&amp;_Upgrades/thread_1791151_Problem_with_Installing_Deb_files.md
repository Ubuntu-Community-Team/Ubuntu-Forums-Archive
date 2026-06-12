---
title: "Problem with Installing Deb files"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by nmoyefelix on 2011-06-26
[FONT="Arial"][/FONT]

Hi, I am a Newbie, I downloaded repositories offline and tried install. I was directed to a install.sh file and to run in the installer. Please how do I go about it? Am I to copy it in the Terminal?

---

### Post by Enigmapond on 2011-06-26
If you are attempting to install a .deb file, just click on it and it will automatically install. Sounds as if you are trying to install from a tarball...can you be more specific?

PS Welcome to the forum..:)

---

### Post by nmoyefelix on 2011-06-26
> **Enigmapond said:**
> If you are attempting to install a .deb file, just click on it and it will automatically install. Sounds as if you are trying to install from a tarball...can you be more specific?

PS Welcome to the forum..:)

You are right, its a tarball, I double clicked it and got it a folder, a file named "install.sh" and a readme.txt. The readme says I should unpack/extract, thann, it says select "run in terminal". This is the problem. How do I run in terminal? Thanks

---

### Post by Enigmapond on 2011-06-26
Right so, extract it to a directory and then in the terminal, navigate to the directory and do:

```
sudo ./install.sh
```

That should do it providing you have the necessary programmes to compile.

---

### Post by nmoyefelix on 2011-06-26
> **Enigmapond said:**
> Right so, extract it to a directory and then in the terminal, navigate to the directory and do:

```
sudo ./install.sh
```

That should do it providing you have the necessary programmes to compile.


Thanks, it worked like magic.:D

---

### Post by Enigmapond on 2011-06-26
Cool...Glad to help. You should mark the thread as solved, in the Thread Tools on top.

Happy Linuxing...:)

---

