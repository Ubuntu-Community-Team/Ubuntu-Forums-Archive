---
title: "Ubuntu Software Center Not Working Properly"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by vishal1875 on 2012-08-19
Hi I Am Vishal,
Actually I Stuck in a Problem which is related to The Ubuntu Software Center Which is not Installing any software which i select from the Software center, 
When i click over Instal Button it shows "Installing" for just 1 sec and then its gone back to normal means not installing, i have tried many commands on Terminal like 
Purged the Software Center and re-installed it again through some commands
Even Synaptic Package Manager is not working from Start Main Menu.

But When i use commands like following in Terminal they both applications works fine also installs that application which i choose to install:
1.     gksu software-center
 2.    gksu synaptic

I don't know why these applications not working properly as normal 
they just only works with commands in terminal not from Start Menu

I am Newbie  Ubuntu User. Plz Help Me 

My system Conf:
Xubuntu XFCE 12.04
Genuine Intel Pentium 4 Processor
1GB RAM
80GB HDD
256MB ATI Graphics Card

Rest all works fine, I love that OS, But only that problems me alot because of software installation

Thanks in Advance....:p

---

### Post by tommcd on 2012-08-19
Are you able to install software from the terminal using **apt-get**?
Can you post the output (in CODE tags #) of:
```

sudo apt-get update
sudo apt-get install my-app

```
where **my-app** is the program that you are trying to install.

EDIT: Starting the software center and synaptic with gksu starts the programs with super user privileges. When you start synaptic it should prompt you for your password to gain super user privileges.

---

### Post by vishal1875 on 2012-08-20
Yes i am able to do that Installation

---

### Post by vishal1875 on 2012-08-21
> **tommcd said:**
> Are you able to install software from the terminal using **apt-get**?
Can you post the output (in CODE tags #) of:
```

sudo apt-get update
sudo apt-get install my-app

```where **my-app** is the program that you are trying to install.

EDIT: Starting the software center and synaptic with gksu starts the programs with super user privileges. When you start synaptic it should prompt you for your password to gain super user privileges.

Yes i am able to do that Installation

---

### Post by tokijin on 2012-10-22
I'm running Xubuntu 12.10 amd64
I suspected that the problem was a permission problem so I've solved this matter changing the file $HOME/.config/autostart/polkit-gnome-authentication-agent-1.desktop

```
mauro@xQuantal:~$ cat -n $HOME/.config/autostart/polkit-gnome-authentication-agent-1.desktop 
     1    [Desktop Entry]
     2    Hidden=false
     3    
mauro@xQuantal:~$ 

```I'v changed the row #2 from
```
 Hidden=true
```to
```
 Hidden=false
```

---

