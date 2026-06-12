---
title: "add-apt-repository not working? not installed?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by leesiulung on 2010-05-13
[FONT=Arial][SIZE=3]So I'm running what I believe to be the latest version of Ubuntu Server Edition 10.04 Lucid Lynx. 

**1. How do I find what version I'm running on the command line?**

As it is, Sun's JDK was removed so I need to add it per the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository").

However, following the instructions and running this command:
[/SIZE][/FONT][FONT=Arial][SIZE=3]```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```Computer reply's with "command not found". Running a whereis on add-apt-repository, it appears it is not installed.

**2. How do I fix this? **

I'm relatively new to the Linux world and help would be much appreciated....
[/SIZE][/FONT]

---

### Post by howefield on 2010-05-13
Find out the version you are running by typing the following into the terminal

```
lsb_release -a
```

---

### Post by leesiulung on 2010-05-13
> **howefield said:**
> Find out the version you are running by typing the following into the terminal

```
lsb_release -a
```

Thanks! How do I know if I'm running a server version or not.

---

### Post by colorlessprism on 2010-05-13
"sudo add-apt-repository ppa:<repository name>" this registers the  ppa with APT and an entry is created in /etc/apt/sources.list  and  backs up to /etc/apt/sources.list.save. ff a key is required and  available it is automatically downloaded and  registered. 

you must have  "python-software-properties" installed before using this command

---

### Post by leesiulung on 2010-05-13
> **colorlessprism said:**
> "sudo add-apt-repository ppa:<repository name>" this registers the  ppa with APT and an entry is created in /etc/apt/sources.list  and  backs up to /etc/apt/sources.list.save. ff a key is required and  available it is automatically downloaded and  registered. 

you must have  "python-software-properties" installed before using this command

it worked by adding "python-software-properties", but is there a way to manually add in the partner repository. How do I do that to avoid installing the python package?

edit: ohh, I see all it did was add the following line to the /etc/apt/sources.list file:

```
deb http://archive.canonical.com/ lucid partner
```

---

### Post by rewolff on 2010-06-30
I found out that one more thing is required, which was not mentioned in this thread. 

You have to have lucid. (I don't know if karmic works. I'm still at jaunty). 

In jaunty the python-software-properties package doesn't have add-apt-repository. 

In the case above, it just needed to add the line to apt/sources.list, in my case, getting the ppa signing key was useful as well....

---

### Post by swmiller6 on 2012-03-05
You do not have to add the repository you can download the deb for your architecture and manually install it.

---

### Post by oldos2er on 2012-03-06
Closed, necromancy.

---

