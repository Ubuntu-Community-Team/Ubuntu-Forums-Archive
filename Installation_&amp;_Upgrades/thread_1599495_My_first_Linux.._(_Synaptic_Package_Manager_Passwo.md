---
title: "My first Linux.. :( Synaptic Package Manager? Passwords?"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Coedy on 2010-10-17
Hi Everyone! 
This is my first post! and my first ever attempt at running or using Linux!:)

I recently found my old laptop. Acer Travelmate 243LC.
Intel Celeron 2.5GHz
256MB DDR ram
30GB HDD.

I thought "Wow! Maybe this would be good to try Linux out on!"

After making a load of Live CDs (Ubuntu, Xubuntu, Lubuntu) It became clear to me that Lubuntu was the fastest for me on my hardware.

I tried installing it and it would hang before displaying the language selection screen (at the desktop).

I eventually found out I could try making a Mini.iso so that is what I did.
I followed all of the instructions and did it all.
(It is VERY scary for a Noob who has never tried Prompts before..)


It is now up and running! boots in under 30 seconds! shuts down in about 2 seconds! Great!:):guitar:


[SIZE="5"]_**BUT!**_[/SIZE]

I cant open Synaptic Package Manager. At all. not even a little.:(

It prompts me for my password. I put it in. the screen disappears and then pops back up saying my password is incorrect.

It is not incorrect. it is the same password I entered every time It has asked me to enter one in previously.

I checked my account was set as an administrator. it is.
I changed my password. still doesnt work.

Any tips?:(

I would like this sorted asap so I can actually try using Linux properly. As it is at the moment I cant follow the "keep Lubuntu up to date" guide because I cant put in the 'correct' password!!
:mad:

---

### Post by heatpumpcontrol on 2010-10-17
This should be your user name password. Be sure to note case sensitivity.

---

### Post by Coedy on 2010-10-17
Hi, 
Thanks for the quick response, but like I said Ive tried that password, but nothing. I checked in case I accidentally had capslock on but no luck :( 
Is there an easy way to check to see if I am running as root? or admin? or whatever it is asking for?

---

### Post by webtechquery on 2010-10-17
Try changing your root password. The following link would be helpful in letting you change your root password. May be this could help:

[http://www.webtechquery.com/index.php/2010/06/ubuntu-root-password-ubuntu-root-login/](http://www.webtechquery.com/index.php/2010/06/ubuntu-root-password-ubuntu-root-login/)

---

### Post by mathgeek2000 on 2010-10-17
Try this from a command prompt:

[COLOR="Red"]**sudo /usr/sbin/synaptic**[/COLOR]

It should prompt for your logon password and run the package manager as root.

---

### Post by aysiu on 2010-10-17
Please do not set a root password. That will just confuse things even more.

If you are certain you're an administrator, and you're certain you're typing your password in correctly (and have Caps Lock off), then it's possible your /etc/sudoers file is messed up. Here is how to fix it:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Coedy on 2010-10-17
Fantastic! Thanks a lot! Root password worked! :D

Just one quick question.
When I used Xubuntu, it didnt have Synaptic Package Manager? It had a different piece of software that was a lot more user friendly (or dumbed down). is it possible for me to install that via Synaptic Package Manager to use instead? or am I stuck with Synaptic?

Thanks again! :D

**EDIT-**

> **aysiu said:**
> Please do not set a root password. That will just confuse things even more.

If you are certain you're an administrator, and you're certain you're typing your password in correctly (and have Caps Lock off), then it's possible your /etc/sudoers file is messed up. Here is how to fix it:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Uh oh... I did it...? I am positive I am admin. (it says so in the user management section), I am positive I was using the right password because I was using it for other prompts and it was working (adding other admin users etc, to test the password was correct).

should I worry about setting the Root password?
Should I still try the link you gave even though the root password worked?
Is there anyway to disable the root account again???

---

### Post by mathgeek2000 on 2010-10-17
> **webtechquery said:**
> Try changing your root password.

The Root account in ubuntu is disabled by default, with no password. -- The Sudoers file -- /etc/sudoers is set up so members of the admin group can run files as root --> per the line ->

%admin ALL=(ALL) ALL

OK -- Geek speak for a newbie - maybe over your head ?
In short - whatever you may have chosen for a username, when you set up your PC should be able to run admin commands, via this group & it's password. (As opposed to other distros (OpenSuse) which prompt for a root password --> alternate model Knowing the root password gets you access).

---

