---
title: "sudo doesn't work"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by Hamster. on 2005-07-31
I've just installed Kubuntu 5.04.

During the install process I created a normal user account.

I can log in to KDE with no problems using that account, but whenever I try to do anything like run Kynaptic or do something as root in Konsole, it asks me for my password. 

I enter the USER password  (ie NOT root's) but it always says "incorrect password please try again".

I know I'm entering the right password, because the password worked to log in to KDE in the first place.

I checked /var/log/auth.log and it tells me the user is not in sudoers. I have no idea how to add a user to sudoers - shouldn't that have been done automatically by the install process when it asked me to create a user?

How do I resolve this problem? 

Additionally, in Konsole, `su -` doesn't work. I found an article about root being disabled, but I'm sure that root isn't disabled. I gave root a password during the install process and if I drop to a terminal using ctrl-alt-1 I can log in as root with no problems what so ever. Why can't I become root in a konsole window?

I'm rather confused.

H

---

### Post by kosmic on 2005-07-31
to add the user to sudoers do this :

Login as root : su -
user your favorite editor (nano,kate,emacs...)
kate /etc/sudoers

Look for a line that says :

root    ALL=(ALL) ALL

Bellow that line add your users. ex.: if your username is john then :

john   ALL=(ALL) ALL

save and exit, and now you can use sudo :) with your username

---

### Post by adwait on 2005-07-31
You can edit the sudoers list with
```
sudo sudoedit /etc/sudoers 
```

---

### Post by Hamster. on 2005-07-31
[QUOTE=kosmic]to add the user to sudoers do this :

Login as root : su -
user your favorite editor (nano,kate,emacs...)
kate /etc/sudoers
[/QUOTE]

Thanks for the instructions on modifying the sudoers file.

It has however raised another problem.

If I type `su -` in konsole, it doesn't work. It just tells me "su: authentication failure".
In order to edit the sudoers file, I had to jump to a terminal (ctrl-alt-1) and log in as root. Why didn't su - work from konsole? How do I fix it so that it does?

Thanks! Sorry for being such a nube

Hamster.

---

### Post by varunus on 2005-07-31
You shouldn't have the '-' after su.  That will cause an error.  Its just "su" in a konsole.

You can also boot into recovery mode and use "visudo" to edit your sudoers file.  Strange that you weren't added automatically...

---

### Post by kosmic on 2005-07-31
hum in ubuntu its possible to run su - in a console or in a terminal but in Kubuntu that is not possible, don't know why...

---

