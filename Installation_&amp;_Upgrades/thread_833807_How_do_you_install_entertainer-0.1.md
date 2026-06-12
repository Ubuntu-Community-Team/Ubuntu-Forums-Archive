---
title: "How do you install entertainer-0.1?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by JoCoProductions on 2008-06-18
From what I have seen in the screenshots,  the program entertainer for linux looks amazing so I have downloaded but I'm having trouble installing it. I extracted the tarball to my desktop, and in terminal cd'ed to the src folder and inputted ```
./entertainer-content-management.py
``` which resulted in ```
Traceback (most recent call last):
  File "./entertainer-content-management.py", line 30, in <module>
    from utils.content_management_dialog import ContentManagementDialog
  File "/home/joco/Desktop/entertainer-0.1/src/utils/content_management_dialog.py", line 38, in <module>
    from utils.weather import Weather
  File "/home/joco/Desktop/entertainer-0.1/src/utils/weather.py", line 12, in <module>
    from utils.theme import Theme
  File "/home/joco/Desktop/entertainer-0.1/src/utils/theme.py", line 10, in <module>
    import clutter
ImportError: No module named clutter

```
Then according to [http://laymanstermsdev.wordpress.com/tag/install/]("http://laymanstermsdev.wordpress.com/tag/install/") you are supposed to ```
./entertainer-frontend.py
``` which again resulted in an error ```
Traceback (most recent call last):
  File "./entertainer-frontend.py", line 30, in <module>
    from frontend.frontend_client import FrontendClient
  File "/home/joco/Desktop/entertainer-0.1/src/frontend/frontend_client.py", line 10, in <module>
    from utils.theme import Theme
  File "/home/joco/Desktop/entertainer-0.1/src/utils/theme.py", line 10, in <module>
    import clutter
ImportError: No module named clutter
```

Any ideas of how to get this program installed and running?

---

### Post by Laterix on 2008-06-19
You must run entertainer-backend first. It will create configuration files and builds database. After that you can run content management tool.

When you run frontend it says that clutter is missing. So, you should install clutter from repository.

Here is a list of Opened hand clutter repos:

deb [http://debian.o-hand.com](http://debian.o-hand.com) edgy/
deb [http://debian.o-hand.com](http://debian.o-hand.com) feisty/
deb [http://debian.o-hand.com](http://debian.o-hand.com) gutsy/
deb [http://debian.o-hand.com](http://debian.o-hand.com) hardy/

---

### Post by Layman's terms on 2008-07-07
I believe that a fairly current version of clutter is in the Universe repository. So if you have enabled that software source (instead of adding the Open Handed respository), you should be able to execute the command:

```
sudo apt-get install python-clutter
```

But if you haven't installed clutter yet, I'm guessing that you haven't installed all the other dependencies as well. You can install all the Entertainer dependencies with the following command:

```

sudo apt-get install python-gobject python-gtk2 python-gst0.10 python-clutter \
python-pysqlite2 python-cddb python-glade2 python-cairo python-feedparser \
python-pyinotify python-eyed3 python-pyvorbis python-imaging python-imdbpy \
python-notify

```

---

### Post by schmindy on 2008-10-12
Any news on ibex?

---

### Post by Layman's terms on 2008-10-15
schmindy, we (the Entertainer developers) can not support Intrepid Ibex because of a problem with clutter (the graphical toolkit that makes Entertainer look so pretty).

Clutter is currently on version 0.8 and Interpid Ibex has the 0.8 libraries. However, the python binding for clutter (read: the part that Entertainer needs to interface with clutter) have not been updated to support 0.8 yet. Because of this broken binding, clutter will not work with any python apps that try to use it, including Entertainer.

We're kind of bummed that pyclutter has not been updated to support 0.8, but there is not much we can do about it. We may try to package 0.8 pyclutter and make it available for users, but that will be a last resort because we want to avoid being packagers of our dependencies.

---

