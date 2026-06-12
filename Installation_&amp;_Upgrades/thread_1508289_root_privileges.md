---
title: "root privileges"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-06-12
I have recently installed Ubuntu 10.04 and still having a number of problems. For example, I have tried toi use System->Administration->Users and Groups to allow me to have root privileges; but, I can not get this right.

* I am the only user on the system and I have administrator privileges
* I should be able to change anything on the system

However, if I try to save the environment file in /etc as environment_old, I get a message

[B]You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

[/B]I am very confused by this --- I wish to make a new environment file with the same attributes and save the old one as is.

--V

---

### Post by darkod on 2010-06-12
It depends how are you trying. Even though you are the main user and administrator, for your own protection your password will need to be entered again for some system commands.

For example, if copying some file is:

cp /path/filename /path/filename_old

for root privilege you need to:

sudo cp /path/filename /path/filename_old

---

### Post by virsto on 2010-06-12
Ok Darko,
I finally figured out how to use sudo to handle this (as you had in your message). But, why can this not be done using System->Administration->Users and Groups?

And by the way using help in Users and Groups does not show the correct screenshots.

--V

---

### Post by darkod on 2010-06-12
> **virsto said:**
> Ok Darko,
I finally figured out how to use sudo to handle this (as you had in your message). But, why can this not be done using System->Administration->Users and Groups?

And by the way using help in Users and Groups does not show the correct screenshots.

--V

You already have the sudo privilege. But that's how linux is designed, in a situation when you need to use it, you just use sudo and enter the password again.

You don't have it active all the time to prevent doing real damage by mistake.

Another note, for graphical programs, like the text editor Gedit, it's better to use gksudo, it has the same role.

gksudo gedit /path/filename

---

### Post by virsto on 2010-06-12
Thanks for the tip on gksudo --- never knew of this.
Note, I have now solved my other problem posted as

 **[COLOR=#980101][B][ubuntu]**[/COLOR]  LaTex Package install after Ubuntu 10.04 upgrade

[/B]These are the steps that I used (with your help):
1. Saved my old environment file as environment_old (just in case...)
2. Used ```
sudo chmod 777 environment
``` to allow full access to environment
3. Used Gedit to change environment to:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/share/texmf-texlive/tex/latex"

```

4. Used ```
sudo chmod 644 environment
``` to restore the original attributes to environment.

And Texmaker now works as it should --- finds my *.sty and *.cls files in folders in .../latex.

Thanks again darko and have a good day (well it is actually is 01:19 Sunday **morning** here in Stockholm).

--V

---

### Post by jwbrase on 2010-06-12
You could just use "gksudo gedit" to edit the requisite file without changing permissions. Also, you should be able to set your path in ~/.profile, which you should be able to edit without needing any kind of special privileges. (It's ~/.profile if you're using bash. You'll need to edit the file appropriate to whatever shell you're using, but bash is the default.)

---

### Post by wojox on 2010-06-12
Here's a good little explanation on root. [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

