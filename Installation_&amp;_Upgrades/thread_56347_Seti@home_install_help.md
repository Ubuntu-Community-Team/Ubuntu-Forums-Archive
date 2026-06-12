---
title: "Seti@home install help"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by madhatter563 on 2005-08-12
Heres the background info.. I just installed ubuntu.  Im pretty new at linux, Ive been using windows my whole life, and want to explore.. Well, I want to run seti@home on a computer I have that is running ubuntu.. but I don't know how to get it to install.. I tried a command from another post about this "sudo apt-get install setiathome" but it said "E: couldn't find package setiathome" I dont know where to go from here... Any help would be great! Thanks!

---

### Post by mo_x on 2005-08-12
Have you enabled multiverse in /etc/apt/sources.list?
You can also download the program from the seti@home website. The website has instructions somewhere on how to install.

---

### Post by madhatter563 on 2005-08-12
I dont even know how to enable that.

---

### Post by numberexhaust on 2005-08-12
To enable that, type the following code in a terminal window:

```
sudo gedit /etc/apt/sources.list
``` 

It'll ask you for your password, then open a text editor.  Uncomment every line in the file that has a single # in front of it, as opposed to a double.

For example, 

##Something something
##Something else
#Some line of code

Becomes

##Something something
##Something else
Some line of code

Save it and then close the editor.  Ask someone else how to install SETI-at home (I'm new to Debian myself,  still learning a lot of things). :smile:

---

### Post by tread on 2005-08-12
[http://setiathome.ssl.berkeley.edu/](http://setiathome.ssl.berkeley.edu/) 

Go to the download page, and there are installation instructions there.

---

### Post by jeffdano on 2005-12-06
Don't forget to join up with the Ubuntu effort at SETI@home as well... we would sure appreciate some new recruits (or seasoned veterans).

[http://setiathome.berkeley.edu/team_display.php?teamid=116723](http://setiathome.berkeley.edu/team_display.php?teamid=116723)

Yeah, yeah, I know I posted this one twice tonight (another thread), but I'm trying to spread the word.:KS

---

