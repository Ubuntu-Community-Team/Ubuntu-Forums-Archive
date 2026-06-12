---
title: "No desktop, only a Terminal"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Korenwolf on 2010-03-22
Hello all,

first of all, I'm on a Compaq Pressario CQ60
4GB RAM, Nvidia 8200M.

I tried to upgrade from 9.10 to 10.04, using "update-manager -d".
It downloaded all sorts of packages, mentioned wich packages would not be used anymore, installed the new packages and then deleted all sorts of obsolete files and packages. So far so good, as far as I can see.

But then after restart is started to go strange.

First I got a black screen with some text on it, pretty normal.
But then I got to a most ugly purple page with 10.04 on it with 4 small dots/squares. It looked like a screen from 15years ago, but then coloured.

After that I got what I think is a default purpleish desktop colour screen with the login box.

When I click my account I'm able to enter my password. normally at the bottom of the screen I'm able to chose the language, the keyboard layout and the desktop environment. the first two I'm able to choose now, but the desktop option is totally missing.

when I enter my password and start my session I get the same background as above and a terminal, but nothing else.

When I check for updates via "update-manager -d" I get some updates, but none fixes the problem
When I try "sudo apt-get udate" and "sudo apt-get upgrade" it checks all sorts of things but then isn't able to upgrade anything.
Then I entered "gnome-panel" I got some very basic, bad looking panels (this way I was able to start chrome and write this). with these panels some applications are accesible, but none of my documents or files are accesible. When I try it says "No apllication is registered as handling this file".

I'm a bit lost now, I couldn't file a bug report (got some error messages) so thats why I tried here.

Cheers,
Erwin

EDIT: via the chrome webbrowser I am able to acces my files, the only way so far via 10.04

Attachement below:
The desktop after I typed gnome-panel and started chrome.
But the first thing I see after I logged in is this backrgound with the terminal in the left upper corner

---

### Post by cheapsaket on 2010-03-22
This might help you:
[http://ubuntuforums.org/showpost.php?p=3254746&postcount=3](http://ubuntuforums.org/showpost.php?p=3254746&postcount=3)

---

### Post by Korenwolf on 2010-03-22
> **cheapsaket said:**
> This might help you:
[http://ubuntuforums.org/showpost.php?p=3254746&postcount=3](http://ubuntuforums.org/showpost.php?p=3254746&postcount=3)

Tried it, but it doen't give any reaction

---

### Post by sdowney717 on 2010-03-22
try running in terminal these

sudo apt-get update
sudo apt-get dist-upgrade

---

