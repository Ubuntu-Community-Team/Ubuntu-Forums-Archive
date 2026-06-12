---
title: "New Install 7.04:  Cannot login"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by jedaven on 2007-05-23
I have installed a new 7.04 on my Dell Latitude laptop and I used the alternate CD because I don't have much RAM (128 Megs).  Anyway after the install, The username and password came up and it won't let me login with my chosen username and password.  I have looked at forums and tried everything I could find and nothing seems to work.  Should I reload?  Thanks.

---

### Post by apunc1 on 2007-05-23
are there any error messages?

---

### Post by jedaven on 2007-05-23
I am rather new at Ubuntu.  I have another machine with 7.04 installed but don't do much with it.  On the laptop I do not receive any error messages after the install.  The beige screen comes up asking for username and password.

---

### Post by apunc1 on 2007-05-23
what does the machine do after you enter in your username and password? just go back to the splash (login) screen?
are you sure you are entering the correct user name and password?

---

### Post by jedaven on 2007-05-23
I am positive I am using the correct username and password.  No special characters in either just letters and numbers.  After I enter the username and password is says.  Wrong suername and passowrd check caps lock etc.

---

### Post by apunc1 on 2007-05-23
ok make sure you have the correct username and password

 Boot into recovery mode. when grub shows up and gives boot selections choose a linux kernal that says (recovery) and type 

cd /home
ls
 
your user name should be listed

to check your password type
 passwd username where username is your username, and then reboot

---

### Post by jedaven on 2007-05-23
Your commands worked in recovery mode!  What happened was my actual name was appended to my username during installation!  I tried variations of that before but not the exact one!  I got in now so I can chage it back.  Thank you very much for your help!

---

### Post by apunc1 on 2007-05-23
Yay! you're welcome

---

