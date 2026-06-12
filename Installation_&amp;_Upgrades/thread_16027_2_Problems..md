---
title: "2 Problems."
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by Slay3r on 2005-02-18
Hi all,

I like the Debian system and just gave ubuntu a try and it looks like a great system but i do have 2 problems with it.

1)
It does not pick the network card up "VIA VT6103" so i cant access the net on that system.

2)
How do you login as root as the system does not ask to set a root password etc.

Q2 may have been asked many times but just put it in as i need Q1 answering lol

Thanks in advance.
Slay3r

---

### Post by DJ_Max on 2005-02-18
The root account settings are setup differently. The root password is the default user you created password. By default, you can't login as root. If you want root privileges, use *sudo* 

For the network card issues, run
ifconfig

---

### Post by Slay3r on 2005-02-18
Thanks, i found the root info on another post so got that sorted and the ifconfig responce is below and another question.

lo link encap: local loopback
    inet addr: 127.0.0.1 Mask: 255.0.0.0
    inet 6 addr :   :: 1/128 Scope: host
    up loopback running mtu: 16436 metric: 1
    rx packets: 13417 errors: 0 dropped: 0 overrruns: 0

    frame: 0 
    tx packets: 13417 errors: 0 dropped: 0 overruns: 0

    carrier:0
    collisions: 0 txqueuelen: 0
 
   rx bytes: 1651024 (1.5 MIB) tx bytes 1651024 (1.5 MIB)


and the new problem is if i go to
Computer -> System Configuration -> Networking 
and i put my root pw in when prompted i get the below error.

Error
failed to run network-admin as user root:
Child terminated with 1 status

---

### Post by WW on 2005-02-18
You may already know this, but just in case... In the "Changing user..." popup window that asks for a password, you must enter *your* password (not root's password).  It doesn't matter if you have set up a root password.  The Computer->System->Networking program is started with gksudo, so it is using sudo and expects the user's password, not the root password.

---

### Post by Slay3r on 2005-02-18
Yeah got it working now thnx

---

