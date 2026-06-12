---
title: "Password for the &quot;su&quot; command"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by tom122587 on 2007-07-27
So I wanted to install Java Runtime Environment for my Firefox, I clicked the instructions how to install it. Then the first step is go to terminal and type "su". It asked me the password. I typed my password for my user, but it shows "su: Authentication failure". I tried all other passwords I used before, and none of them work. :( Can someone help me please?

---

### Post by Pumalite on 2007-07-27
In Ubuntu you have 'sudo' and then the password. That allows to do work as root while you need it. Usually last about 10 minutes, then you have to enter the password again. In other cases you can try: 'sudo su'

---

### Post by tom122587 on 2007-07-27
Thank you. So if I want to reset my password for "su", how can I do it?

---

### Post by Evans132 on 2007-07-27
su requires the root password which is generated during the Ubuntu install.

Two easy options here:

1. You can either go into system->administration-> Users and Groups and change the root user password and use that or...
2. Use synaptic to install the JRE. (open synaptic and search for "jre")

I just did the second option myself earlier today

---

### Post by aysiu on 2007-07-27
There's about a 99.9999999% you'll never have to use *su* in Ubuntu. You may choose to for fun, but you'll almost never *have* to use it.

In this particular case, go to System > Administration > Synaptic Package Manager. Search for *sun-java6-plugin*, right-click it to mark it for installation, then click *Apply*.

---

### Post by dando80 on 2007-07-27
It's good practice to use sudo. If you really want to reset the root password, do "sudo passwd root", enter your own password and then enter the new root password when prompted.

---

