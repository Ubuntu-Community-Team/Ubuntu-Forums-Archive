---
title: "javac - jdk 1.7.0 issue"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by Rephiscorth on 2011-09-11
hello everybody. Well, I installed th JDK 1.7 because i was asked to by my teacher at the university, to use it with eclipse. 

But after installing it, when i use javac in the console it wont work. it says: 

"the program 'javac' can be found in the following packages" 

and it shows a list of openjdk6 and some others. but that doesnt make any sense, since i could use javac before installing jdk1.7.

thanks (:

---

### Post by YesWeCan on 2011-09-11
Hi there. It should be inside your jdk directory:
jdk1.7.0/bin/javac

So you should either add this directory to your PATH or make a symbolic link to it in a directory that is already in your PATH, such as your home directory or for general access /usr/local/bin/

To see your paths in the PATH environment variable
[COLOR="DarkSlateBlue"]echo $PATH[/COLOR]
To add a new path
[COLOR="DarkSlateBlue"]PATH=$PATH:/new_path/[/COLOR]

To make a symbolic link in the current directory
[COLOR="DarkSlateBlue"]sudo ln -s /.../jdk1.7.0/bin/javac .[/COLOR]

---

