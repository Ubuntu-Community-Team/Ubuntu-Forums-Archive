---
title: "[SOLVED] user is not in sudoers file"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by jediknight1226 on 2008-01-15
I am on a fresh install of ubuntu server 7.10 I didn't realize the server was command line onlt. Thats not that big of a deal though. When I try to do sudo commands it says i'm not in the sudoers file. I tried to use visudo but that says permission denied. I tried su root but it says authentication failure. it wont let me change the password either. So it seems like to change one I have to be in the other but I can't access any of them. What do I do?

---

### Post by reckless2k2 on 2008-01-15
well if you are trying to get to the root user you would just type:

```
su -

```

it will then ask for the password. do you remember your root password?

as far as the rest, you need to include your user/users in the admin group and then they will be able to "sudo" without a problem. you may have to log out and back in as that user before it takes affect. 

got it or do you need specific commands to handle the user mods?

---

### Post by jediknight1226 on 2008-01-15
I just installed it. I never set a root password. When  I was installing it the only passwords it asked for was my user and the mySQL root password. I made both of these the same. I tried it it didn't work. I also tried root with no password and it still wouldnt let me.

---

### Post by jediknight1226 on 2008-01-15
P.S. I am an evil conservative too LMAO.

---

### Post by jediknight1226 on 2008-01-16
OK I figured it out. I had to hit esc while booting to enter recovery mode. Then at the root prompt i was able to edit the sudoers list by adding: corey ALL=(ALL) ALL     I added this right below root and then hit cntrl + x to exit. y to save. and then I had to remove the .tmp extension at the end of the filename before i saved it.

---

### Post by reckless2k2 on 2008-01-16
i've been hearing about this problem but never experienced it myself. 

are you using wubi or running this in a virtual box or is this a standard install?

i'm just curious because i have been hearing this a lot in the forums.

---

### Post by LORDGROND on 2008-01-17
Hi!!

I have the same problem. After the first reboot after the setup program, when I type (example):

sudo apt-get update

The prompt says:
"[sudo] password for 'my-login-name-here':"

(I type the same password of the user name created in the setup program)

The prompt says:
"'my-login-name-here' is not in the sudoers file. This incident will be reported"


I'm installing Ubuntu Server 7.10 in a Virtual Machine on a VMWare Server 1.0.4.

I'll try the same solution of jediknight1226...

---

### Post by reckless2k2 on 2008-01-18
that solution will fix you up but it must be a virtual machine issue that's causing it to drop off i guess. i'd like to know if there are any standard installs experiencing this. if not, this might need to be a bug reported if it's not already.

---

### Post by ICberg7 on 2008-01-18
I had the same problem with server 7.10, when I did a standard install on an older machine I have lying around. I'd like to get some experience running a server, and I figured that the older machine could handle a linux server box better than a Win2k3 server install.

I ran a disk check from the installer menu before installing it, and I don't remember it asking me if I wanted to set a root password or a mysql password, either.

Booting into failsafe, changing the password and adding myself to the suoders list using visudo seems to have solved the problem.

---

### Post by fcigoi on 2008-01-19
Same thing here. I've installed Ubuntu Server 7.10 on a Netfinity from scratch but it denies sudoing....

---

### Post by chomski on 2008-01-24
I have to report the same problem, just done a fresh install of Server 7.10 and I am experiencing the sudoers problem. I will boot into the recovery mode and alter the sudoers file as proposed.
All this after getting through the "Panic:CPU too old for this kernel" problem, meh.

---

