---
title: "ROOT rights howto"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by dirkme on 2005-10-01
Hallo to all Ubuntu user,

I am wondering if somebody knows an answer.

I installed XMMS and wanted to add a new Vizual Plugin in the folder. But it says I do not have the rights?? How can I? When I installed UBUNTU 5.04 it never asked for a root password. And what I am gona do now?

I think a root password is a crucial thing with Linux.

Mayday.

2. When I installed things like GFTP with synaptic.... were are they?? They don't show up anywhere :???: 

Thanks for your help in advance

Dirk

---

### Post by adwait on 2005-10-01
Wherever you need to run a command which requires the root password, add the word sudo before it
eg: instead of chmod use
```

sudo chmod

```

It will ask for the pasword, use your own password there. Ubuntu by default, doesn't have a root account.

---

### Post by aysiu on 2005-10-01
[QUOTE=dirkme]Hallo to all Ubuntu user,
I am wondering if somebody knows an answer.
I installed XMMS and wanted to add a new Vizual Plugin in the folder. But it says I do not have the rights?? How can I? When I installed UBUNTU 5.04 it never asked for a root password. And what I am gona do now?
I think a root password is a crucial thing with Linux.
Mayday.[/quote] [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> 
2. When I installed things like GFTP with synaptic.... were are they?? They don't show up anywhere :???: 
Thanks for your help in advance
Dirk They're a whole bunch of places. You can usually launch apps by typing their names in a Run dialogue. For example, to launch Thunderbird, I type ```
mozilla-thunderbird
```

---

### Post by Emerzen on 2005-10-01
I find a root GUI/Nautilus file browser very helpful here, especially for us noobs.  Type the following into the command line:

sudo nautilus

A file browser will pop up w/ sudo priveledges...you can right click a folder->permissions and change away.  Of course, you do not want to change defalut priv's willy-nilly for security reasons.

---

### Post by aysiu on 2005-10-01
[QUOTE=Emerzen]I find a root GUI/Nautilus file browser very helpful here, especially for us noobs.  Type the following into the command line:
sudo nautilus
A file browser will pop up w/ sudo priveledges...you can right click a folder->permissions and change away.  Of course, you do not want to change defalut priv's willy-nilly for security reasons.[/QUOTE] You can also create a launcher that has the command ```
gksudo nautilus
```

---

### Post by Emerzen on 2005-10-02
Aysiu,

This is off topic but what's the difference between gksudo and sudo?  I know I have to use gksudo to open k3b.  If I use sudo it changes my .ICE authority files.  Thanks

---

### Post by aysiu on 2005-10-02
[QUOTE=Emerzen]Aysiu,

This is off topic but what's the difference between gksudo and sudo?  I know I have to use gksudo to open k3b.  If I use sudo it changes my .ICE authority files.  Thanks[/QUOTE] As far as I can tell, *sudo* has to be used in the terminal, whereas *gksudo* is a command that will launch a graphical prompt for your password to do something sudo style graphically.

So, if you're in a terminal, you can type *sudo nautilus* and you'll be prompted for your password, but if you create a launcher that has the command *sudo nautilus*, nothing will happen.

---

### Post by Emerzen on 2005-10-02
Excellent...thank you.

---

