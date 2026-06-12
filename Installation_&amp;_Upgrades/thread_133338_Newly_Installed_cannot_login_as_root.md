---
title: "Newly Installed/ cannot login as root"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by treeflyr on 2006-02-20
It may have been something I mis-typed during install process.

I was able to access the installed partition and copy an encryption string
from /etc/shadow on my Suse10 system to /etc/shadow of my Ubuntu
install. I rebooted again under Ubuntu and still was not able to login as
root, which I need to be able to do.

---

### Post by el3ktro on 2006-02-20
root is disabled by default on Ubuntu. You need to give him a password first, with "sudo passwd". Sudo will ask for YOUR password, then you can give root a password. But in general, Ubuntu has the philosophy that everything is done with sudo.

Tom

---

### Post by sadjack on 2006-02-20
el3ktro

Can you explain why? I am new to Ubuntu but have used other flavous a linux for some time. I would like to get my head around the way Ubuntu treats root and the idea of sudo.

It seems strange to me that a user can download say gparted and use it without root permissions.

Thanks

:confused:

---

### Post by el3ktro on 2006-02-20
Well using sudo instead of a "real" root account is more secure. sudo allows you only to run single tasks as root, e.g. you may edit a config file in /etc by typing

sudo nano /etc/network/interfaces or
gksudo gedit /etc/network/interfaces

With sudo (SuperUser DO) only this one command is executed as root, and when you close nano/gedit, you're a normal user again.

When you use a real root acount, you'd type "su" to log in as root, and then ALL commands you execute are executed as root. This can lead to fatal situations when you for example just forget that you're logged in as root.

Another thing is that even if your system was exposed to the Internet, e.g. you accidental have some not needed service running, there's a bug somewhere, nobody could log in as root, because root isn't even enabled.

The downside is that you alays have to type YOUR password when you want to do something as root, but when you need some commands as root very often, or when you want to call them in a script, you can edit the file /etc/sudoers and configure Ubuntu in a way that certain commands can be executed with sudo but do NOT need your password to be entered. For example, I'm calling 'ifconfig' in a script to add a second IP to eth0, and this script is intended to run automatically, so I don't want to have to enter my password when I run it, so I configured /etc/sudoers so that ifconfig - and ONLY ifconfig can be run without entering a password.

Well, I hope this explains it a little :-)

Tom

---

### Post by Mustard on 2006-02-20
Here is a link that might help explain some more...

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-02-20
You may also want to take a look at the third link of my signature.

Interestingly enough, Mac OS X uses the sudo (not root) model, and no Mac users seem to complain about it...

---

### Post by tappad on 2006-02-20
Hi, i have a question..
I dont want every account to be able to use sudo, since all they have to do is to type their password.. What do i do?

Do i? :

sudo passwd root
sudo passwd -l root
and then:
"You can make sudo ask for the root password instead of the user password, you can do this by adding the keyword rootpw to the line in /etc/sudoers that starts with Defaults."

There must be an easier way?

Thanks..

---

### Post by infoseeker on 2006-02-20
I do 'sudo su' which gives me all the root access that I need.

---

### Post by aysiu on 2006-02-20
[QUOTE=tappad]
I dont want every account to be able to use sudo, since all they have to do is to type their password.. What do i do?[/QUOTE] Not every account has sudo access. The first account you create (during installation) has it. Then, when you create new accounts, if you put them in the "admin" group, they will also have sudo access. If you **don't** put them in the admin group... they won't.

---

### Post by tappad on 2006-02-20
[QUOTE=aysiu]Not every account has sudo access. The first account you create (during installation) has it. Then, when you create new accounts, if you put them in the "admin" group, they will also have sudo access. If you **don't** put them in the admin group... they won't.[/QUOTE]

Okay.. thanks for clearing that up!

---

### Post by treeflyr on 2006-02-20
Thanks to everyone for their courteous, prompt, and informative replies.

I will attempt the sudo trick, and figure out to ultimately get ubuntu to
accept a regular root login.

Also on sudo:  yes I find it to be a very handy configurable alternative to
logging in as root everytime I need root access.

My purpose for all the root access is to test my bootable backup perl
script (mkbkup.pl) in order to see if it can function on an ubuntu system.

Regards,
Treeflyr

---

### Post by sadjack on 2006-03-06
A good thread with lots of info for us Ubuntu newbies. Thanks everyone.

---

