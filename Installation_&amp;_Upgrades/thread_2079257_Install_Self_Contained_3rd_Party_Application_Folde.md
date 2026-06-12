---
title: "Install Self Contained 3rd Party Application Folder"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by kid1000002000 on 2012-11-01
Hello,

I am trying to install Kiwix ([http://www.kiwix.org/index.php/Main_Page](http://www.kiwix.org/index.php/Main_Page)). It comes downloaded as an already-compiled, self-containing folder that can be executed. However, I am trying to figure out the best place to store this folder in. I have successfully used Alacarte to add this to Unity's interface.

My questions:
[LEFT]
[LIST=1]
[*]This is an all-inclusive file. Should this be installed in /opt or /usr/local? My guess: /opt.
[*]These folders are owned by root. Putting the application in these locations does not allow me to run it as a non-root user, even if I change /kiwix's permissions! I do not want to just stuff the folder in /home/; I would like to follow proper protocol. I also am not sure if it is a good idea to change these folders to non-root access. Solution?
[/LIST]
Thank you for your help.

[/LEFT]

---

### Post by kid1000002000 on 2012-11-04
bump

---

### Post by darkod on 2012-11-04
If the application is a folder containing all it needs, simply put it in /usr/local/ so that it would be /usr/local/kiwix for example.

If you need to change some permissions so it can run, do it only for that folder. That will not affect all /usr/local/ it will only affect the kiwix folder.

Also check whether you need to make some files executable so it can run properly. Many apps come with their files but are not set as executable by default.

---

### Post by kid1000002000 on 2012-11-04
thank you

---

