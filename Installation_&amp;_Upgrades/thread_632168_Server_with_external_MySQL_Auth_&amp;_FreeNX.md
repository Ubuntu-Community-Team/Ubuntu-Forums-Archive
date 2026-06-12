---
title: "Server with external MySQL Auth &amp; FreeNX"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by bmhm on 2007-12-05
[FONT="Verdana"]Hi,

I'd like to do the following:
1.) Install Ubuntu 7.10 on an server (but non-server-edition).
2.) Auth users against an MySQL-Database, but keep groups they belong to locally saved
3.) Install FreeNX, but I don't wan't to add each user individually.
4.) Prevent users from hitting "hibernate" or "suspend"-Buttons.

Why store log-ins this way? Well, because the database already exists, and I really don't want users to remember two log-ins. This is an existing and working login for a online portal.

Also, I am still looking for a way to make users able to use KDE or Gnome on that Server, whatever they like. Is FreeNX the best way for this? And if yes, how do I make FreeNX accept those login information from an mySQL-DB?

All I'd like to have a server, where you can connect by SSH, graphically (windows rich clients) and choose your desktop - and all that by using existing log-in-data from a MySQL-DB on the net.

Thanks in advance,
--Ben[/FONT]

---

### Post by bmhm on 2007-12-05
*bump*

---

### Post by daflame on 2007-12-06
The answer to what you are asking for is yes this can be done.  Is it easy? No.  I will answer each of your questions as they come below:

> **bmhm said:**
> [FONT="Verdana"]1.) Install Ubuntu 7.10 on an server (but non-server-edition).[/FONT]
This is straight forward and I would recommend Gutsy desktop edition as this is the best version I have found on the net.  You can install both desktop environments, but I suggest choosing a login manager to match the default desktop environment for the local machine.  If you want FreeNX I would highly recommend a desktop edition OS, since I have heard many a horror story of people trying to resolve permission issues with server OS versions.  Many are resolvable, but not without nearly turning the security level down into a Desktop OS anyways.

> **bmhm said:**
> [FONT="Verdana"]2.) Auth users against an MySQL-Database, but keep groups they belong to locally saved[/FONT]
The first part is simple with PAM MySQL/NSS MySQL, but you may have to alter your database to comply with mcrypt style password hashing if it doesn't use it already (you can always just add a field and set it as well when you change passwords in the interm) and you need specific fields for this to work.  Having groups stored as a file may not be possible once changing to the MySQL database however, but group management will still function the same as always as long as you use the user/group programs in the system and don't try to edit the group file directly (This is a BAD programming practice anyways).

> **bmhm said:**
> [FONT="Verdana"]3.) Install FreeNX, but I don't wan't to add each user individually.[/FONT]
Some things just can't be avoided, for preexisting users you will either need to spend a little elbow grease and create a script to add them automatically or pay the money for a programmer to make one for you.  Otherwise, setting up each user individually may be unavoidable.
However, many of the setup hassles can be removed by adding the NoMachine keys and any default settings you want to the home directory skeleton that gets copied when a new user is created.  This is in /etc/skel.  This is one of the less known great things about Linux new user creation.  This will solve problems for new users, but not preexisting ones.

> **bmhm said:**
> [FONT="Verdana"]4.) Prevent users from hitting "hibernate" or "suspend"-Buttons.[/FONT]
This one is easy.  They can't do this if they log in over FreeNX.  Those buttons just aren't available.

> **bmhm said:**
> [FONT="Verdana"]Why store log-ins this way? Well, because the database already exists, and I really don't want users to remember two log-ins. This is an existing and working login for a online portal.[/FONT]
This is a good plan, but as in all good plans they either cost time or money.

> **bmhm said:**
> [FONT="Verdana"]Also, I am still looking for a way to make users able to use KDE or Gnome on that Server, whatever they like. Is FreeNX the best way for this? And if yes, how do I make FreeNX accept those login information from an mySQL-DB?

All I'd like to have a server, where you can connect by SSH, graphically (windows rich clients) and choose your desktop - and all that by using existing log-in-data from a MySQL-DB on the net.
[/FONT]
You can create an online NX portal site using the NX Web Companion which is freely available on NoMachine's website.  What they offer is mostly an example of what you CAN do with it however.  As for the access via MySQL and choosing of desktop environments, however, you will need to create an nxs file from MySQL for the web site to access.  This too will require a web developer.  You could always contract someone like myself if you need this done, but I'm not sure of your budget.

If you want you can check out the forum I have setup to have access to recent FreeNX .deb packages for Gutsy.  I have packaged these for everyone to use freely and provided a guide for those not using Gutsy too:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by bmhm on 2007-12-06
I thing I found out that you can use existing logins with FreeNX, no concerns so far, as FreeNX also uses PAM. I just found a good tutorial  which should make things easy.



But sadly, users DO see "suspend" buttons, and they DO work. I just tested it: Created new user, no specific rights, works. Argh.
Yeah, shutdown & Restart are gone, but suspend and hibernate are not.

But still I'd like administrators to see these buttons - how?

Thanks so far, your writing stile is great, I can understand it very easily :-)

Regards

---

### Post by daflame on 2007-12-07
> **bmhm said:**
> I thing I found out that you can use existing logins with FreeNX, no concerns so far, as FreeNX also uses PAM. I just found a good tutorial  which should make things easy.



But sadly, users DO see "suspend" buttons, and they DO work. I just tested it: Created new user, no specific rights, works. Argh.
Yeah, shutdown & Restart are gone, but suspend and hibernate are not.

But still I'd like administrators to see these buttons - how?

Thanks so far, your writing stile is great, I can understand it very easily :-)

Regards

Are you using Gnome?  I have used KDE and those buttons aren't available on the machines I log into.  You could also try to create a custom unix session creating a whole desktop and running gnome-session I think or whatever the start script is for gnome.  Sometimes that will prevent the gnome desktop from connecting to the hardware, but not always.  The only other option is to disable suspend/hibernate and have a script check the user's group rights and enable them if it's an admin.  I just don't know what happens if someone logs in after the admin, if they will be able to suspend then too...  I still think that if you are making a terminal server that you ought to disable those buttons globally anyways.  Those features should be reserved for laptops IMHO.

---

