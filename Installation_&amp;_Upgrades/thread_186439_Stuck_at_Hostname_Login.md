---
title: "Stuck at Hostname Login"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Wagz on 2006-06-01
I installed 6.06 and wiped out my previous install of 5.10.  When I reboot, it goes through the checklist and then gets to:

--------
Ubuntu 6.06 LTS ubuntuLaptop tty1

ubuntuLaptop login:
--------

(ubuntuLaptop being my very original hostname)

I didn't up a login for the hostname, though I set up a username/password for my user account, of course.  Anyone know what I did wrong in the setup?

---

### Post by llamakc on 2006-06-01
Uhm type in your username and when the password prompt appears type in your password.

---

### Post by johnc4510 on 2006-06-01
Remember, they are case sensitive.
Also if you have numbers involved, enable the numbers lock key on the keyboard

---

### Post by Wagz on 2006-06-02
Sorry, should have elaborated in the original post...I am unable to type anything at all, it's like the keyboard is disabled.

EDIT:  rebooted, and now it works, sorry for the confusion.  However, it boots into command line, how do I get my pretty GUI?

---

### Post by johnc4510 on 2006-06-02
Hum, not sure, sorry

---

### Post by fabe on 2006-06-02
Does this work?

[http://linux.slashdot.org/comments.pl?sid=187187&cid=15448678](http://linux.slashdot.org/comments.pl?sid=187187&cid=15448678)

quote:
Whenever I have seen this problem, of GNOME locking up as it starts the desktop, the following has fixed it (read and remember steps 2 and 3 before running step 1, because step 1 will make this text disappear):

    * hold control and alt and press F1 to get into a virtual console
    * pkill esd
    * hold alt and press F7 to get back to the GNOME screen

---

