---
title: "What is my Root password ?"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by zeelog on 2012-09-30
I just installed Lubuntu as a user. It didn't ask me
 anything during the install about root, or what root
 password I would like. So now, when I need root to
 change /etc/fstab or /etc/rc.local, I can't. When I
 try to set up root admin in Users Accounts, it says
 there already is a root. Nobody said nothing to ME
 about setting up a root account. I'm just the owner
 of this computer, and the installer of Lubuntu. 
 Why should I be told about anything...
 So how do I find out what my root's password is ?

---

### Post by PaulW2U on 2012-09-30
The root account is disabled in Ubuntu, there is no password.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for a full explanation.

---

### Post by darkod on 2012-09-30
Calm down. When you try running system commands, ubuntu asks you again for the password with root permissions.

The first user you create during the installation has the root permissions by default. Only the account is not called officially root, your own account is used. So since you are the first user simply type your own password again.

Users you create later can also be added to have these permissions and run system commands with their passwords, but that is another topic.

---

### Post by critin on 2012-09-30
> **zeelog said:**
>  When I
 try to set up root admin in Users Accounts, it says
 there already is a root. Nobody said nothing to ME
 about setting up a root account. I'm just the owner
 of this computer, and the installer of Lubuntu. 
 Why should I be told about anything...
 So how do I find out what my root's password is ?

Use your user password--the one you log in with.  You are root, administrator,user.  Anytime it asks for a password, it wants your log-in password.

---

### Post by zeelog on 2012-09-30
Sorry. It was a stupid question. I should have tried
 harder myself to find the answer before bothering all of you.
 Thank you for all your relies. I need more sleep and less
 coffee. Anyway, the problem is solved.

---

### Post by critin on 2012-09-30
> **zeelog said:**
> Sorry. It was a stupid question. I should have tried
 harder myself to find the answer before bothering all of you.
 Thank you for all your relies. I need more sleep and less
 coffee. Anyway, the problem is solved.

No, it wasn't a stupid question--many have asked it.  Even I had an issue with passwording everything at first.  I couldn't see the need to password something only I ever touched.  I do now though.  :P

Asking is never a bother when you're learning.

---

### Post by hearthand on 2013-04-14
Running Ubuntu 12.10 and I don't see how any of the suggestions here helps.
I am trying to install a Lexmark Printer. The Install shell is asking for the Administrative Root Password
My Administrative Password is not what it is looking for.
I get this error when I use sudo passwd

   sudo: parse error in /etc/sudoers near line 23
   sudo: no valid sudoers source found, quitting
   sudo: unable to initialize policy plug-in

I have checked and sudo is enabled. I know my password. Even following the suggestions of changing the password from  the terminal I am blocked.

---

