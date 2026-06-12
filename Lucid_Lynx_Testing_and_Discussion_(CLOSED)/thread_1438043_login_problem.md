---
title: "login problem"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eekfonky on 2010-03-24
after the last update i restarted my computer. when  i reach the login screen i enter my name and password and i get taken in circles back to the login screen. please help

---

### Post by puchat3k on 2010-03-25
I'm also affected by this bug or problem. There's no mention of this issue on lunchpads bugtracker.

Yesterday I updated my system and put it to sleep. After waking it up the system rejected my login attempts. I tried going into recovery mode and upgrading my system, and changing the password with the passwd command.
The command just outputs a system error without any real detail.
It's not just gdm that is affected. After changing to a different tty I can't login to the command line also.

I can't seem to file a bug report because I can't login into the system.

Any help would be greatly appreciated. I'm willing to provide more details to anyone who has the expertise to track this issue down.

I'm running lucid lynx beta 1 installed from scratch on launch day, i386 desktop version. Latest kernel (can't remember the exact number).

Regards

---

### Post by eekfonky on 2010-03-25
If you hit CTRL+ALT+F1 at the login
enter your username and password
then do:
```

sudo apt-get install gnome-desktop-environment
```

It will work, it's currently not displaying some icons on my taskbar and and a few applets say, "delete" "Don't Delete' option, but you can at least "see" what's going on

---

### Post by puchat3k on 2010-03-25
That's the problem - I can't do that. :-)
CTRL+ALT+F1 switches me to the terminal - I can't login there too. So inputing any commands is out of the question.

When during boot I choose recovery mode I have access to a root shell but I lack the time (I'm at work) to properly diagnose the issue. Changing the password for my user in recovery mode by using passwd myusername doesn't work. The system returns an error.

My guess is that something is borked in one of the key packages of the system as: passwd, pam or someting else responsible for user authentication.

---

### Post by deebo32 on 2010-03-27
Having this same problem...

Installed server beta1 just couple hours ago, after the installer finished i couldnt login to the server so i thought i managed to typo the password twice in the installer

So I reinstalled with a really simple password i made sure i typed right without caps lock on... and i still cant login to the server...

tried rescue mode, but trying to change passwd fails with passwd spewing an error, creating a new user does the same, the user gets created but it has no password apparently...

trying to upgrade my home servers hardware and going upto 10.04 at the same time but no luck so far

---

