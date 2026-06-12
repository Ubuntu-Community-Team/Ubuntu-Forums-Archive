---
title: "Trying to install Intel Compiler, but terminal won't allow"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by epicbattle on 2008-07-10
Alright, I am trying to get Intel's compiler which I think is called i_cc_p_10 or something, but when I do the install and it asks me for the password (in terminal) it won't let me type. I am, to my knowledge, under the root. I didn't find this in the any of the repositort stuff. I'm very new to ubuntu.Uou might find to be ironic that I am trying to download a compiler, and I can't install the darned thing. But everyone has to start somewhere. This is what it looks like when I click on the install icon (which reads install.sh)

1. Install as a root.
2. Install as a sudo to root.
3. Install as a current user.
h. Help.
x. Exit.
Please type a selection.

I choose 1 and press enter, this comes up:

Attempting to log in as root...
Password: 

This is where I can't seem to type anything.
Any ideas? Thank you. 
 

Ubuntu 8.04 Hardy
1.2 gHz
80gig
1gig ram
Athelon

---

### Post by Partyboi2 on 2008-07-10
you wont see the password on screen as you type it in, so go ahead and enter your password and press enter and see what happens.

---

### Post by fotoni on 2009-01-28
You could simply login as root and then begin installation.
 
user@abcd:~$ sudo su
[sudo] password for user: *********
root@:/home/abcd# ./install.sh

---

