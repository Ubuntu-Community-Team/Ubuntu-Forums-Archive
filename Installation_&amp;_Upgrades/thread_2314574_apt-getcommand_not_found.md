---
title: "apt-get:command not found"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by bradatan13 on 2016-02-22
Firstly, sorry if its wrong sub-forum but apt-get is used to install things. Secondly, im using a linux based on ubuntu 14.04. Just based.

So, im trying to install python. I typed the needed commands. At ./configure , i got the error "no acceptable C compiler found in $PATH". I tried to install tcc, but the "make" command didnt work ("make" command not found"). Afted typing "sudo apt-get make" i got another error: "sudo-apt: command not found". Anyone knows what i can do? Or at least what wget command i could type?

TL;DR
Command apt-get not working on ubuntu 14.04 based linux but wget works. Need how to fix or what wget command i need.

---

### Post by steeldriver on 2016-02-22
Any "linux based on ubuntu 14.04" should have both python2.7 and python3.4 already installed - be VERY cautious about installing a different version from source as python is tightly integrated into the system. Did you try simply typing

```

python

```
at the command line?

Your basic error with apt-get is that you are missing the part of the command that tells it what you want to do - for example

```

sudo apt-get **install** make

```

or (to install 'make' **and** the C/C++ compilers)

```

sudo apt-get **install** build-essential

```

---

### Post by MAFoElffen on 2016-02-22
+1, and...

If you are teaching yourself Python, try to stay to Python 3 conventions. With the upcoming release of 16.04, Ubuntu is trying to shift from Python v2.7 to v3.0. Only a few milestones left, then 2.7 will be able to be removed (and be gone). Just a thought.

---

### Post by goofprog on 2016-02-22
I would try it this way too.  It is a lazy way to get python.  
Get the dependencies first and then compile the source into a package and install it.  I guess it is dangerous in certain situations. The compiler tools get included from the dependencies.

---

### Post by oldos2er on 2016-02-22
Please tell us which distro you're using.

---

### Post by MAFoElffen on 2016-02-23
I'm following this... Just in-case the OP's interest in Linux turns into a questions or he needs help. Right now, since a misunderstanding on Python has been answered, is there any further questions?

Python is ingrained into Linux as part of the OS. (Unlike Windows OS'es where you would have to install something.) To install on a Win machine, an interpreter should be installed. Python itself is a powerful language,very underrated, and easy to learn.

---

### Post by oldos2er on 2016-02-23
> **bradatan13 said:**
>  Afted typing "sudo apt-get make" i got another error: "sudo-apt: command not found". Anyone knows what i can do? 

Wait, it looks like there was a typo in your command showing "sudo-apt". There's no hyphen between "sudo" and "apt-get". But the problem remains that we don't know what distro you're using; plus the fact that python (usually more than one version) is installed by default on most of the popular desktop distros.

---

### Post by oldos2er on 2016-02-23
> **goofprog said:**
> I would try it this way too.  It is a lazy way to get python.  
Get the dependencies first and then compile the source into a package and install it.  I guess it is dangerous in certain situations. 

Please stop making "dangerous" suggestions. Our goal is to help people, not make their problems worse.

---

