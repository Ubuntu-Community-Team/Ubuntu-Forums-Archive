---
title: "emesene 1.5 - can't type user login"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wxnker on 2009-09-24
Anyone else having this problem? When opening emesene I can't type in the user account. I can enter the password, change status and select check boxes, but the user field is grey/non selectable.

I already tried reinstalling + deleting the emesene folder in ~./config.

---

### Post by Ubu-Sef on 2009-10-01
[LEFT]Hello,

Yesterday I've managed to fix it. It works for me, so enjoy this solution.

What do you need to do?


[LIST=1]
[*]You need to run emesene as root. You probably get this message:
> I refuse to run as root
[*]Time to do something against that. Open the Console and type in:
```
sudo kate /usr/share/python-support/emesene/Controller.py
```Find:

> def debug(msg):
   '''print a debug message'''
   print 'Controller: ' + msg

def main():
    if os.name == 'posix' and os.getuid() == 0:
        print "I refuse to run as root"
        return

   try:
       path = os.path.dirname(__file__) or sys.path[0]
   except NameError:
       path = sys.path[0]And change it like so:

```
def debug(msg):
   '''print a debug message'''
   print 'Controller: ' + msg

def main():
#    if os.name == 'posix' and os.getuid() == 0:
#        print "I refuse to run as root"
#        return

   try:
       path = os.path.dirname(__file__) or sys.path[0]
   except NameError:
       path = sys.path[0]
```So, comment the three lines out.
[*]Time to run it as root. Open up a console and type:

```
sudo emesene
```
[*]Now, you see the login box is unlocked. Login with a wrong password, so you get a error.
[*]Close emesene from the taskbar and open up a console again.

Do:

```
sudo chown -R "your username" /home/<your username>/.config/emesene1.0/<youraccount>/
```Without the quotes and arrows
[*]Open emesene again, and login.
[*]Happy chatting!
[/LIST]
Success to all, I hope I writed it Noob-friendly enough.

Cheers!
[/LEFT]

---

### Post by ljrmorgan on 2009-10-01
It's probably better to file a bug than do this, it seems a bit hacky, to put it mildly!

Seriously, report a bug, share your solution by all means, and get it properly fixed, I'm guessing the developers would rather know about the problem than have their users doing this.

---

### Post by wxnker on 2009-10-03
Thank you for your replies. The problem is fixed with recent updates.

Cheers,
wxnker

---

### Post by sleepitoff on 2009-10-07
Hmm... I'm having this problem now after fresh reinstall and I have the latest updates. This seems to be KDE related somehow, as another app with a similar problem is Nicotine+, where you can't type in the search box. Both work in Gnome/Ubuntu, though

Ubu-Sef's work around doesn't work for me, either, as /usr/share/python-support/emesene/Controller.py doesn't exist :(

---

### Post by cylverbak on 2009-10-08
Same problem here trying to install emesene in KDE with everything updated.

Ubu-Serf's fix worked well. I found Controller.py in /usr/share/emesene/Controller.py on my machine.

---

### Post by sleepitoff on 2009-10-08
Okay, I adjusted the commands to locate my controller.py and it's still not working :( Any thoughts? It works if I run through the terminal as root, but not otherwise

---

