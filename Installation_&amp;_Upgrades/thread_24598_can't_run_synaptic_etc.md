---
title: "can't run synaptic etc"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by plzdontspamme on 2005-04-07
I recently installed Hoary 5.04 but now I'm unable to access anything that requires me to enter a password (Synaptic, root terminal, etc.)  I can log into Ubuntu using my username and password, so I know that my user password is OK.  Also, I can log into my root account by opening a user terminal, typing "su" then my root password, so I know my root password is OK, too.  But, if I try to use any Gnome application that requires a password, neither my user or root password will work.  (Which password should I be using to open these anyway--my root or my user password?)

FWIW, I installed Ubuntu over two partitions, one for my root directory and the other for my home directory.  I tried reinstalling over these two partitions but am having the same problem.   (Note that in reinstalling over my home partition, the original information appears to have remained since my old bookmarks in Firefox were still there!)

---

### Post by Nis on 2005-04-07
[QUOTE=plzdontspamme]I recently installed Hoary 5.04 but now I'm unable to access anything that requires me to enter a password (Synaptic, root terminal, etc.)  I can log into Ubuntu using my username and password, so I know that my user password is OK.  Also, I can log into my root account by opening a user terminal, typing "su" then my root password, so I know my root password is OK, too.  But, if I try to use any Gnome application that requires a password, neither my user or root password will work.  (Which password should I be using to open these anyway--my root or my user password?)

FWIW, I installed Ubuntu over two partitions, one for my root directory and the other for my home directory.  I tried reinstalling over these two partitions but am having the same problem.   (Note that in reinstalling over my home partition, the original information appears to have remained since my old bookmarks in Firefox were still there!)[/QUOTE]
 You should always use your password in the gksudo boxes that pop up when you try to run a priviledged application.  You sudo setup might be wrong or you are no longer part of the admin group, which is now the group that can sudo for root priviledges, as compared to Warty where only the first user on the system had this priviledge.  Try editing /etc/sudoers with visudo (this command is the command that must be used) and check to see if you have this line:
```

%admin  ALL=(ALL) ALL

```
If you don't, add it.  If you do, make sure your username is part of the admin group.  Open up the Users and Groups tool as root and check out your username's properties.  Under 'User priviledges' make sure 'Executing system administration tasks' is checked.  If you don't have that option listed, add the admin group using the 'Users and Groups' tool and then trying adding your username to the group as per the instructions above.  Log out and back in as your username and see if your priviledges are back.

---

### Post by plzdontspamme on 2005-04-09
The line in my /etc/sudoers file before read
```
root   ALL=(ALL) ALL 
```
I changed it to
```
%admin  ALL=(ALL) ALL
``` 
as you suggested.

But, I was unable to open the User and Groups tool as you suggested for the original reason of my post  O:) , so I tried to add my username to the "admin" group using 
```
adduser *myusername* admin
``` 
That group didn't exist, so I first had to create the group using
```
addgroup admin
``` 

Now I can access almost all the functions requiring root access *except* :
1) It's not asking me for *any* passwords (shouldn't it be at least asking me for my username's password??), and
2) When I try to use the Users and Groups tool, I receive the message
 > The entered password is invalid.
Check that you typed it correctly and that you haven't activated the "caps lock" key 
even though I was never asked to enter a password!

What now?

---

### Post by aholz on 2005-05-22
I do have the same problem also. No application that requires 'root' rigths run. For instance, synaptic. If I enter with my user passaword it just says:

 Failed to run /usr/sbin/synaptic:
 Child terminated with 1 status

on root console I get:

root@ubuntu:~ # synaptic

(synaptic:12909): Gtk-WARNING **: cannot open display:
root@ubuntu:~ #

Is this already solved? With my livecd there is no problem. But it does not make really much sense to download many packages on a I live CD  ;-) 

Alex

---

### Post by aholz on 2005-05-22
I think I have it now :) 

Ubunto should not allow working with root for X apps. It should have an adm or admin group where my 'userlogin', as it was the first created, should be in. This group members are allowed to "sudo" administrative tools (like synaptic, for instance).

Somehow, this group did not exist and my 'userlogin' does not have priviledges.

So I went to root console, folder /etc and edited 'suduers' file with the apropriate command visudo. I added my 'userlogin' just like this:

userlogin  ALL=(ALL) ALL

After saving the sudoers file (note that visudo is an script that edits a sudoers.tmp file and copy over sudoers. So, just save sudoers.tmp as you leave the editor and the script will do it right), I was able to run everything without questions (passwords) asked. 

I am trying now to bring it as it should be, that is, creating an admin group and adding my 'userlogin' to it and having passwords asked. If I succed, I will post here.

Alex

---

### Post by aholz on 2005-05-22
*Final Solution*

The first response to this thread from **Nis** was right. Just crate a admin group, add yourself to this group and add the group to sudoers file. Just user group name with a % in front of it. 

Everything will work fine then. Use my other suggestion to be able to star /Administration /Users and Groups application. Then remove yourself from sudoers later.

Alex

---

### Post by cRoMo on 2005-05-27
[QUOTE=aholz]*Final Solution*

The first response to this thread from **Nis** was right. Just crate a admin group, add yourself to this group and add the group to sudoers file. Just user group name with a % in front of it. 

Everything will work fine then. Use my other suggestion to be able to star /Administration /Users and Groups application. Then remove yourself from sudoers later.

Alex[/QUOTE]
 I have upgraded from Debian SID, and have similar problem. First, I removed old sudoers file and did dpkg-reconfigure sudo, so the new one was created. Then I used Nis instructions: added myself to admin group, added %admin  ALL=(ALL) ALL, and logout to make changes work. And it worked fine, but... I could run any program with sudo and it didn't ask for password at all! Note, that I also had root   ALL=(ALL) ALL  line in sudoers file. What is wrong?

---

### Post by cRoMo on 2005-05-28
*bump*

---

### Post by cRoMo on 2005-05-28
I have just find out, that I can run some system commands as an user without using sudo, e.g. wajig upgrade/remove (but not apt-get upgrade/remove). What is the problem? This is how my sudoers file looks like:

root	ALL=(ALL) ALL
%admin  ALL=(ALL) ALL

As I mentioned before, user is added to admin group.

EDIT: OK, I get it. sudo doesn't ask for password as it can cache it somehow, whilst wajig uses sudo automatically whenever it needs to. Personally I'd like sudo to cache password only for some time, e.g. 5 minutes.... is it possible at all?

But other problem is that "sudo reboot" works fine when executed from terminal, but the same command executed by fluxbox menu doesn't work...

EDIT2: OK, I found out how to lessen time within sudo remembers my password. Still didn't manage to fix "sudo reboot" problem...

---

