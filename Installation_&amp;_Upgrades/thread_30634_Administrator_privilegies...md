---
title: "Administrator privilegies..?"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by Sandokan on 2005-04-29
Some-times I need to copy some files in to directory or in uder direction...O.K. the question is how can I make the user I used to install Ubuntu administrator...
So I could do evrything I want with files...

Sorry for English...

---

### Post by brk3 on 2005-04-29
Ok.. quite hard to understand the english! But if you want to do what I think you want to do, its not a good idea at all. Do you mean you want to have root privalages all the time in day to day use??
Because this is a no no  [-X 
 ;-)

---

### Post by Fab on 2005-04-29
[QUOTE=Sandokan]Some-times I need to copy some files in to directory or in uder direction...O.K. the question is how can I make the user I used to install Ubuntu administrator...
So I could do evrything I want with files...

Sorry for English...[/QUOTE]
 sudo <command to run as administrator>

it will then ask for the password, and execute the command with superuser rights

---

### Post by Sandokan on 2005-04-29
But at log-in firestarter says that I dont have admin privilegies....so it want start at begining and I have to do it manualy....I would like to have some things working 100% no mater what....Shoul I use some uder firewall...

Thanx

---

### Post by Limulus on 2005-04-29
Coincidentally, I installed Firestarter yesterday and have been having the same (vexing) problem; I think the reason he wants user privileges is because of this thread: [http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter) (see post #2).

Basically, the problem is that if you're running Firestarter and you logout/reboot it tries to start it again, but not using sudo.  I followed the official Firestarter FAQ: [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php) as per getting it to restart with sudo from Sessions, which it does, but ubuntu *also* tries to restart it without (so one working instance and one failed one with the error ^_^; )

Now, if you shut down FS before you logout/shutdown ubuntu, when ubuntu restarts, there is no error message.

Is there a way to automatically shut FS down before ubuntu shuts down, or a way to prevent ubuntu from trying to restart it on its own, or a way to prevent ubuntu from loading FS if there's already an instance of it?

[Edit] A work-around that is less annoying than seeing the error on startup is to have FS in Sessions startup and just manually close it before you logoff/shutdown/restart.

---

