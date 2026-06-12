---
title: "Entertainer"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by tacticalsphinx on 2008-09-10
Can anyone tell me where i can find the file entertainer-0.1.tar for Ubuntu 8.04 on lunchpad? Also what is lunchpad?

---

### Post by Partyboi2 on 2008-09-10
If you are meaning launchpad it is a  hosting service for open source projects. This is where you can report bugs get answers for problems and get involved in different projects. You can read more [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/+tour/index")
You can download entertainer from [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/entertainer/+download") (launchpad)
But if you were actually wanting info on lunchpad then see [[COLOR=Blue]here[/COLOR]]("http://www.lunchpad.com/") :wink:

---

### Post by tacticalsphinx on 2008-09-11
ok, so how do i install it in ubuntu. all i get is the option to open it in archive manger.

---

### Post by Partyboi2 on 2008-09-11
Open a terminal (Applications>accessories>Terminal)
and install the needed packages.
```
sudo apt-get install python-gobject python-gtk2 python-gst0.10 python-clutter python-pysqlite2 python-cddb python-glade2 python-cairo python-feedparser python-pyinotify python-eyed3 python-pyvorbis python-imaging python-imdbpy python-notify
```
Then change directory to where the downloaded entertainer-0.1.tar.gz file is, so if its on your Desktop type
```
cd ~/Desktop
```
then extract it with
```
tar xvzf entertainer-0.1.tar.gz 
``` then change into the newly created directory
```
cd entertainer-0.1/src
```
then set the contents
```
./entertainer-content-management.py
```
then 
```
./entertainer-backend.py
```
finally
```
./entertainer-frontend.py
```

---

### Post by tacticalsphinx on 2008-09-11
got it working but cain't seem to add music, movies, picture. also, do i always have to run it in terminal.

---

### Post by Layman's terms on 2009-03-24
tacticalsphinx,

Entertainer is still a pretty young project in the scheme of media center applications. You can now install it from a package, but launching the content manager and preferences still requires a terminal command for now.

[http://wiki.entertainer-project.com/wiki/StartUpGuide](http://wiki.entertainer-project.com/wiki/StartUpGuide) is a good place to start for installation instructions.

You can also ask any question directly to the developers on Launchpad ([https://launchpad.net/entertainer](https://launchpad.net/entertainer)) or on the IRC channel (more info that can be found on the wiki).

---

