---
title: "Installing server version"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by pod25 on 2006-09-09
Hello all.
To start I am a total newbie with Linux and Ubuntu, so please be nice, I am however a damn quick learner.

I have installed the server version of ubuntu, however I hate the fact that it's command line only, so I am installing the GUI over the top.
Now I know how to do this and I also know I need to edit > /etc/apt/sources.list Now to start, when I use > /etc/apt/sources.list in the command line I get permission denied, so I chmod the file to 777 to allow me to open the file, this is where my problem is.
Once I try to open the file I see this error : > /etc/apt/sources.list: line 5: syntax error near unexpected token '('
then
> /etc/apt/sources.list: line 5: 'deb cdrom:[Ubuntu-server 6.06.1 _Dapper Drake_-Release i386 (20060807.1)] dapper main restricted'

Without being able to edit the sources.list I cannot install ubuntu-desktop

---

### Post by berrida on 2006-09-09
I'm in the process of setting up a server myself and have just edited the same file.  I think you've got 2 issues here:

1 - you need to open the file with an editor - for me that's:

emacs /etc/apt/sources.list

2 - in order to write to the file you need to use sudo:

sudo emacs /etc/apt/sources.list

This should allow you to make the changes you want and save the file - it worked for me.

---

### Post by pod25 on 2006-09-09
I will give that a try.
Oh and I only need to use sudo if I am not logged in as root ;)

---

### Post by pod25 on 2006-09-09
After reading a post that appeared only a few minutes I have found my solution, here is my solution :
> nano /etc/apt/sources.list

Thanks to whizbaby 

There are bound to be more posts from me ;)

---

### Post by Sef on 2006-09-09
Do not log in as root.  This explains why [sudo is better]("https://help.ubuntu.com/community/RootSudo") than root.

---

### Post by az on 2006-09-09
> **pod25 said:**
> I will give that a try.
Oh and I only need to use sudo if I am not logged in as root ;)

Don't log in as root - use sudo.  Don't even think about using a desktop as root.

---

### Post by pod25 on 2006-09-09
Is there a reason why I should not be 'root'  ?

---

### Post by az on 2006-09-09
> **pod25 said:**
> Is there a reason why I should not be 'root'  ?

The Ubuntu desktop uses sudo for priviledge escalation.  You will not be able to use the desktop as root.

By default, there is no root account when you install the server version since it follows the same security model - sudo for privilege escalation.

---

