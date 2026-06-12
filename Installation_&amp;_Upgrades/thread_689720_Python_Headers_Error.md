---
title: "Python Headers Error"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Thexgene14 on 2008-02-06
Ok trying to install [Avant Windows Navigator 0.2.1]("https://launchpad.net/awn") using a .tar file. 

I use the following method.

# tar xvzf avant-window-navigator-0.2.1.tar 
# cd avant-window-navigator-0.2.1
# ./configure
# make
# make install

My problem comes at "./configure"

It seems to run fine. Goes through "Checking.....yes" stuff

at the end it is checking for python version...2.5 and I get this error:

[COLOR="Red"]configure: error: could not find Python headers[/COLOR]

I tried the following command:

sudo apt-get install python2.5-dev (found that on a quick forum search)

Get this error
E: Could not find package python2.5-dev

Do I have to change the source list? What url would I put in it? 
Also I went to the [Python Website]("http://www.python.org/download/releases/2.5.1/") and I tried installing version 2.5.1 from the .tar file. Using the same install method listed above. Worked fine, But I still get the error. Restarted computer. Still have the error:

[COLOR="Red"]configure: error: could not find Python headers[/COLOR]

Any help would be great. Thanks. Also, I am very new to ubuntu. Sorry if this is something stupid.

---

### Post by Partyboi2 on 2008-02-07
Open up Software Sources (System>Admin>Software Sources) make sure on the first tab you have all of them ticked except source code. Then close the window and try installing  python2.5-dev again.

---

### Post by jan quark on 2008-02-07
if everything else fails 

try this graphical installation guide

[http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu](http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu)

---

