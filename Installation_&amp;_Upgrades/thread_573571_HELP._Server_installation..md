---
title: "HELP. Server installation."
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by achristopher on 2007-10-11
Hello, 
 I am relitivly new to linux/ubuntu. I just downloaded the latest server version of ubuntu. I thought that I had partistioned my hard drive. I have a pentium4 and 512mb ram 40ghhdd. Here are my problems:

I thought that I had partitioned my hdd disk,but I don't see any option to use windows. ubuntu loads on startup not windows. Is there a way to restore the system back to windows and all my files?

after I enter user name and password  I get is a message that says
"username@username:-$"  I don't know how to get past this.
 it won't let me do anything
I try startx and I get this message 
x: cannot stat /etc/x11/x (no such file or directory aborting)
 giving up connection reused (errno 111) unable to connnect to server.

What do I do? Please help ... THanks

---

### Post by taurus on 2007-10-11
You need to understand that the server version doesn't come with X so startx is not going to work unless you install that extra package.  

What's the output of this command from a prompt, after you've logged in?

```
sudo fdisk -l
```
(Use the same password that you use to log in with and when you type it in, you won't see any echo back on the screen so make sure you type it right.)

---

### Post by achristopher on 2007-10-11
it says ivalid option -1
and then gives an exaple of how to use the command.

---

### Post by taurus on 2007-10-11
That is a lower case letter l, not number 1.

---

### Post by achristopher on 2007-10-11
AH, my mistake. I tried it again the right way and got the same response .

---

### Post by taurus on 2007-10-11
Can you post the command that you typed and the output/error message of it?

---

### Post by achristopher on 2007-10-11
Sorry. I did it wrong this is what it says:

Disk/dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
units=cylenders or 16065 * 512= 8225280 bytes
device boot  start    end           blocks   Id system
/dev/sada1    1       4681     376001101 83 linux
/dev/sada2    4682 4865 141477980 5 extended     
/dev/sada5 4682 4865 147948= 82 linux swa/solaris

---

### Post by taurus on 2007-10-11
Sorry but you just blew away your Windows on your machine.  I hope you did backup your files before you attended to install Ubuntu server!

---

### Post by maybeway36 on 2007-10-11
There's no windows there, it seems...

---

### Post by achristopher on 2007-10-11
Well, I did have some pictures. But thats fine. How do I install ubuntu or get it to work thats all I care about. I am using a version that I downloaded from the ubuntu website.  I am I missing something?

---

### Post by oldos2er on 2007-10-11
> **achristopher said:**
> Well, I did have some pictures. But thats fine. How do I install ubuntu or get it to work thats all I care about. I am using a version that I downloaded from the ubuntu website.  I am I missing something?

 It is working. The server version has no GUI; but you can install one by typing "sudo aptitude install ubuntu-desktop" at the terminal, after you've logged in.

---

