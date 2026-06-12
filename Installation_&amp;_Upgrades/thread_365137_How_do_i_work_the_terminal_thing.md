---
title: "How do i work the terminal thing"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by ianmak on 2007-02-19
I just don't get this. nothing works. i found a terminal, typed in sudo install antivir and entered and it wanted a password!! Every time i type in something it wants a password BUT when i go to put in a password the keyboard seems to be disconnected. You people should make things a lot more clear if you want us to take up the system. SO how do i get this terminal thing to work?...Ian

---

### Post by renzokuken on 2007-02-19
ok, when you use the command "sudo" it is giving you temporary superuser access.

if it asks for your password, just type in the password you used to login with.

the terminal will not display any text or 'stars' as you type, but trust me, it is recognising it.

just type the password and press enter, even if nothing is displyed in the terminal as you type.

---

### Post by teaker1s on 2007-02-19
you wont see anything as you type password to gain root access, just type your password and hit return.

---

### Post by geovino on 2007-03-07
I'm being asked to login in as superuser and when I do I get this:

davek@davek-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
davek@davek-desktop:~$ 


I had already logged in to use synaptic. earlier something didn't uninstall right and synaptic froze up after that it wanted me to go to the terminal and use this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
I tired and it won't let me because It think I'm not in root but I am in root. How do I fix this?

---

### Post by chewearn on 2007-03-07
> **geovino said:**
> I'm being asked to login in as superuser and when I do I get this:

davek@davek-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
davek@davek-desktop:~$ 


You are not supposed to do this in Ubuntu.  Instead of trying to log into superuser, you are supposed to use sudo command (see below).

> I had already logged in to use synaptic. earlier something didn't uninstall right and synaptic froze up after that it wanted me to go to the terminal and use this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
I tired and it won't let me because It think I'm not in root but I am in root. How do I fix this?Try this:
```
sudo dpkg --configure -a
```You will get a password: prompt.  Type in your user's password, and hit <enter>.

---

### Post by yota on 2007-03-07
Try to use 'sudo':

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And remember to SBP! (Search the forum Before Posting) ;-)

---

