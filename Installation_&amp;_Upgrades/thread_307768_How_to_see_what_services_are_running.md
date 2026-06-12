---
title: "How to see what services are running"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-11-27
I am a relatively new UBUNTU user

Down Loaded and installed the Lamp server version of Ubuntu 6.10


Trying to learn from the command Line

What is the Command  to see what systems are running 

bit confused about directory layouts and how to access them 

HELP:D 

Thanks Bill007

---

### Post by loell on 2006-11-27
in system menu --> administration --> system monitor

---

### Post by satish1482 on 2006-11-27
Just type top command in the terminal. U will come to know which programs r running in urs system.:mad:

---

### Post by Bill007 on 2006-11-27
sorry command line only  

This is a production server running only the base lamp system I have no graphical interface 

Using webmin 1.307 but not working properly so need to work from cammand line at the moment

So need the command line commands fro finding files and directories

Bill007

---

### Post by girishv on 2006-11-27
ps -aux | less
should give you the information on all the processes running by the user x and other programs which he can see.

ps -elf | less
to list all the processes running 
The number of programs are usually so many, they wont fit in one page of the terminal and the "pipe '|' and less" helps you to scroll them line by line or page by page.

Girish

---

### Post by Bill007 on 2006-11-27
Thanks for that girishv That a good start thanks for the heads up on the    | more  tip

Bill007

---

