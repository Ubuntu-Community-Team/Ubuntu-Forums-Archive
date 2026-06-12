---
title: "Install Sun's Java?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by apoth on 2007-05-23
I'm after installing Sun's JDK (>=1.5) but I need to install it via a command line and can't for the life of me find out what repository I need to add. Can anyone help?

Thanks

---

### Post by merlinus on 2007-05-23
Synaptic lists this in the regular repositories.  On my machine, anyway....

-merlin

---

### Post by taurus on 2007-05-23
Which release are you running?

```
sudo aptitude update
sudo aptitude install sun-java5.bin sun-java5-plugin sun-java5-font
```

---

### Post by apoth on 2007-05-23
It looks to be running feisty.

```
$ sudo aptitude install sun-java5.bin sun-java5-plugin sun-java5-font
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5.bin"
Couldn't find any package whose name or description matched "sun-java5-plugin"
Couldn't find any package whose name or description matched "sun-java5-font"
```

---

### Post by taurus on 2007-05-23
Try

```
sudo aptitude update
sudo aptitude install sun-java6-bin
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by apoth on 2007-05-23
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

---

### Post by taurus on 2007-05-23
Those lines are only the bottom third of the whole thing.  Can you scroll up and paste the whole file in there.

---

### Post by apoth on 2007-05-23
That is the whole file.

---

### Post by taurus on 2007-05-23
No wonder you can't install java.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove all the lines in there.  Now, paste these new lines in.

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```
Save the new file.  Then, at the prompt, run

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by apoth on 2007-05-23
Thanks, job done.

---

