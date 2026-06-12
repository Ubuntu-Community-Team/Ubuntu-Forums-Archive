---
title: "Install and configure openssh"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by andrew.frederick.jackson on 2011-09-11
[SIZE=1]i'm new to ubuntu server so please forgive me for my ignorance. i've done a basic installation and have installed openssh using the following command:[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]sudo apt-get install openssh-server[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]i'm now trying to remotely login using putty on a windows machine that resides on the same network but i'm unable to do so.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]i've been looking through the documentation and searching the internet for step-by-step guide but have not found anything of any use.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]any help/advise would be greatly appreaciated![/SIZE]
[FONT=Arial][FONT=Verdana][SIZE=1][/SIZE][/FONT][/FONT]

---

### Post by tom4everitt on 2011-09-11
Hi,

The first thing you want to try after installing openssh-server, is the command
```

ssh localhost

```
which will check that server is up and running etc. 

If that works, you need to know your user name and the "node name"/"network name"/whatever of your computer. 

One way to find out your user name is the command
```
 
whoami

```

One way to find out your computer's node name is
```

uname -n

```

In putty the host name of the computer should be: nodename.local (appending .local to your node name). 

Try 
```

ssh username@nodename.local

```

in your Ubuntu terminal, to see that you got user name and host name right. 


Good luck - get back if you have further problems!

---

