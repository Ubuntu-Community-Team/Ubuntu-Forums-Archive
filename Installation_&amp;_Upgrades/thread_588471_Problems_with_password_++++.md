---
title: "Problems with password ++++"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by theKvakkis on 2007-10-23
First of all: im completely new with linux, installed it last night. With that "install from windows"-option, since the cd-rom didn't work xD

------------------
The install was finished, and i was about to start up for the first time, and the problems that has occured up to this point is the following:

1: After ive wrote in username and password, nothing happened. I think i was supposed to write some commands in the dos-like black/white window at start up, but i don't know what. Suddently the next problem occured:

2: I cant write my password! I turned of the computer, and returned several hours later to try again. Maybe i hit a wrong button or something, but i just can't enter my password:O username works fine, but when it comes to the password, it's just no reaction at all when i hit the keyboard.

Please help:D

Looking forward to new and interesting experiences with Linux!

---

### Post by DagonSphere on 2007-10-23
Did you try hitting ENTER after typing the password?  As a asecurity feature, passwords aren't displayed (even the **** placeholder) on a console login

---

### Post by theKvakkis on 2007-10-23
That was the one, oh dear how embarrasing xD

Anyway, what should i do next (problem #1)?
The console-thing asks me to enter some commands or something, but i don't know what.

Am i even finished with the install? Is this things i must do, or have i done anything wrong?

---

### Post by Robor on 2007-10-23
What are you trying to do from the console?  Are you trying to launch the GUI to get to the desktop?  If so I think the command is, '/etc/init.d/gdm start'  My question is, what type of install is this?  Did you choose a 'Server' install?  If so, by default it doesn't load the stuff for a GUI.

---

### Post by theKvakkis on 2007-10-23
Yeah, im trying to get to the desktop, one way or another:P

I don't know which instaltion it is, but i was that "install from windows-"stuff. ubuntu 7.04. Don't think that was hat you asked about, but thats wat i know xD

---

### Post by Robor on 2007-10-23
Can you post where you got this installer?  Are you talking about Wubi?

---

### Post by theKvakkis on 2007-10-24
I got it at the official Ubuntu-page.

---

### Post by Martje_001 on 2007-10-24
What do you see if you type 'startx' in the console.

btw. Installing from windows is still experimental..

---

### Post by theKvakkis on 2007-10-24
Something happen, a lot of text appeared on the screen, and at last the message "No valid FontPath could be Found".



btw: i wanted to install from a CD, but the CD-rom didn't work:/
Maybe i should try to install from a memory-stick instead?

---

### Post by DagonSphere on 2007-10-25
I'm not familiar with 'Install from Windows.'  I'm not sure if it's like a full ~650mb install CD, or a Debian NetInstall CD, but let's try a few things.

After logging in, switch to superuser.

```
sudo -s
```

Enter your password
Note: My previous post said ENTER - this was not shouting; just a means to tell you it's a key :)

Check your /var/log/messages file for anything pertaining to the X server

```
grep -i x /var/log/messages
```

And check dmesg

```
dmesg | grep -i x
```

Post anything that may look like an error.  Also, what kind of video card do you have?

Oh, and don't be embarrassed about the password thing.  All of us who dove into Linux head first have embarrassing stories.  This is a whole new world :)

---

