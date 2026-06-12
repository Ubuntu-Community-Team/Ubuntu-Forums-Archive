---
title: "Problem Installing Apache"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by Croquer on 2005-09-13
Hi im trying to install Apache Server in my ubuntu. Im writing in the terminal root the folowing line:

sudo apt-get install apache2

the answer is:

E: Type '$sudo' is not known on line 27 in source list /etc/apt/sources.list
E: The list of sources could not be read.

please help me....
Thanks

---

### Post by fcarmo3 on 2005-09-16
If you are in a root terminal, you don't need use the 'sudo' command.
This command is only for execute another command whit root's privileges.
So, in a user's terminal write:

sudo apt-get install apache2

and type the user's password, not the root's password.

The above command execute 'apt-get install apache2' with root's privileges.

good luck.

---

