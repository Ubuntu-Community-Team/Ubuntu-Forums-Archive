---
title: "Unable to sudo"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by vinodh on 2005-03-10
I wanted to change the root user name, hence I used the "Users and Groups" application in System Configuration and renamed the user. I then closed the "Users and Groups" application. Now if I try sudo, I get the following error:

Password:
adm is not in the sudoers file.  This incident will be reported.

I am unable to visudoer or modify /etc/passwd - again since I am not able to sudo.

I also tried to start the "Users and Groups" application to try and change the root username back to the original username, but the application never starts up now :(

Any help to get sudo working again will be much appreciated.

Thanx

V~

---

### Post by krusbjorn on 2005-03-10
did you try logging in as the whatever-username-you-set-root-to and change it back?

---

### Post by vinodh on 2005-03-10
Thanks for your reply.

I hadn't logged out of gnome till now. I logged in as the changed user via console and tried to use visudoers and modify /etc/passwd - got the same result as before (unable to sudo). 

Now I logged out of gnome, thought I would login as changed user and try to run the Users and Groups app. I couldn't login with the changed username or the old username. Luckily I had created some other non admin users and I am able to login to gnome with another username. I now tried to start the Users and Groups app. - It asks for root password. When I give the password, the app fails to load with the following error:

Failed to run users-admin as user root:
 Child terminated with 1 status

V~

---

### Post by GrapeApe on 2005-03-10
Let me understand, you tried to rename root?   Why?

Sounds like you are going to have to boot single user.  I'm not sure if that will prompt for the root password or not.  Haven't done it under ubuntu yet.   If it doesn't prompt for the password, it will take you into a root shell where you can then modify passwd or whatever. 

Since the root account doesn't have a password by default, I imagine it may not ask for it.

Under grub you should see two entries for your kernel.  One which is your standard boot.  I believe the other is called recovery.  That is a single user boot mode.  Try that.

---

### Post by vinodh on 2005-03-10
Ok. Thanx, it helped. Now I am able to sudo after rebooting in single-user (recovery mode) in GRUB and making the necessary changes in the /etc/passwd file and visudo files.

---

