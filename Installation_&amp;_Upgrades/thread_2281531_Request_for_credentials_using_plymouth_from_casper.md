---
title: "Request for credentials using plymouth from casper-premount"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by tempusfugit2 on 2015-06-07
Hello All,

I would like to ask for your help in the following matter, please.
I'm trying to have a prompt for credentials before the real file system is mounted and for this I have written a little script which I put in the casper-premount folder: 
I use plymouth (otherwise I cannot type when init stops) and I would like to store temporary the username and the password which are inputted to variables, anyway I cannot really understand the way to do this;
I though that following lines might work but that is not the case as I can see[INDENT]plymouth ask-question --prompt="Please, type the username to mount image repository:" --command="read USER"
plymouth ask-for-password --prompt="Please, type the related password:" --command="read PASSWD"
[/INDENT]

Would you have any suggestion on the way to achieve my purpose?

At the moment I use Ubuntu 12.04 LTS, but I plan to do the same also with later releases

Thanks in advance for your help.


Update:

Hello All,

I have found some info related to the possibility of  stopping plymouth during boot, thing that actually makes easier to  prompt for credentials and save the reply in variables, 
anyway I  would be still interested in taking advantage of the graphical  possibilities of plymouth: is there any guide on how to customize it,  that you know?

Thanks in advance for your help.


Update 2:

After some further digging around I found out that the correct format is the following:

PASSWD="$(plymouth ask-for-password --prompt "Please, type the username to mount image repository: ")"

In Ubuntu 14 this works perfectly either with ask-for-password or ask-question, while in Ubuntu 12 not really....still checking on that

---

