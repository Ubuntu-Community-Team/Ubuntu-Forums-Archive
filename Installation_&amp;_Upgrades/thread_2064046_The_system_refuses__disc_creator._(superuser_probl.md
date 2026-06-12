---
title: "The system refuses  disc creator. (superuser problem?)"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by elinvik on 2012-09-28
I was going to do a clean install of my computer using a bootable usb stick.

When trying to make the stick using disc creator the system refuses me from continuing. 
I get the message: 
 "System policy prevents mounting. An application is attempting to perform an action that requires priviliges. Auhentication as the superuser is required to perform this action" 

I've googled it ooover and over and getting nothing that works. 
Trying to change super user password, no luck. I was told I didn't need to have a super user with ubuntu so wtf?? 

So do I have to bike across town to my sisters house to create a bootable usb stick?? :( 
Any ideas? 
Btw I'm kinda new to ubuntu so simple english pleeeaase! :) 
All help is very appreciated!!!!

---

### Post by kc1di on 2012-09-28
as far as I can see disc creator is a Windows program won't run under linux. But I might be misunderstanding what your trying to do.

If you want to create a live usb stick to install Ubuntu from why not use unetbootin. you can find it here [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") for both linux & windows.
has always worked for me. 
If your in a Ubuntu machine you can install it from the software center. 
good Luck.

---

### Post by Wim Sturkenboom on 2012-09-28
Ain't there a popup asking for the password (which is your password)?

Ubuntu still needs a superuser; it would not even work without it. But what the message states is that you need superuser privileges; you elevate your privileges to superuser privileges with e.g. sudo.

---

