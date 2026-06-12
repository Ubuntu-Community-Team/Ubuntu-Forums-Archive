---
title: "sudo does not work .."
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by Isiodos on 2010-11-05
Hello every one.. First of all I am new in ubuntu community (!)..

I have the following problem. I am trying to install a program (matlab).. But it happens the following absurd.
When I am typing (in terminal) :
sudo sh /home/isiodos/m_iso/install
it says :  "sh : Can't open /home/isiodos/m_iso/install"

BUT if I type : sh /home/isiodos/m_iso/install 
it runs the installer (without administrator rights and I have problem to create folders etc).

I did it (I mean worked with sudo) one time and it run and I install it but in wrong folder and I delete it etc. 

I have tryied to reboot .. The pass for sudo is correct because it left me do other jobs like delete files in which I need rights etc

---

### Post by cgroza on 2010-11-05
Try:

sudo su
[your command without sudo]

---

### Post by Isiodos on 2010-11-05
> **cgroza said:**
> Try:

sudo su
[your command without sudo]

says "bash: /home/isiodos/m_iso/install: Permission denied" :(
and after that does not work neither with sh ...

---

### Post by TSJason on 2010-11-05
Isiodos,

Have you checked the file permissions?
Is that location mounted as nfs with root_squash?

---

### Post by Isiodos on 2010-11-05
> **TSJason said:**
> Isiodos,

Have you checked the file permissions?
Is that location mounted as nfs with root_squash?

About the permitions as I said I can open it with sh but not with sudo sh. If that helps you...

About the mount type I used Furius ISO ,but I don't understand what exactly you asking..

---

### Post by Isiodos on 2010-11-05
I changed all the mount options in fuze !! 
I don't know which is the wrong but it worked!
I change from fuse to Loop from Md5 to SHA1 and from Brasero to Nautilus..
:guitar: :popcorn: :KS

---

