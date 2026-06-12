---
title: "Installed successfully but no MAIL/FINGER command"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by Alok on 2005-11-19
I mean I have installed ubuntu 5.10 successfully on my computer and it is giving me bash shell.

I logged in succesfully and ran some basic commands(thats what all I know).

but when I run the MAIL/FINGER commands it says does not exist. 
And when I ask for manuals for these commands(e.g. man mail/finger) it says does not exist.

Can anyone please tell me if I have to install anything more?

Please advise as I am a newbie in this field. thanks

---

### Post by heimo on 2005-11-20
You could install mailx and finger:
```
sudo apt-get install mailx finger
```

Very useful package search:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

