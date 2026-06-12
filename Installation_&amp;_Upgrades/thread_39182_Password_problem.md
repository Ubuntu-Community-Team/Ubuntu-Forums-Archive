---
title: "Password problem"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by Chan on 2005-06-03
In my anxiety to install Ubuntu, I apparently screwed up entering Usernames and Passwords.  (I won't bore you with a lot of details).  Is it possible to enter corrected new Usernames and Passwords, without having to completely re-install Ubuntu? 
 
I can't seem to get past the initial splash that's asking me for the username and password.  If could get into the load commands, and knew what commands to use, I'd be able to save repeating a weeks worth of effort. 
 
Perhaps I'm not the first to get into this pickle, and somebody can pass along how to pick myself up, dust myself off, and continue on my way to enjoying Ubuntu.  Thanks, Chan  ](*,)

---

### Post by jdodson on 2005-06-03
[QUOTE=Chan]In my anxiety to install Ubuntu, I apparently screwed up entering Usernames and Passwords.  (I won't bore you with a lot of details).  Is it possible to enter corrected new Usernames and Passwords, without having to completely re-install Ubuntu? 
 
I can't seem to get past the initial splash that's asking me for the username and password.  If could get into the load commands, and knew what commands to use, I'd be able to save repeating a weeks worth of effort. 
 
Perhaps I'm not the first to get into this pickle, and somebody can pass along how to pick myself up, dust myself off, and continue on my way to enjoying Ubuntu.  Thanks, Chan  ](*,)[/QUOTE]

yes, you can reset passwords for user accounts, etc, using single user boot mode.  

this redhat link will work: [http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html)

even though its redhat, and a bit old, its still pertanent as redhat uses grub and so does ubuntu.  so after you boot into single user moder type:

passwd <username>

and enter the password twice.

hope that helps.

---

### Post by Chan on 2005-06-03
Thanks, jdodson.

Will this allow me to reset the Username, and Password for the Root user, Normal user, and New user, because I apparently fouled  all of them?

I'll go check out that link to Redhat pronto.  Tnx agn, C   :grin:

---

### Post by mingus on 2005-06-03
Well, hello again Chan!

I am assuming you did not change the Login Screen Setup to allow root login, which would be the fastest way to resolve this.

I'm sure there is more than one way to do this, and this is a bit of a kluge, but it works:

First, get in as root.  Boot from the GRUB menu, choose recovery (if no menu, hit escape), this will take you to a root password prompt.

If you don't have your root passord, check the Start Guide [www.ubuntuguide.org](www.ubuntuguide.org) for how to get it without it.  Make sure once you are in that you have set a root password.

Once you are in as root, then do
#adduser
you will be prompted for a user name, password, blah blah.
now do
#gdm
you will be given the login screen, login as the newuser/password you just added

Once in Gnome, go to Applications/System Tools/Run as different user.  Run "users-admin" as user root, it will prompt for the *root* password, and you'll be at the screen to add/change/delete users.

Voila!

---

### Post by Chan on 2005-06-03
Incredible!  I sure have good vibes about this Ubuntu Society that I've joined.  There's so many people that are more than willing to help a guy out.  For this I'm mighty grateful, and look forward to doing the same for somebody.

Have a great weekend, all.  Chan   \\:D/

---

### Post by Chan on 2005-06-04
[QUOTE=mingus]Well, hello again Chan!

I am assuming you did not change the Login Screen Setup to allow root login, which would be the fastest way to resolve this.

I'm sure there is more than one way to do this, and this is a bit of a kluge, but it works:

First, get in as root.  Boot from the GRUB menu, choose recovery (if no menu, hit escape), this will take you to a root password prompt.

If you don't have your root passord, check the Start Guide [www.ubuntuguide.org](www.ubuntuguide.org) for how to get it without it.  Make sure once you are in that you have set a root password.

Once you are in as root, then do
#adduser
you will be prompted for a user name, password, blah blah.
now do
#gdm
you will be given the login screen, login as the newuser/password you just added

Once in Gnome, go to Applications/System Tools/Run as different user.  Run "users-admin" as user root, it will prompt for the *root* password, and you'll be at the screen to add/change/delete users.

Voila![/QUOTE]
----------------------------------------------------------------------------------------------------
I had some difficulty finding the passage in the Start Guide that deals with - "...If you don't have your root password, check the Start Guide [www.ubuntuguide.org](www.ubuntuguide.org) for how to get it without it...."  

The Start Guide is so comprehensive that any reference to the Root Password eluded me.  If you could give me a specific reference to the section that deals with the desired Root Password, it would sure be appreciated. 

Thanks, Chan

---

### Post by mingus on 2005-06-04
First 3 questions this section, depending on what your root situation is now

[http://www.ubuntuguide.org/#rescuemode](http://www.ubuntuguide.org/#rescuemode)

and here

[http://www.ubuntuguide.org/#allowrootlogingnom](http://www.ubuntuguide.org/#allowrootlogingnom)

---

