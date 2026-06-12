---
title: "Password required"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Sengwa on 2011-02-12
I am using Ubuntu 10.01 and am trying to install my Lexmark X7675.  I downloaded a driver from Lexmark (/home/matt/Lexmark/lexmark-08z-series-driver-1.0-1.i386.deb.sh) and when i try to run it, it asks for an administrator password.  I do not have an "admninistrater" user set up and my logon password will not permit access.  What password is it looking for, and where could i find it?

---

### Post by gordintoronto on 2011-02-12
Did you use sudo to run the .sh?

---

### Post by Kaboontu on 2011-02-24
I have the same problem too.
I heard it is a drivers' problem with ubuntu 10.10.
I would really need a solution.
Thnx in advance.

---

### Post by sisco311 on 2011-02-24
> **Kaboontu said:**
> I have the same problem too.
I heard it is a drivers' problem with ubuntu 10.10.
I would really need a solution.
Thnx in advance.

Hi and welcome to the forums!

You have to run the installer as root. [uhelp]community/RootSudo[/uhelp]


Open a terminal (Applications - Accessories - Terminal), type **sudo -i sh**, then type a space. Drag the installer in the terminal window, press Enter and follow the instructions...

---

### Post by Kaboontu on 2011-02-25
it seems i was doing sudo wrong on this one.
thnx a lot.
solved for me.

---

