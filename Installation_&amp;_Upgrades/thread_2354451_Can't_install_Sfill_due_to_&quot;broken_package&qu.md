---
title: "Can't install Sfill due to &quot;broken package&quot;"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2017-03-02
I'm running Lubuntu 16.04.2 from a flash drive on a Dell Inspiron 660 PC.

I went to Synaptic Package Manager to install **sfill**, but when I tried, I got this error message:


[ATTACH=CONFIG]273960[/ATTACH]


I used the "Fix Broken Packages" feature in Synaptic Package Manager, but it didn't seem to do any good.

Suggestions, please.

---

### Post by Bashing-om on 2017-03-02
steve169; Hello'

When the going gets tough, the tough go to terminal :)

Post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
And we know the state of the package management system, Telling us what the condition is.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by steve169 on 2017-03-04
Dear Bash-om,

Attached is the readout of the commands you specified.

---

### Post by Bashing-om on 2017-03-04
steve169; Hey !

Looks to be golden now :)

What now results in doing your app install:
( libgsecuredelete-dev, libgsecuredelete0/, secure-delete )

updates
[INDENT][INDENT]can and do wonders
[/INDENT][/INDENT]

---

### Post by steve169 on 2017-03-04
Dear Bashing-om,

I'm kind of a newbie, so I have a basic question re: "( libgsecuredelete-dev, libgsecuredelete0/, secure-delete )":

Are those three separate commands for running in Terminal?

---

### Post by Bashing-om on 2017-03-05
steve169; Well...

Be aware I do not use a GUI for package management .
In your synaptic you show " sfill " as desired to install;
OK,
I look from terminal :
```

sysop@x1604:~$ apt list sfill
Listing... Done
sysop@x1604:~$

```and I have no return, indicating no package by that name .. so synaptic is aware of it and I want to know more :
```

sysop@x1604:~$ apt search sfill
Sorting... Done
Full Text Search... Done
libgsecuredelete-dev/xenial 0.2.1-2 amd64
  wrapper library for the secure-delete tools - development files

libgsecuredelete0/xenial 0.2.1-2 amd64
  wrapper library for the secure-delete tools

secure-delete/xenial 3.1-6ubuntu1 amd64
  tools to wipe files, free disk space, swap and memory

sysop@x1604:~$ 

```

Now to delve deeper :
```

apt show libgsecuredelete-dev
apt show libgsecuredelete0
apt show secure-delete/xenial

```

Now as a " I'm kind of a newbie" : are you sure you even want to go here ? And for what purpose ?

[INDENT][INDENT]this is linux
[INDENT][INDENT]it gets as deep as you want to go
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steve169 on 2017-03-05
Dear Bashing-om,

[B]Re: "Now as a 'I'm kind of a newbie': are you sure you even want to go here ? And for what purpose ? This is linux -- it gets as deep as you want to go."
[/B]
Yes, I see what you mean. Thanks for the reality check. I'll stay with the simpler stuff.

Many thanks nonetheless.

---

### Post by Bashing-om on 2017-03-05
steve169; Hey ;

As long as you have a fully functioning system in a consistent state and are in a happy state.
I am tickled .

If the above is a true statement, then:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Open up a new thread on any thing else that you have a concern about .

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

