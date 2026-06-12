---
title: "No root logon"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by Coomkeen on 2006-06-22
Hi All,
Complete beginner here. Just upgraded from 5 to 6, and the installation only asked me for 'my' logon name and password.
How do I get in as root?
I have an external USB hard drive which I can't write to as it says it's owned by root.
Fair enough, but I should be root as well as me!
Help appreciated.
Ron:???:

---

### Post by The-One on 2006-06-22
i think you can log in with user " oem "  then type the password that you enter it in the installation .... you will be logged in 

i hope i answer your question  .. im biginer too

---

### Post by user1397 on 2006-06-22
ubuntu disables the root account by default, read this for more info: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

as for your problem, try this: press ALT+F2, and type **gksudo nautilus**

this will give you temporary root permissions to nautilus, the file browser. then try going to the usb drive from inside that root window, and see if you can write to it now.

---

### Post by Coomkeen on 2006-06-22
Hey thanks guys.
All sorted.
Ron

---

