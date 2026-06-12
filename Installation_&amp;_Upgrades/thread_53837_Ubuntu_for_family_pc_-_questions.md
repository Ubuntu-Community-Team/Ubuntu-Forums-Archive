---
title: "Ubuntu for family pc - questions"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by onniojut on 2005-08-02
Hi! 

I'm going to install Ubuntu for a family pc. I have some questions for advantage. 

1. When I install all the software are they avalable for all users by default? If they aren't what is the easiest way to do it?

2. How can I make a default session same for every user?

3. What is the easiest way to access and do maintenance to Ubuntu remotely, like via ssh or remote desktop?

4. Best way to do filesharing for all users? 

5. How about partitioning?

Any advices for the procedures? 

Thanks.

---

### Post by jasmuz on 2005-08-02
Hello there!

Some answers to your questions.

If you install software, generally they are available to all users, unless its software that is to modify the system, wich only the main user can.

Default session?...the default session for Ubuntu, is Gnome with the Human theme, any more?

Maintenance for your Ubuntu, can be easily done via SSH (most of us do).

The best way to do filesharing for all users is to create a folder in the root partition and give all users read/write access.

You wont have to make any decisions upon partitioning unless you are sharing the disk drive with another operating system, in wich case you would need to resize the space in order to make a root partition and a swap space (wich is normally the double the size of your ram)

Here you can read about how its installed:

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

Well hope that helps.

---

### Post by onniojut on 2005-08-02
Thanks alot.

> If you install software, generally they are available to all users, unless its software that is to modify the system, wich only the main user can. 
Can you give an example of both to really understand the difference?


> Default session?...the default session for Ubuntu, is Gnome with the Human theme, any more? 
If I put a link to the shared folder on the desktop of 'default session' and save it does it look the same way with every user. Guess it does. 


**partitioning** - So it would be okey to leave 40GB harddrive with only one partition in the installation if you only use Ubuntu.

[B]
maintenance[/B] - What about maintenance done with 'remote desktop' mentioned in Ubuntu starter guide? Could be easier for me to be able to work in gnome gui. I have been using Ubuntu since warty but I haven't done these things before.

---

### Post by kosmic on 2005-08-02
[QUOTE=onniojut]Thanks alot.

 
Can you give an example of both to really understand the difference?


 
If I put a link to the shared folder on the desktop of 'default session' and save it does it look the same way with every user. Guess it does. 


**partitioning** - So it would be okey to leave 40GB harddrive with only one partition in the installation if you only use Ubuntu.

[b]
maintenance[/b] - What about maintenance done with 'remote desktop' mentioned in Ubuntu starter guide? Could be easier for me to be able to work in gnome gui. I have been using Ubuntu since warty but I haven't done these things before.[/QUOTE]


For example most of the program you install by apt (synaptic) is avaible to all your users in the system, but if you compile a program and put that program in the /opt/program and the acess permissions and group permissions is set only to your user, no one in your system can acess or execute that program except you.

If you are not comfortable with shell comands then is best to do gui manutention, try FreeNX :) if you pretend to do maintenace from a Windows PC, is just a sugestion :)

Yes for a simple instalation you can make only 1 partition with 40GB

---

### Post by az on 2005-08-02
2. How can I make a default session same for every user?

Do you mean the theme?  Do you mean like if you make a symlink on your desktop that it appear on everybody else's?  Do you mean the everybody automatically logs into one user account at boot?




3. What is the easiest way to access and do maintenance to Ubuntu remotely, like via ssh or remote desktop?

remote Desktop (VNC) I guess is easier, but it is the least secure.  If you want to use ssh, install the ssh package.  By default, you only have the ssh client installed.



4. Best way to do filesharing for all users?

Right click on a folder in a home drive and make it world-read/writeable.  I would not use another directory in the root directory.


5. How about partitioning?

How about it?  If you are assking about partitoining for the sake of partitoining, just use the default - one partition for everything.  If you have other specific needs, what are they?

You can use the installer to split an NTFS partition if you want to dual boot...

---

### Post by onniojut on 2005-08-02
[QUOTE=azz]2. How can I make a default session same for every user?

Do you mean the theme?  Do you mean like if you make a symlink on your desktop that it appear on everybody else's?  Do you mean the everybody automatically logs into one user account at boot? [/QUOTE]


I just mean that I want to make the session easy to use for everyone in the family. They haven't used linux before so the basic things can be hard for them. I wanted to make a shared directory which they had a link on their desktop. And maybe some other most common links to the desktop.. Don't know yet. And I don't want to make it again for every user...

Also it would be great if they all had the same theme. I believe 'Clearlooks' is the easiest to approach...

Don't know what is symlink.

---

### Post by mingus on 2005-08-02
[QUOTE=onniojut]
Don't know what is symlink.[/QUOTE]

Essentially the same as a W$ shortcut . . . also like in W$, easiest way to create is in Nautilus (the gnome explorer equiv), just right-click on an object and then click on "Make Link", then drag it wherever you want it.  You can also drag to the panels (taskbars).

---

