---
title: "Gaim connection error"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Gouz on 2007-09-04
Hello folks.
Maybe someone has all ready answer this question but I couldn't find it so here I am asking.
I was away from my computer for about a week and when I come back I found out that I can't sent anything though Gaim internet Messenger I always got the same message : - Message could not be sent because a connection error occurred -


I tried Updating, uninstall and reinstall but nothing, all the other messenger kopete and the amsn are working normally.
Do you have any idea what can it be?

---

### Post by tszanon on 2007-09-04
> **Gouz said:**
> Hello folks.
Maybe someone has all ready answer this question but I couldn't find it so here I am asking.
I was away from my computer for about a week and when I come back I found out that I can't sent anything though Gaim internet Messenger I always got the same message : - Message could not be sent because a connection error occurred -


I tried Updating, uninstall and reinstall but nothing, all the other messenger kopete and the amsn are working normally.
Do you have any idea what can it be?
I don't know, maybe the msn protocol has changed a little, but I don't think so.
Have you tried Pidgin?

---

### Post by Gouz on 2007-09-04
What is that?

---

### Post by Pumalite on 2007-09-04
[http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

---

### Post by tszanon on 2007-09-04
> **Gouz said:**
> What is that?
Due to legal issues, gaim was terminated and the guys responsible for it started Pidgin. So, Pidgin is the "update gaim", if I may call it this way. Gaim is not under development anymore, and I think gaim users should stick to Pidgin.

Pidgin is already part of the default Gutsy installation, that will be released next month.

You can get Pidgin:
1. downloading the source, at [http://pidgin.im;](http://pidgin.im;)
2. there's this site GetDeb ([http://www.getdeb.net](http://www.getdeb.net)). Never used it, but people say they have an already compiled DEB package.

Have fun!

---

### Post by Gouz on 2007-09-05
Thanks :P
Now I have to find how to install it, since I am new to linux :P

---

### Post by Sef on 2007-09-05
> Now I have to find how to install it, since I am new to linux

Read [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Gouz on 2007-09-05
I found that, and some other info.
But I got the following message:

:~$ sudo dpkg -i pidgin_2.0.0beta7devel.vicox-1_i386.deb
dpkg: error processing pidgin_2.0.0beta7devel.vicox-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 pidgin_2.0.0beta7devel.vicox-1_i386.deb

---

### Post by tszanon on 2007-09-05
> **Gouz said:**
> I found that, and some other info.
But I got the following message:

:~$ sudo dpkg -i pidgin_2.0.0beta7devel.vicox-1_i386.deb
dpkg: error processing pidgin_2.0.0beta7devel.vicox-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 pidgin_2.0.0beta7devel.vicox-1_i386.deb
The package you downloaded is for 32bit Ubuntu. Here's what you have to do:
1. In GetDeb, in the top you'll find something like this (I translated it from PT-BR, so it may be a little different):
```
You are looking for software for Ubuntu Feisty (32 bits), you can choose another version
```
Click the link "version";
2. Choose the correct version (64 bits for sure, and since you're new to ubuntu, you probably are using Feisty, so, "Ubuntu Feisty 64 bits");
3. Click save;

Now you can download Pidgin. The package will have the correct architecture (AMD64).

---

### Post by Gouz on 2007-09-05
Thanks for the help I manage to install it.. but I still can send mesenges..
I still got the same error messenge:


Message could not be sent because a connection error occurred.


do you have any idea why?

---

### Post by tszanon on 2007-09-05
> **Gouz said:**
> Thanks for the help I manage to install it.. but I still can send mesenges..
I still got the same error messenge:


Message could not be sent because a connection error occurred.


do you have any idea why?
I have no ideas, but let's see what else we can find about it. If we are lucky, pidgin will give us a more detailed error message if we run it in the command line. I'm not sure, but I think the command should be just
```
pidgin
```
After running pidgin, repeat the steps in order to make the error happen again. Then, paste here whatever pidgin outputs in the terminal window.

When connecting, is there anything unusual, like any warning message?

---

### Post by donpoon on 2007-09-11
Don't know if you have solved the problem.

I experienced similar problem too.  Make sure you don't use HTTP method to connect to MSN.
i.e. Modify your MSN account and un-check "Use HTTP Method" under the advance tab.

However, I have to connect using HTTP method at work.  Still cannot find a solution to chat using HTTP method.

---

### Post by Jingo on 2007-09-12
Un-check worked here too.
Anyone know how to fix openwengo ?

---

