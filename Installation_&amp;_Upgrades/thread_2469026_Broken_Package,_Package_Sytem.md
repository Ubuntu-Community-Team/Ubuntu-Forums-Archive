---
title: "Broken Package, Package Sytem"
date: 2021-11-17
forum: Installation &amp; Upgrades
---

### Post by aldo82 on 2021-11-17
[SIZE=3]Hi everyone,
I'm unable to  update 20.04  because the package system is broken

The answer in  Ask Ubuntu was to insert the following command:  sudo nano etc//apt/source.list/etc/apt/sources.list.d/yarn.list
But after inserting this command  there is an error message :
 "etc//apt/source.list/etc/apt/sources.list.d/yarn.list"does not exist"
[https://askubuntu.com/questions/1374544/broken-package-on-ubuntu-20-04](https://askubuntu.com/questions/1374544/broken-package-on-ubuntu-20-04)

Thanks in advance
Aldo[/SIZE]

---

### Post by KBar on 2021-11-17
Hi.

You're missing a leading slash&#8211;the "/" character&#8211;in your pathname and the pathname itself is repeated twice.

---

### Post by TheFu on 2021-11-17
Dude, that is NOT what the link says.  Details matter.
If you'd like help, show the exact commands run and the RELEVANT output from those commands, including the errors.  We don't need to see 50 lines of "everything is fine" output, but we do need to see the first 2 .... and the last 2 for each section  - use a <snip> so show that you removed stuff. 
Post the command AND output here, wrapped in code tags. Code-tags how-to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

Ok, the commands are:
```
sudo apt update
sudo apt full-upgrade
```
^^^^^^^^^^^^^^
Those are what code tags are show as here. We are used to seeing it, but you don't just type code:. 

And please copy/paste, don't type stuff.  Details matter greatly.

---

### Post by MAFoElffen on 2021-11-17
The reason to wrap output within code tags, is two fold. Unwrapped output does strange and sometimes harmful things to the Forum's system application. Secondly, it makes it easier for users to read.

These are what Code Tags look like: [noparse]```
<-- Put output within these Tags --> 
```[/noparse]

Either manually typing them, or go to the "Go Advanced" editor, highlight the text and use the '#' Icon to automatically wrap the highlighted text within those tags... (See attached photo's)

---

### Post by aldo82 on 2021-11-20
SOLVED.  Thank you for your help, in particular for the advice 

of kbar, which solved the problem.

---

### Post by deadflowr on 2021-11-20
You can mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

