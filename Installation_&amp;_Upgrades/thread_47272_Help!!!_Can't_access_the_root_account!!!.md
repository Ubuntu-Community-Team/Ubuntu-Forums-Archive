---
title: "Help!!! Can't access the root account!!!"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2005-07-08
I'm required to log in as root, but I'm not even offered to set a password for root!!!

I didn't have this problem with another distro. But I'm required to update my Linux distro, so I chose Ubuntu. 

I'm required to access a couple of administrive functions, thus this is the equivalent of having an account that don't have administrator rights with Windows!!!  :-x 

Does anyone know how to solve this problem with Ubuntu?

---

### Post by drummer on 2005-07-08
There is no root account in Ubuntu, instead you use the sudo command to gain root privaliges when issuing commands. The root account can be enabled if you really feel you need it (have a read here: [www.ubuntuguide.com)](www.ubuntuguide.com)), otherwise use sudo to do things as root in the terminal or specifically open a root terminal from Applications > System Tools > Root Terminal

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=drummer]There is no root account in Ubuntu, instead you use the sudo command to gain root privaliges when issuing commands. The root account can be enabled if you really feel you need it (have a read here: [www.ubuntuguide.com)](www.ubuntuguide.com)), otherwise use sudo to do things as root in the terminal or specifically open a root terminal from Applications > System Tools > Root Terminal[/QUOTE]

The domain name, ubuntuguide.com isn't recognised, thus a DNS problem!!!

Thus I can't access the web site!!!  :-x

Also, when using the **sudo**  command, I gotten an error message about being required to add the host name of my PC to the file /etc/hosts and I can't access it, because I can't log in with root priviledges!!!

---

### Post by drummer on 2005-07-08
sorry, the post insluded the ")" in the URL, and there's no "www", silly me.. here it is all on it's lonesome:

[http://ubuntuguide.com/](http://ubuntuguide.com/)

Using sudo or the Root Terminal should be sufficient though, rather than enabling the root account. Just remember to only use the root account when administrating and LOG OUT afterwards before doing anything else because when logged in as root you can do absolutely ANYTHING to your system.. including undesirable things by mistake that can break stuff  ](*,)

---

### Post by drummer on 2005-07-08
[QUOTE=RJARRRPCGP]Also, when using the **sudo**  command, I gotten an error message about being required to add the host name of my PC to the file /etc/hosts and I can't access it, because I can't log in with root priviledges!!![/QUOTE]
 That seems a bit odd with the hosts file, what are you running with sudo that gives you this message? The hosts file is the information from the hosts tab in "System >  Administration > Networking".

---

### Post by drummer on 2005-07-08
Sorry again.. I just can't get it right. It's [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=drummer]sorry, the post insluded the ")" in the URL, and there's no "www", silly me.. here it is all on it's lonesome:

[http://ubuntuguide.com/](http://ubuntuguide.com/)
[/QUOTE]

Still the same problem, that's why I said that.  :-x

---

### Post by MrPsycho on 2005-07-08
Have you read the manual or maybe some documentation?  Linux is not the same as windows, so you're going to have to do things differently.

What do you need a root acount for?  Are you installing something?  If so, you're probably installing this the wrong way.

Use synaptic package manager and .deb packages to make installs of software.

If you absolutely need to run something as the root user you type
```

sudo your_command
```

or go into a terminal window and
```

sudo bash
```
which will give you the prompt
root@ubuntu:~#

Now, whenever you are asked for a password for verification or a sudo command or whatever, it is the password you set for your current user.  Fox example, my account is Matt and I use my personal password to perform a sudo command as root.

btw: sudo stands for super user do, and its also a pun for the word pseudo and also the su(switch user) command.

---

### Post by drummer on 2005-07-08
Sorry, I'm not sure what the problem is.. here's what's at ubuntuguide.org about the root account:
To enable it - ```
sudo passwd root
```
To disable it - ```
sudo passwd -l root
```
[quote=ubuntuguide.org]Q: How to allow root user to login into GNOME?
   1. Read General Notes
   2. Read How to set/change/enable root user password?
   3. System -> Administration -> Login Screen Setup
   4. Login Screen Setup
Security Tab -> Options -> Allow root to login with GDM (Checked)[/quote]
/etc/hosts shouldn't have anything to do with using sudo, but here's mine if you want to compare:```
127.0.0.1	localhost.localdomain	localhost	owen

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```If you are having trouble using sudo for the above commands, use the "Root Terminal" under "Applications > System Tools"

---

### Post by drummer on 2005-07-08
Thanks MrPsycho, explaining sudo and admin in Linux should have been the first thing I did, I didn't think of it  ](*,)

---

### Post by MrPsycho on 2005-07-08
Np, I have a feeling he's trying to install a bin or something similiar anyway.  Enabling the root account is really only going to cause more problems.

RJARRRPCGP: You just need to learn the debian way of doing things.  Based on your other posts, it sounds like you're having hardware troubles too so I'm sure this can't be easy.

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=MrPsycho]

RJARRRPCGP: You just need to learn the debian way of doing things.  Based on your other posts, it sounds like you're having hardware troubles too so I'm sure this can't be easy.[/QUOTE]

I don't have any hardware malfunctions, AFAIK. And the domain name not found problem was because the Ubuntu guide web site is a .org, not a .com!!! Oops.

---

