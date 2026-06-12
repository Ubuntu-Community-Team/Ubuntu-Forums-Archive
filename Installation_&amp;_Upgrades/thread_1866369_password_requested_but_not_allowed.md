---
title: "password requested but not allowed"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2011-10-21
Dear readers,
I am facing a lot of problems after installing the new Ubuntu 11.10. One of them is that I am not allowed to install new software; when I try to do this, I am asked the usual password (this time I was choosing a short password : "1"). When I type the password I am told that it is wrong and cannot go any further.
This is perhaps that I was cancelling a file in a certain window, a file related to password. But unfortunately I do not remember what I exactly did.
Now I would like :
1) to cancel any password need on my PC
2) if the 1) is not possible, to go to the old password.

Thank you for a help

---

### Post by 23dornot23d on 2011-10-21
Have a look at the list below .... looks like the Xauthority problem .... there is a solution at the top
of the thread marked below in my footer in red  ..... for failed upgrades

If its not this then someone else may help you on this .... one .... 

are you sure >>>> no caps lock or num lock is on too >>> when entering the password

---

### Post by telegiovi on 2011-10-21
thank you for your answer. Yes I am able to log in and to run ubuntu.  But I am NOT able to install new software. This is the problem

---

### Post by raja.genupula on 2011-10-21
Hi could you please tell us what you wanna install and give us the output of ```
sudo apt-get update
``` 

all the best.

---

### Post by telegiovi on 2011-10-21
roberto@roberto-EL1850:~$ sudo apt-get update
[sudo] password for roberto: 
Sorry, try again.
[sudo] password for roberto: 
Sorry, try again.
[sudo] password for roberto:

---

### Post by oldos2er on 2011-10-21
Try [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) to change your password, and I would encourage you to make it at least four alphanumeric characters, if not more.

---

### Post by 23dornot23d on 2011-10-21
[ answered same time - good reply if they do not need the password to change it back ]

although the root password should be different to the user password any way ..... if they set one up .....
ok I did not realize you could do it that way ..... good to know .....

I think I know whats happening here ...... 
seen this before ..... 

When a user creates a second new user and then deletes the main user off the
system .......... or modifies the password for the main user .....

The main users password carries over ...... 

Ended up with me needing two different passwords ......... and it ddi get confusing. 


It seems a strange case you can log in using your password but not use sudo ......

[Sudo would come uip with and error if you were not in the sudoers list  ..... so ......
this is strange/odd .....] 

( Trying to help here .... )

Do you have multiple passwords/users on your system ..... 
or have you removed any users or changed passwords recently ? 

Have you tried any other passwords you may have for the system ..... ?

just a thought - hope it helps ....

**I once ended up with two different passwords ..... one was left over from a deleted user on my system and that deleted users password took me in ........**

---

### Post by telegiovi on 2011-10-21
I tried the way suggested by oldos2er but I receive the answer "errore manipolazione token di autenticazione" (yes my ubuntu is in italian).

Yes I installed Ubuntu over Ubuntu and changed password. I tried to use the old password but didn't work.

Is also happened something strange at the end of the installation (yesterday): the picture on the screen
was the "old" one and not the "new" one.

---

### Post by telegiovi on 2011-10-22
after a new installation, now ubuntu seems to work properly. I have a problem because the USB port of the printer (multifunction printer Samsung scx-3200) is not being "seen". I tried to install and uninstall several times but the problem persists. How can I get the USB port being seen?
Thank you

---

### Post by nothingspecial on 2011-10-22
No one who knows the answer to your new question will know that your new question is in this thread.

Create a new thread with a title that refers to your question.

---

### Post by telegiovi on 2011-10-22
I'll do it

---

