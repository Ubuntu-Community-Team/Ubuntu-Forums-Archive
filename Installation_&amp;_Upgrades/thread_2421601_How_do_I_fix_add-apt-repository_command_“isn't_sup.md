---
title: "How do I fix add-apt-repository command “isn't supported” error in Ubuntu 18.04?"
date: 2019-06-24
forum: Installation &amp; Upgrades
---

### Post by springaprilday on 2019-06-24
As a disclaimer: I'm really new at this so I may have have some trouble understanding advanced concepts. Thank you for your help and understanding. 

I am trying to install Wine however when I run:
~~~
~$ sudo add-apt-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main'
~~~

I get: 
...LSB codename: 'bionic'.
This codename isn't currently supported.
Please check your LSB information with "lsb_release -a".
...

I've already tried (in order):
~~~
:~$ sudo apt-get install python3-software-properties
~$ sudo apt-get install apt-file
~$sudo apt install python-software-properties
~$ sudo apt-get update
~$ sudo apt-get install --reinstall python-software-properties
~$ sudo apt install --reinstall software-properties-common
~~~

(I followed the first two answers from <https://askubuntu.com/questions/38021/how-to-add-a-ppa-on-a-server>).  When I search for add-apt-repository, I get:
~~~
~$  apt-file search add-apt-repository

software-properties-common: /usr/bin/add-apt-repository
software-properties-common: /usr/share/man/man1/add-apt-repository.1.gz
~~~

How do I get add-apt-repository to work?

---

### Post by Dennis N on 2019-06-24
Your command should end with 'bionic main', not 'cosmic main'
'cosmic' refers to Ubuntu 18.10

---

### Post by again? on 2019-06-24
You can add repository without using add-apt-repository.

Add 32bit architecture.
Add the signing key.
```
sudo dpkg --add-architecture i386
wget -qO - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
```

Add the repository and update sources.
```
echo "deb https://dl.winehq.org/wine-builds/ubuntu/ [COLOR="#FF0000"]bionic[/COLOR] main" | sudo tee /etc/apt/sources.list.d/wine.list
sudo apt update
```
Use [COLOR="#FF0000"]your release[/COLOR] codename in above command.
```
lsb_release -cs
```

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

