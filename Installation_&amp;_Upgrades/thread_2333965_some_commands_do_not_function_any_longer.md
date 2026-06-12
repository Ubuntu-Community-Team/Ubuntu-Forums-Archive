---
title: "some commands do not function any longer"
date: 2016-08-15
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2016-08-15
Good morning fellow ubunters):P
I am the grumpy type, I know I am. I regret upgrading from 14.04 to 16.04. When I try updating _ because you are not always informed of updates_ and the updater does not function properly _ it happens that it abruptly aborts without any explanation_ I try updating using the terminal. But with 16.04 you cannot do it anymore.

christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# sudo aptitude update
sudo: aptitude: command not found
root@hp1:/home/christophe# sudo aptitude safe-upgrade
sudo: aptitude: command not found
root@hp1:/home/christophe# sudo aptitude full-upgrade



I have a dream that someday, someone will come up with an operating system you only need update every three months. 

Have a nice Monday all of you. ;)

---

### Post by christon74 on 2016-08-15
Phew! I have just found the answer:
Ubuntu 16.04 uses the apt package manager.  To update from the terminal command line type in the following:
```
sudo apt update
sudo apt upgrade
```

But I maintain. 14.04 was better.

---

### Post by wildmanne39 on 2016-08-15
Aptitude does not come installed by default and it has not for a long time, I think you can still install it in 16.04 but I do not in my system I have no reason too.
```
sudo apt-get install aptitude
```
should do the trick if it is in the repo's still.

---

### Post by CantankRus on 2016-08-15
As far as I know you have to install aptitude in both trusty and xenial to use the **aptitude** command.
**apt** is supposed to be a more user friendly version of **apt-get**. You can still use  **apt-get** in xenial.
> The apt command is meant to be pleasant for end users and 
does not need to be backward compatible like apt-get(8).
[**_[COLOR="#B22222"]What is the difference between apt and apt-get?[/COLOR]_**]("http://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get")

---

### Post by Bucky Ball on 2016-08-15
Just throwing this in.

```
sudo apt update
sudo apt full-upgrade
```

... is more efficient than the combination you posted. See 'man apt' in a terminal for the difference. ;)

'apt' is not just a convenient abbreviation and innovation to replace 'apt-get' and aptitude. It is fully refurbished and more efficient. [See here]("https://www.maketecheasier.com/apt-vs-apt-get-ubuntu/") for more detail.

---

### Post by vasa1 on 2016-08-15
> **Bucky Ball said:**
> ...
'apt' is not just a convenient abbreviation and innovation to replace 'apt-get' and aptitude. It is fully refurbished and more efficient. [See here]("https://www.maketecheasier.com/apt-vs-apt-get-ubuntu/") for more detail.

The author of that page seems a bit over-enthusiastic.

---

### Post by Bucky Ball on 2016-08-15
> **vasa1 said:**
> The author of that page seems a bit over-enthusiastic.

Perhaps. 'man apt' is a more sober account, less flowers, says what it does. ;)

---

### Post by grahammechanical on 2016-08-15
> I have a dream that someday, someone will come up with an operating system you only need update every three months. 

One already exists. It is on your machine right now. All you have to do is change the setting to "never" and run Update Manager whenever you want to update.

---

