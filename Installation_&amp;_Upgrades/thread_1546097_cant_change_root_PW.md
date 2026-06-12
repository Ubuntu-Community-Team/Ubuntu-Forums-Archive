---
title: "cant change root PW"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by zerovnik on 2010-08-04
[LEFT]Quite sometime ago I dule installed windows and ubuntu on the same machien i stopped using it for a time and forgot the Root PW. i have gone to the grub and tried to reset the password by typing

passwd

enter password
retype password

etc.

at the end of all this some how it set a new password in the prompt to where now before i can use the above steps i have to type the password i had entered but when i boot normally i still cant login as root.

its driving be crazy and i dont want to mess more stuff up and make it even harder.
[/LEFT]

---

### Post by snowpine on 2010-08-04
Root login in Ubuntu is neither recommended nor supported. Any administrative task can be performed with "sudo" as described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by presence1960 on 2010-08-04
If you are talking about your user account password see [here]("http://www.psychocats.net/ubuntu/resetpassword"). 

If you are talking about the root password, snowpine is right on the money. 

There is a way to activate it, but forum policy strictly prohibits discussing how to do so because you are bypassing ubuntu's security measures.

There really is no need to activate the root password. You can use sudo and gksu (for graphical apps) you want to run as root.

If you had a valid reason to want to log in as root, you wouldn't be asking how to do it. You would already know how.

---

### Post by RamsesII on 2010-08-06
Hello zerovnik,

Presence1960 last line was clever. I hope you didn't take him wrong. 

What do you mean exactly by log into root ? Do you mean that you'd like *to graphically log into root* as you do for a regular user ? if so, root logging in console and graphically is deactivated by default on ubuntu for good security reasons. Now if you want to perform some tasks as root, the regular procedure in ubuntu is to log in as a regular user and then use a console to log into root with "sudo" to perform task as root. For example if you want to update your system, you should type in a console:
*sudo apt-get update*

The sudo command will prompt you to enter a password before. The password to enter is your current regular user password and **not the root password**. Only after that it will perform the update. The sudo command is very useful and safer to use than activate the root account and set it a password. **Which are not done by default on ubuntu**. Though you can still activate it and set a password. Hope this help. Keep me in touch till you get what you want.  ;-)

---

### Post by RamsesII on 2010-08-09
oops I already answered to that one.

---

