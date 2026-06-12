---
title: "user name/password after installation?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by raghukr on 2007-12-17
I used the ubuntu 7.10 alternate CD and installed successfully. But there was no step to create first user. After  selection and installation of softwares, it installed bootloader and then asked to remove cd and boot into newly installed system. I had to go to rescue mode and create user. It this the way it works or have I missed something?

---

### Post by jken146 on 2007-12-17
I'm pretty sure that there is a step to create the first user.  I've no idea why you might not have seen that in the installation though.

---

### Post by raghukr on 2007-12-17
> **jken146 said:**
> I'm pretty sure that there is a step to create the first user.  I've no idea why you might not have seen that in the installation though.

Even I was hoping so, since all the installations I have done till now had this step -- including the 7.10 desktop cd. But somehow, with the alternate CD, it was not there. I even reinstalled it thinking I might have missed it. This time I choose expert mode. Even in the tasks lisk, creating user is not listed as one of the tasks.

---

### Post by Chuck77 on 2007-12-27
Hi,

I am facing a similar problem! I´ve installed ubuntu 7.10 from alternate CD. As I remember I have been asked for user/pw in text based installation dialog, but I am not sure about it, because I´ve tried to install it several times before with desktop cd but failed. 

In any case, when start the computer I see a logon screen and enter user/password, in my case user "chuck", and a password with 11 characters, small and capital letters and numbers. 
--> Access denied!

Now, I have the following (beginner) questions:
1) How can I enter the rescue mode and create a user?
2) Are there any system users (like root or admin) which I can use? Do they have a default password?
3) Are there any limitations regarding the password length? Maybe my password is too long with its 11 characters? 

Kind regards,
Chuck

---

### Post by Chuck77 on 2007-12-27
> **Chuck77 said:**
> 
Now, I have the following (beginner) questions:
1) How can I enter the rescue mode and create a user?
2) Are there any system users (like root or admin) which I can use? Do they have a default password?
3) Are there any limitations regarding the password length? Maybe my password is too long with its 11 characters? 


After reading some documentation, I think, I´ve found the answers:
to Q1) 
a) Press ESC after starting the computer. Select **recovery** (not rescue) mode.
b) Then I am logged in with root user. Entering a password is not necessary.
   Command: adduser <username> < password>
                     adduser <username> sudo
c) Command: reboot 

to Q2) 
There is a root user without a password (AFAIK).

to Q3) 
I still don´t know, but the mentioned password works fine.

---

### Post by wagoner on 2007-12-30
I just did an install of Kubuntu 7.10 with the alternate install cd and it does have a step to setup a user account.

It did not have a step to set the root password.  I looked at the documentation on the install cd and it says that sudo is enabled and that the root password can be set by 
sudo passwd root 

This doesn't work, since it asks for the root password.  My system dead now until I figure out how to get root access.

---

### Post by jken146 on 2007-12-30
You don't need to activate the root account.

Ubuntu uses sudo, which means that you type **sudo** before a command to run it as root.  You are then prompted for a password.  Use *your* password.

For more details see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

