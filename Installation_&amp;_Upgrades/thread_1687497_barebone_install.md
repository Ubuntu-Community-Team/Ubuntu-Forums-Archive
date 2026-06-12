---
title: "barebone install"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by peterng25 on 2011-02-14
Hi all!

My first post here in this wonderful place.
I tried the barebone install, everything went great. I then ran:
sudo service gdm start
I then input my password, got a GUI login screen, as per psychocats.net tutorial.
I then logged in, tried opening Synaptic Package Manager, which of course asked for the administrator password.
So I entered the password that worked for the sudo command, and am told the password is incorrect.
Please help, is this a standard password (like 'penguin' or something, like that) or what am I doing wrong?
Thanks for the help!

---

### Post by An Sanct on 2011-02-14
Welcome to the forum!

The password *synaptic* asked you for is the same as you used for *sudo*, also the same, you *logged in *with.

Maybe your keyboard layout is changed (qwerty/qwertz), try to type your password somewhere else, so you can see it and than copy and paste it into synaptic.

The only thing I am aware of is the problem with very short passwords, If you use "abcd", that can be a problem! If so, try to change your password. You can go to System->Asministration->Users and Groups, there find your username and on the right you will see "Password:" and a "change" button besides it, try to modify your password there. (it might work there and not in synaptic ... that would be odd, but possible)


PS. There are no default passwords :)

---

### Post by peterng25 on 2011-02-14
Thanks!
I actually launched the terminal (Ctrl+Alt+T), then installed some software (I am a noob just learning my way around), and the sudo password works every time.
Now here's the puzzle: when I go to System > Administration > Synaptic Package Manager, this same password doesn't work??
 Very puzzling indeed, although it could be something simple...
Thanks for any input


Peter):P

---

### Post by An Sanct on 2011-02-14
Well, but synaptic should accept your password, if it does not, then something is wrong...

Can you run 
```
gksu synaptic
```
From the terminal and post if it gives an error?

---

### Post by peterng25 on 2011-02-16
I run **gksu synaptic** in terminal, get the following error:
An error occurred
...
E: Type '2011-02-15' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Goo to the repository dialog to correct the problem.
E: _cache ->open() failed.please report.

I tried to vi /etc/apt/sources.list but it's marked 'read only', of course I can't su or sudo because the (only) password I used during install is not recognized.
I am baffled, any help?...

---

### Post by An Sanct on 2011-02-16
> **peterng25 said:**
> I run **gksu synaptic** in terminal, get the following error:
An error occurred
...
E: Type '2011-02-15' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Goo to the repository dialog to correct the problem.
E: _cache ->open() failed.please report.

I tried to vi /etc/apt/sources.list but it's marked 'read only', of course I can't su or sudo because the (only) password I used during install is not recognized.
I am baffled, any help?...

Yes, to edit such an important thing as the sources list, you have to be admin :)
```
sudo vi /etc/apt/sources.list
```

PS. sorry, I couldn't help you much before, I didn't know, you are using medibuntu (!), that is an important piece of information if you want to get help ;) !!!

Take a look at [this tutorial]("https://help.ubuntu.com/community/Medibuntu") from canonical
Also take a look at [this page]("http://packages.medibuntu.org/") (packages for medibuntu)

---

### Post by peterng25 on 2011-02-16
Thanks for all the help

---

