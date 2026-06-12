---
title: "What's my root password?"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by diamond on 2005-11-26
I just finished installing Ubuntu 5.10. It asked me to create a personal account, and I am able to log in with that account. But at no point during the installation process did it ask me for a root password. I tried becoming root with the "su" command, and I tried my password (i.e., the one I used for my account), I tried an empty password, I even tried "ubuntu". No luck.

Is there some default password that it uses for root on installation? Or did I miss a step somehow? Is there anything I can do, short of re-installing from scratch?

---

### Post by aysiu on 2005-11-26
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

There is no root password.
Use your user password.

---

### Post by Juippisi on 2005-11-26
But you can get/change your root-password with *sudo passwd* or *sudo passwd root*. For example: 
sudo passwd
<your passwd>
<root's passwd>
<root's passwd>

And type to "root's passwd" whatever you like it to be. Then just *su root*

---

### Post by Littleweseth on 2005-11-26
out of curiosity, is there anything root can do that my normal self can't do via sudo? I think I read somewhere it's only things like reading password files and such that sudo won't let you do. (something to do with shadow/)

---

### Post by philry4n on 2005-11-26
i had quite a similar password
i tries using sudo in the terminal

i write 'sudo gedit', and then the system ask for my password
i insert mine and nothing happens
the gedit didn't show up

i tried inserting random characters and it replies "sorry, try again"
this message doesn't apeear when i insert my real pass but the problem is nothing happens
:(
help please 
newbie here

---

### Post by zootreeves on 2005-11-26
you cannot su root with ubuntu - there is no root user use sudo instead

---

### Post by fbongor on 2005-11-26
I also have this problem.  On doing some reading via google, I discover that Ubuntu developers have a certain attitude about how people "shouldn't want to" log in as root, so they've made it nightmare instead of an option.  I rebooted into single user mode and set the root password... this didn't help at all.  Later I found a page in the Wiki that explains that this renders all the gui tools unusable- apparently they get the root password from someplace other than the /etc/shadow file (I'm guessing).  There's no explanation of how to fix this problem.  I did discover though the option for allowing graphical login as root in the System->administration->login screen setup / security section.  Now I can log in as root, but I still cannot log in as myself and get access to any of the gui panels for configuration that require the root password, as this is apparently not "the" root password.  Gawd I hate it when people think they have a "better idea" and end up forcing it on everyone else.  Kinda like Suse taking telnetd off the system, or red hat moving all the directories around to suit themselves.

If anyone figures out where the "other" password for root is kept, I would really like to know where it is.

---

### Post by WebDrake on 2005-11-26
[QUOTE=aysiu]There is no root password.
Use your user password.[/QUOTE]
I have to say this is one aspect of Ubuntu I have never quite understood, since it seems to be compromising the traditional Linux security model.

After all, if someone can break into your user account, they can get your password, and a moment's check with sudo allows them to test if you have this privilege.

I appreciate the point that using the sudo technique and disabling root means the hacker cannot do things easily by just targeting root@...

... but surely the encouraged practice for Ubuntu, even for a single user, should be to set up an admin account which has the privileges to use sudo, *separately* from the daily use account?

---

### Post by aysiu on 2005-11-26
Did you read the link I linked to?
You don't have to agree with the decision made, but it is secure, and it's simple.

---

### Post by WebDrake on 2005-11-27
[QUOTE=aysiu]Did you read the link I linked to?
You don't have to agree with the decision made, but it is secure, and it's simple.[/QUOTE]
Yes, I read it and I appreciated the arguments made there on many grounds.  There's much about the use of sudo that is attractive.

Maybe I missed the following lines:

> Any user who uses su or sudo must be considered to be a privileged user. If that user's account is compromised by an attacker, the attacker can also gain root privileges the next time the user does so. The user account is the weak link in this chain, and so must be protected with the same care as root.
... which seem to say pretty much what I was saying. :rolleyes:

---

### Post by alma on 2005-11-27
I have got the same experience. Just installed Ubuntu yesterday evening and everything works fine. But I cannot switch to super user with su, because I have not got the password. My user password doesn not work.

Only if I do su username user pasword then I get in, but I don't know whether I then have su privileges.

Regards

---

