---
title: "Newbie needs help with Kernal"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by jacksparrow1 on 2008-08-21
Hey people,

I needed to install some drivers on my machine and after browing the web the only ideal way I could do this was by installing the ndiswrapper - however after checking their website I can see before I use  ndiswrapper I must install kernal.

So on my xp machine I download kernal 2.6.26.3 put it on USB and tranfer the folder to my ubuntu machine.  I copy and paste the folder on my desktop, unzip it and dont know what to do next.  Ive read the help files on the kernal but when I run the following coding:

gzip -cd linux-2.6.26.3.tar.gz I tar xvf

it says no such file or directory.

Any help please?

---

### Post by Ayuthia on 2008-08-21
> **jacksparrow1 said:**
> Hey people,

I needed to install some drivers on my machine and after browing the web the only ideal way I could do this was by installing the ndiswrapper - however after checking their website I can see before I use  ndiswrapper I must install kernal.

So on my xp machine I download kernal 2.6.26.3 put it on USB and tranfer the folder to my ubuntu machine.  I copy and paste the folder on my desktop, unzip it and dont know what to do next.  Ive read the help files on the kernal but when I run the following coding:

gzip -cd linux-2.6.26.3.tar.gz I tar xvf

it says no such file or directory.

Any help please?

You don't need to go that far to install ndiswrapper.  If you have the liveCD (the install CD for Ubuntu), you can do the following in the Terminal:
```
sudo apt-cdrom add
```It will ask you to insert your CD.  Use your liveCD.
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by jacksparrow1 on 2008-08-22
Really? That would be so awesome dude.

Well I tried what you said and this is what happened:

```

ubuntu@UBUNTU-PC:~$ sudo apr-cdrom add

```

It first asked me for a password, when I enter my password for my login it says the following

```

Sudo: apr-cdrom: command not found

```

Now when I try to run the above code again it doesn't ask me for a password again, it keeps showing the error again.

Any help or suggestions please? Thanks

---

### Post by DavidTangye on 2008-08-22
The correct  command is : ```
sudo apt-cdrom add
```

---

### Post by other guy on 2008-08-22
It is not apr. It is apt.. As in **apt**itude. Which is the name of the package manager. Just shortened a bit. Synaptic is the graphical version of aptitude. The command line is just simply apt.

Fix the minor typo in the syntax. It should fire off nicely.

---

### Post by DavidTangye on 2008-08-22
> **other guy said:**
> It is not apr. It is apt.. As in **apt**itude. Which is the name of the package manager. Just shortened a bit. Synaptic is the graphical version of aptitude. The command line is just simply apt.

Fix the minor typo in the syntax. It should fire off nicely.
No
```
dt@tex:~$ which apt-cdrom
/usr/bin/apt-cdrom
dt@tex:~$ man apt-cdrom
```

---

### Post by other guy on 2008-08-22
> **DavidTangye said:**
> No
```
dt@tex:~$ which apt-cdrom
/usr/bin/apt-cdrom
dt@tex:~$ man apt-cdrom
```

How is telling him to change apr to apt wrong? Or is it telling him what apt is, and options of it. The part that is no. I am not trying to be smarmy, just wondering what part is simply no.

---

### Post by jacksparrow1 on 2008-08-22
Guys I will give it a go in about 30 mins.

I'm sure I did try apt and apr was a type error on Ubuntu forums, anyway 30 mins.  Thanks

---

### Post by jacksparrow1 on 2008-08-22
Hi guys:

I done the following:

```

ubuntu@UBUNTU-PC:~$ sudo apt-get install ndiswrapper-utils-1.9

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following extra packages will be installed:

  ndiswrapper-common

Suggested packages:

  ndiswrapper-source

The following NEW packages will be installed

  ndiswrapper-common ndiswrapper-utils-1.9

0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.

Need to get 0B/30.4kB of archives.

After this operation, 213kB of additional disk space will be used.

Do you want to continue [Y/n]? y

Selecting previously deselected package ndiswrapper-common.

(Reading database ... 95844 files and directories currently installed.)

Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...

Selecting previously deselected package ndiswrapper-utils-1.9.

Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...

Setting up ndiswrapper-common (1.50-1ubuntu1) ...

Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...

ubuntu@UBUNTU-PC:~$ 


```

Does this mean ndiswrapper has installed?  Sorry if i sound like an idiot - it's just I've never even looked at a linux before.

If ndiswrapper has installed, what do I do to install the drivers of my wireless card? (I have the drivers on my cd that came with the card)  Thanks guys much appreciated.

---

### Post by jacksparrow1 on 2008-08-22
Anyone?

---

