---
title: "Problem Authenticating after Install of Ubuntu 14.04 alongside of Window 7"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by flnx on 2014-07-30
I have hp desktop 64bit with 500gb HD & 3gb ram ,Windows 7. I used unetbootin usb  flash drive to boot Ubuntu . I also tried Ubuntu prior to installing it.  Had no problem what so ever during testing.  I then decided to install it,  with ease and no errors or other problems encountered (my language selected was English US. I also used autmatic login  and set the passwd for authenicating.  I set up my email using Thunderbird with no hassles.  I then decided to install google's Chrome browser.  This is were I ran into problems.  After I chose the Chrome software (using Ubuntu software) I was unable to authenicate (incorrect passwd)using my password.  I have tried it again over and over, but no go.  I decided to make sure my keyboard was not on capital lock.  I then used text editor (which came with Ubuntu) to verifiy what I was typing was being received correctly, which it was. I also tried using the built in Ubuntu keyboard to no avail either.   tried to use the terminal access to see if it had a problem (entered sudo su , which requires password approval.  The outcome was the same, incorrect password.  I therefore decided to reset the password (found instuctions online physcocat.net , using passwd, etc....).  I successfully created a new password .  However, I still could not authenicate.  I ran the passwd reset several times and each time was successful, but still I have not been able to authenicate.  One thing I noticed while resetting paswd using root shell, entering command characters were not being inturrpeted correctlly as typed. (like entering a 'e' would get a w, entering 'p'  produce a diffrernt character, etc..)  So I found out what character generated the desired character for the comand and entered the command words that way.  But, still did not suceed in authenicating. I really need help on this weird Problem with Ubuntu.

---

### Post by ajgreeny on 2014-07-30
Is this the site you used for the info on resetting your password?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
If so, you must use the command ```
mount -o rw,remount /
``` which is easy to miss if you are not aware of it, that makes the filesystem read/write, allowing the password change.

If you have done all that I am a bit baffled; I was going to suggest a keyboard layout problem, but your text editor seems to eliminate that, so apart from checking the groups you are a member of with command **groups**, I'm not sure where to go next.

Don't forget also that your username must be correct in all ways and as far as I'm aware, no upper case letters are allowed in usernames, so check that as well as the password.

---

### Post by flnx on 2014-07-30
thanks for your reply.  I did include the mount line info prior to my other commands, but still did not work. Yes, I did get passwd change info from the site you indicated, and had no errors there, upon entering all.

---

### Post by flnx on 2014-08-03
Hello,  this is  both a update and a question re: my original Authenication Post last week.  I have managed somehow to fix the problem of password authenication.  I went thru the root password changing several times and each time i did receive a succesfull password change.  After repeated this, somewere it fixed it self. I can now use my keyboard to authenicate too.
 
Question though.  I still have to translate to Root, the command parameters I type in.  If I don't,  I get different characters from what I type and Root can not read my inputs.    I still have no idea how password Authenica failed after installation.  I would appreciate a feedback on why Root can not read my keyboard typing correctly.  Unless I subtitute representated characters for the desired characters I type. I am  pleased with the functions/operations using Ubuntu and I have no other problems/issues using this latest version 14.04.  I thank you for your ear/help and looking for your reply.

---

