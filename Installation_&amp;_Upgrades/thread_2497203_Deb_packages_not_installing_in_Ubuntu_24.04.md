---
title: "Deb packages not installing in Ubuntu 24.04"
date: 2024-04-26
forum: Installation &amp; Upgrades
---

### Post by Jurjen de Vries on 2024-04-26
Dear community,

I just installed Ubuntu desktop 24.04. Before I was able to doubleclick a deb package. Now when clicking a deb package I am getting an error:
Could not display filename.deb . There is no app installed for "Debian package" files.
This was working well before, and I have multiple deb files to install

Thanks for helping.

---

### Post by #&amp;thj^% on 2024-04-26
What about "dpkg -i some.deb" ....and "gdebi" just a right click open with gdebi.

---

### Post by ajgreeny on 2024-04-26
I just use 
**sudo apt install  /path/to/file.deb**
You must use the full path to the file or if it's in Downloads open a terminal in Downloads and run command 
**sudo apt install ./file.deb**
No need for gdebi or anything else.
You must use the ./ in that second command.

---

### Post by Jurjen de Vries on 2024-04-26
Thanks. That seems to be working. But any idea why it isn't working from the desktop anymore as it did before?

---

### Post by #&amp;thj^% on 2024-04-26
Things change very quickly with Buntu, New features added some Old ones removed.

My self like ajgreeny just get accustom to the terminal.

BTW which one worked for you?

---

### Post by hrsetrdr on 2024-04-26
> Deb packages not installing in Ubuntu 24.04

I read an article mentioning this just this morning off some Facebook link, I didn't have any problem installing a .deb file without first manually installing gdebi,just worked.

---

### Post by Jurjen de Vries on 2024-04-27
> **1fallen said:**
> 
BTW which one worked for you?

sudo apt install ./file.deb 
worked well for me

---

### Post by rememberthehill on 2024-05-16
Hello,

The dpkg approach did not work for me. I used apt install, too.

---

### Post by bambiemurphy85 on 2024-06-04
I used 

> sudo apt install gdebi

Worked for me easy and quick way to install DEB packages.

---

### Post by grahammechanical on 2024-06-05
In the past when you double clicked the deb file did Ubuntu Software load and in turn install the application?

In 24.04 LTS Ubuntu Software is in fact the snap store. It is not designed to install deb applications. We need to install Gnome Software to install deb package application using a GUI utility.

Regards

---

### Post by Claus7 on 2024-07-10
Hello,

> **grahammechanical said:**
> ... We need to install Gnome Software to install deb package application using a GUI utility. ...

thank you for that. Having an upgraded system I wasn't able to notice the problem, since gnome software was already installed in my system. In a fresh installation of noble though I noticed the issue and your proposal brought things back to normal.

Regards!

---

