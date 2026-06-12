---
title: "Put javac in user path"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by goob on 2005-10-19
I'm new to Ubuntu but have used linux quite a bit.

I can't seem to get javac recognised in my path.

When I look for it in the path it does the following:

christopher@ubuntu:~$ whereis javac
javac:

The path to get to javac is:  /usr/java/jdk1.5.0_05/bin

How / where do I add this to my path?

export .... PATH = ....  in .bashrc  in my home directory
doesn't seem to work.

Thanks so much for bearing with me. I'm new to Ubuntu.

---

### Post by Murgle on 2005-10-19
when you have it in your .bashrc I believe that you need to log out before that reloads... or atleast close the old term and open a new one before it takes effect.

---

### Post by goob on 2005-10-19
Strangely when I try to get javac to work it can't find it. Yet javac is in the path as shown below:

root@ubuntu:/usr/java/jdk1.5.0_05/bin # echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/usr/java/jdk1.5.0_05/bin

root@ubuntu:/usr/java/jdk1.5.0_05/bin # whereis javac
javac:

I am using bash:

root@ubuntu:/usr/java/jdk1.5.0_05/bin # echo $SHELL
/bin/bash

I'm logged in as root so there should be no problem.  ????

---

### Post by MakubeX on 2005-10-19
Actually, I had been tinkering with this problem. It is weird when I tried SSH-ing on the same account in my terminal, it works! But it doesn't work upon the execution of the terminal (or the path to JDK isn't detected).

Therefore, I had put this statement:

PATH="${PATH}:/usr/local/jdk1.5.0_05/bin"

in the latter part of (/etc/bash.bashrc).

HTH.

---

### Post by goob on 2005-10-19
It still doesn't work.

Perhaps if I try it in /etc/environment ?

I've used redhat, fedora, and suse...and
never had such strange problems before.

java sdk was installed using suns' rpm
which was converted to a .deb package
using alien.

This is a really weird problem.

Also I can't log in to gnome desktop using
my root account...

weird weird weird....

---

### Post by Murgle on 2005-10-19
I believe that root login into gnome is disabled by default... not sure where to allow it though

---

### Post by MakubeX on 2005-12-11
[QUOTE=goob]It still doesn't work.

Perhaps if I try it in /etc/environment ?

[/QUOTE]

Yes, I had placed those statements in my /etc/bash.bashrc not in the .bashrc of my profile/account folder.

---

### Post by axle_foley00 on 2005-12-16
Hey guys,

I am having the same problem as goob. I tried what you said MakubeX and I get the following whenever I try to run javac:

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

Do you have any other suggestions?

---

### Post by bfonseca on 2006-01-03
On my computer I was able to edit the PATH by doing this:

sudo su 

go into  /etc

here is a bash.bashrc
to edit:

type:
gedit bash.bashrc

then at then end type 

PATH="${PATH}:*here is the path you wanna add*"

you can also edit the path using the profile in etc
 or the .bashrc

Hope this helps you
Brian

---

### Post by bfonseca on 2006-01-03
Another approach would be to download the automatix, here it automatically adds javac to the PATH.

Sorry I dont have the link.  I know it would be easy to find here in the forums just search for automatix.

Brian

---

