---
title: "Complete noob needs help"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by johcker on 2005-04-14
I am trying to get my wireless USB adapter installed, but when I try to modify my interfaces file it will open as read only. I tried using the text editor and open office word procesor. I am sure there is a way to modify it from the command line but am lost.

---

### Post by nuke on 2005-04-14
I suspect you are trying to modify the file while logged in as the "user" and not root.  I am relatively new to Ubuntu and  I think that I read that root is not enabled by default.  This usually means that you need to do a super user (sudo) command to get to change configuration files.

If you are not familiar with one of the typical Linux command line editors, then you will need to start to learn this.

You might try something like this if you know how to use "vi". (Sorry I'm not even sure that vi is installed in the base as I am still trying to get Ubuntu installed on my laptop).  If you google on "vi" you should find some easy explanation of how to use it.  Or use "man vi" or "info vi".  For other editors just use same command with other editor name.  Other possible editors are "pico", "nano", "emacs".

At this point, you might want to make a copy of the file before you edit it so you can go back in case you screw something up.  i.e.

sudo cp filename filename.bak

then edit filename like this

sudo vi filename
Then you will be asked for your user pswd.

this should start vi editor as root.  The file should be read, write for you now.

Be careful and good luck!

---

### Post by johcker on 2005-04-14
thanks for the quick reply. I feel bad, I thought i had done a good search before asking the question but that was not the case. I now see that this is a FAQ and with what you have told me I should be good. Thanks so much. :)

---

### Post by lgb on 2005-04-14
"sudo gedit filename" without quotes    will do it for you.

---

### Post by Casey on 2005-04-14
[QUOTE=lgb]"sudo gedit filename" without quotes    will do it for you.[/QUOTE]

This works well if you need/prefer a gui.

If you are ok with doing things at the command line, I prefer nano for quick editing of conf files.  
```
sudo nano filename
```
will open the proper file in nano.  The basic commands are shown at the bottom of the window.  ^ means ctrl, so ctrl-x is exit, ctrl-o is write out, ctrl-w is find, etc.  I find nano quicker than gedit for most things.  If you need to do some multi-line copying and pasting, gedit is easier though.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=nuke]You might try something like this if you know how to use "vi". (Sorry I'm not even sure that vi is installed in the base as I am still trying to get Ubuntu installed on my laptop).  If you google on "vi" you should find some easy explanation of how to use it.[/QUOTE]

Ubuntu has **vim**, the improved version of vi, installed as part of its base. If you need a tutorial, I recommend [Gentoo's Cheatsheet Guide to Vim](http://www.gentoo.org/doc/en/vi-guide.xml).

---

