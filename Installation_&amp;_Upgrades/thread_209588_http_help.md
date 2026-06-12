---
title: "http help"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by dareofficer on 2006-07-05
I need help with apache.  I have apache2, enabled, and can see it but I can't show the files I want to show, I mean point it at my home directory.

This is an example of my area,

berlin@berlin-ubuntu:/$ cd var
berlin@berlin-ubuntu:/var$ cd www
berlin@berlin-ubuntu:/var/www$ ls
apache2-default  Folder  movies  Movies  Music  video  Video
berlin@berlin-ubuntu:/var/www$ cd video
bash: cd: video: No such file or directory
berlin@berlin-ubuntu:/var/www$ /home/berlin/Video Movies
bash: /home/berlin/Video: No such file or directory
berlin@berlin-ubuntu:/var/www$ ls
apache2-default  Folder  movies  Movies  Music  video  Video
berlin@berlin-ubuntu:/var/www$

The folder movies, movies, music video video, show up but the link has nothing in it.

---

### Post by adwait on 2006-07-05
How did you create those files? Copied the folders? Or created Symlinks??

---

### Post by dareofficer on 2006-07-05
sudo ln -s <path to your music folder> /var/www/

---

### Post by adwait on 2006-07-05
It seems ou have made some mistake while linking the files, perhaps a typo or somehing? Check it out with
```
ls -lia
```

Check the part after -> of each file...That's all I can think of :)

---

