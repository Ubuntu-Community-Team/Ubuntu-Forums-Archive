---
title: "Questions about finding software packages"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Jeff Root on 2011-03-18
I want to install ubuntu-restricted-extras and other packages
on an operating system other than the one I'll use to download
them.  Where do I go to search for the packages I want?
 
What is the relationship between the Ubuntu Software Center
and Synaptic Package Manager?  I can't tell whether they are
supposed to do the same thing or completely different things.
 
   -- Jeff, in Minneapolis

---

### Post by Megaptera on 2011-03-18
For "What is the relationship between the Ubuntu Software Center and Synaptic Package Manager?"  have a look at answers 3 & 4 here [http://ubuntuforums.org/showthread.php?t=1547531](http://ubuntuforums.org/showthread.php?t=1547531) I think that explains it quite well.

---

### Post by JRV on 2011-03-18
There is a program called APTonCD available in the Software Center that can create a repository of the packages you want on a CD to use on any Debian based system. (Ubuntu is a Debian based system.) 

In Linux everything can be done from the command line.
The low level package management command is dpkg.  It can be accessed with the apt-get command.  The Software Center, Synaptic, and the Update Manager are all graphic front ends to dpkg.

Jack - Also in Minneapolis

---

### Post by matt_symes on 2011-03-18
Hi

EDIT: Just re-read your post and i'm not sure if this is directly related to your question but it may help others.

You can search for packages using the command apropos <search word>

i.e.

```
matthew@matthew-laptop:~$ apropos browser
charmap (1)          - Unicode character picker and font browser
chromium-browser (1) - the web browser from Google
elinks (1)           - lynx-like alternative character mode WWW browser
git-web--browse (1)  - git helper script to launch a web browser
gnome-character-map (1) - Unicode character picker and font browser
gucharmap (1)        - Unicode character picker and font browser
infobrowser (1)      - read Info documents
libsmbclient (7)     - An extension library for browsers and that can be used as a generic browsing API.
lynx (1)             - a general purpose distributed information browser for the World Wide Web
lynx.cur (1)         - a general purpose distributed information browser for the World Wide Web
sensible-browser (1) - sensible editing, paging, and web browsing
smbtree (1)          - A text based smb network browser
viewres (1)          - graphical class browser for Xt
w3m (1)              - a text based Web browser and pager
www-browser (1)      - a general purpose distributed information browser for the World Wide Web
matthew@matthew-laptop:~$
``` 

If they are in your sources they will be found if there is a match.

Also have a look at

[http://www.osalt.com/](http://www.osalt.com/)

and 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Kind regards

---

