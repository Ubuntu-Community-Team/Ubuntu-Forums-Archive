---
title: "Most Administrator tasks don't work"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by khazmo on 2008-05-14
I am a Linux newbie, but so far I like the OS, I will not go back to windows, if they paid me. Being a newbie, I am not well versed in the system. 

After upgrading to Heron, some of my administrator tasks don't work. 

I tried to install some upgrades the system said I needed. The 'starting admin' button appeared on  the taskbar, but disappeared after a few seconds. 

I can access users and time and date, but those options say I need to unlock it, so I can perform the tasks. My login has admin privledges, so I am unsure of what to do.

Thanks in advance for any assistance provided.

khazmo

---

### Post by wpshooter on 2008-05-14
Please tell me what this "starting admin" button you refer to is ?

Thanks.

---

### Post by khazmo on 2008-05-14
When you open a window, whether it is Firefox or a game, there is a button on the bar at the bottom of the screen. For example, when I click on System> Administration> Update Manager, no window opens. There is just a button on the panel at the bottom of my screen that says: Starting Administrator....

khazmo

---

### Post by Partyboi2 on 2008-05-15
What happens if you try and start something with admin rights from the terminal? (Applications>Accessories>Terminal)
```
gksudo synaptic
```

---

### Post by khazmo on 2008-05-18
Thanks for the help. I was searching the forum and I found a way to fix it. I forgot where the info was, or I would post it here for others.

---

### Post by umor on 2008-05-18
Hello, 
I had the same issue, [and followed this form entry ]("http://ubuntuforums.org/showthread.php?t=723361") which solved the problem for me.
hth, UM

---

### Post by Lektorvis on 2008-05-27
!unable to perform any admistative tasks after kernel update incl. Synaptic!
Here is my solution

1) Type in Terminal: 

 my@my-laptop:~$ sudo gedit /etc/hosts

2) Output of /etc/hosts looked like this:

127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.1 my-laptop.Hønsehuset

3) I added the line "127.0.1.1 my-laptop" at top of the file and saved. The new file look like this:

127.0.0.1 localhost
**127.0.1.1 my-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.1 my-laptop.Hønsehuset

4) Problem solved.
[Inspired by this thread]("http://ubuntuforums.org/showthread.php?t=723361")

---

