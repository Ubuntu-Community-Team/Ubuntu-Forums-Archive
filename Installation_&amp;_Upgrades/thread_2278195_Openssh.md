---
title: "Openssh"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by giuseppe18 on 2015-05-14
Hello everyone! I'm trying to install a program that needs the ssh's command.
Then i write:
[U][I]hduser@giuseppe-Aspire-8935G:~$ sudo apt-get install openssh-server

[/I][/U]and the answer is:

[I][U]hduser non è nel file sudoers. Questo evento verrà segnalato.

[/U][/I](hduser is not in the sudoers file. This event will be report.)

There's something that i could do? It's only an error of mine pc?

PS:If i use ssh's command:

[I][U]hduser@giuseppe-Aspire-8935G:~$ ssh localhost
ssh: connect to host localhost port 22: Connection refused[/U][/I]

---

### Post by Lars Noodén on 2015-05-14
Only the system administrator(s) can install new programs.  You'll have to log into an account that has the right privileges or have someone else who does have that access do it for you.  Then after it is installed will you be able to log in remotely.  

Also, if you have UFW enabled, you'll need to open port 22 for incoming connections.

---

