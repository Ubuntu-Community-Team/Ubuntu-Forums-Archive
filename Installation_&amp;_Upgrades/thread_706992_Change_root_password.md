---
title: "Change root password"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-02-24
Just reinstalled Ubuntu. Now I need to make a change to a file but get an error telling me that I can not make changes to it. I assume I need to login as root but I can't seem to figure out  what the default root password is. Is there a way to change it?

I even created a new user with Admin privileges but it can't edit file as well.

Lost...

---

### Post by Iandefor on 2008-02-25
The root account is left unconfigured in Ubuntu by default.

Instead, you should use sudo. If you're not familiar with sudo, the Ubuntu Wiki has a [good introduction]("https://help.ubuntu.com/community/RootSudo") to it.

---

### Post by dodgingspam on 2008-02-25
Actually I probably asked an incorrect question.

I need to add one line to /etc/modules but it won't allow me to save the changes when I am logged in as user. 

How do i make a change?

---

### Post by Iandefor on 2008-02-25
That's what sudo's for. You put it at the beginning of the command you want to run with administrative privileges. It'll ask you for your user password; provide it and it'll run the command with root privileges.
Like so:```
sudo nano [file]
```You can do the same with graphical applications. Just use gksudo (or kdesu if you're using Kubuntu) instead.

It's kind of like having an admin account but having the admin powers not always turned on.

---

### Post by Rome.konig on 2008-02-25
if you want to use a drag and drop method to open root files you can >right click on desktop >create launcher>title it> and for command use> gksu nautilus
now all you have to do is drag the folder that the file is in and you will be able to save the read only file.

---

### Post by ardren on 2008-02-25
1. Go to administration- Users and Groups, edit the password for the root.
2. Go to administration - Login Windo, then security tab, check allow local system administrator login.

Hope this help

---

### Post by gerananda on 2008-02-28
I am having the same problem. I read the threads of this post and they all make sense but nobody reveals the password that root brings by default. I tried changing root's password as someone said, but the system prompts you for root's pwd. Also, I think that in order to use **sudo**, you must be in some sort of sudo list, which in order to edit, I fear you will need root's privileges (i.e. password).
Sorry if this is a trivial qtn...

---

### Post by dodgingspam on 2008-02-29
Apparently you can make changes to setup without login in as root. If you problem sounds similar to what I was trying to accomplish, edit file, just open Terminal and add
[PHP]sudo[/PHP]
before your command. It's some sort of virtual root functionality. Did the trick for me.
Good luck.

---

### Post by aysiu on 2008-02-29
> **gerananda said:**
> I read the threads of this post and they all make sense but nobody reveals the password that root brings by default. Well, there are two reasons for this:
1. There is no root password by default. The root account is disabled for login.
2. There is no need to log in as root or enable the root account for login or give it a password. > I tried changing root's password as someone said, but the system prompts you for root's pwd. That shouldn't happen. I could give you the exact command you'd need to give root a password, but (as I said before) this is completely unnecessary. You should be able to accomplish all root tasks through *sudo*, *gksudo*, or *kdesu*. > Also, I think that in order to use **sudo**, you must be in some sort of sudo list, which in order to edit, I fear you will need root's privileges (i.e. password). Again, not true. You do not need root's password. You do need root privileges, however, and if you're not already in the *admin* group, perhaps another user thought it right that you shouldn't have administrative privileges on the computer. If you're the only user on your computer and somehow got yourself out of the *admin* group [this](http://www.psychocats.net/ubuntu/sudo) should help get you back in.

---

### Post by Iandefor on 2008-02-29
> **gerananda said:**
> I am having the same problem. I read the threads of this post and they all make sense but nobody reveals the password that root brings by default. I tried changing root's password as someone said, but the system prompts you for root's pwd. Also, I think that in order to use **sudo**, you must be in some sort of sudo list, which in order to edit, I fear you will need root's privileges (i.e. password).
Sorry if this is a trivial qtn... I recommend reading the page I linked to earlier. It should help to clarify some things.

---

### Post by Bucky Ball on 2008-02-29
Just to reiterate what was mentioned earlier:
[I]
There is no password set for root unless you set one yourself.[/I]

The password you set during installation is for the user only.

sudo (super user do!) nano ´filename´

... also mentioned earlier.

To change to root type:

sudo su

You will be asked for the *user´s* password and then you will become root:

root@yourmachine:#

If you are asked for root password, just hit enter as there isn´t one, unless, as I say, you have set one. :)

---

