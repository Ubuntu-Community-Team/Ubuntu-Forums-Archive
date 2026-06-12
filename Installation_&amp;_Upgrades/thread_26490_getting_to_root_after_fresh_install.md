---
title: "getting to root after fresh install"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by martinez9049 on 2005-04-13
hi, i just installed ubuntu and when i try to go to root it asks me for a password. the problem is that i never set a root password. and the password for the user does not work. help please?

thanks,
ismael m

---

### Post by martinez9049 on 2005-04-13
UPDATE: when i go to the root terminal in apps and put in my password it works. if i just open up terminal and type in 'su' and put the password it doesn't work.

---

### Post by nad on 2005-04-13
The system is setup with sudo. To set a root password, open a root terminal from gnome. You will be asked for the sudo password which is your password. Once you have a root session, issue yourself a password. ' passwd '.

Dan M

---

### Post by yfarjoun on 2005-04-13
Same here. Just got through a fresh install and I have no idea what the root password is. I gave the installer a username + password for a regular user account and I can login with that, but I cannot su or login as root.

Thanks,

Yossi

---

### Post by MicroChris on 2005-04-13
```
sudo passwd root
``` 

to activate root password

```
sudo passwd -l root
``` 

to remove


-Chris

---

### Post by Buffalo Soldier on 2005-04-13
The no root user policy of Ubuntu is well documented:[list]
[*] During installation before/when the installer asked for a username and password, there is an explaination about no root user and sudo.
[*] And it also has been well discussed in here (forum)
[/list]

For further info and previous discussion on sudo:[list]
[*] [Sudo and the Root Account](http://www.ubuntulinux.org/wiki/RootSudo) from Ubuntu User Documentation Wiki
[*] [Sudo](http://ubuntuforums.org/showthread.php?t=25509) thread
[*] [how do you use su or sudo](http://ubuntuforums.org/showthread.php?t=24195) thread
[*] [ubuntu root password](http://ubuntuforums.org/showthread.php?t=23432) thread
[/list]

---

### Post by heimo on 2005-04-13
This is FAQ stuff. May I please politely ask you to search the forum, FAQ and wiki... :)

And the answer is that the root password is not set by default (at least not always). So you are supposed to do maintenance using sudo to run programs which need super user privileges. (for example: sudo gedit /etc/resolv.conf) (password for sudo is your users password)

Or if you really want to set password for root, do *sudo passwd root* but do not use it for anything else than maintenance and administration, no games, no web browsing. :) I don't want to sound evil, but you should understand that you can mess your system and harm your security by using system with root privileges.

Cheers!  :smile:

EDIT: Oh, had to leave my computer for couple minutes and when I came back to post this, there was already tons of answers, sorry for reduncancy.

---

### Post by yfarjoun on 2005-04-13
Thanks Dan, 

That works very smoothly.

I'm not sure how I was supposed to figure out that the regular user is allowed to sudo...if it was written anywhere in the installation I must have missed it....

Yossi.

---

### Post by martinez9049 on 2005-04-13
thanks....it worked just fine.

---

