---
title: "[SOLVED] Emesene"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Sid1980 on 2008-05-21
If i try to execute Emesene the error msg comes " I refuse to run as root"

Thx

---

### Post by ChameleonDave on 2008-05-21
> **Sid1980 said:**
> If i try to execute Emesene the error msg comes " I refuse to run as root"

Thx
We need a little bit more info.  Are you saying that it gives you that message even if you don't run it as root, or are you saying that you don't understand the error?

---

### Post by Sid1980 on 2008-05-21
> **ChameleonDave said:**
> We need a little bit more info.  Are you saying that it gives you that message even if you don't run it as root, or are you saying that you don't understand the error?

I m running hardy heron and having only one root account, if i try to execute thro terminal the error msg comes " I refuse to run as root" even if i double click on Icon nothing happens i hope this much info is enough

---

### Post by atomkarinca on 2008-05-22
Did you login with your root account?

---

### Post by Sid1980 on 2008-05-22
> **atomkarinca said:**
> Did you login with your root account?

if i m saying i m only having one root account that means i could only login as root account :)

---

### Post by atomkarinca on 2008-05-22
During the installation you should've created a user account. It's not suggested to use your system with the root account. Under Users and Groups (System > Administration) you should be able to see all the users you've created. Login with that user account and try to launch emesene with that account.

---

### Post by Sid1980 on 2008-05-23
> **atomkarinca said:**
> During the installation you should've created a user account. It's not suggested to use your system with the root account. Under Users and Groups (System > Administration) you should be able to see all the users you've created. Login with that user account and try to launch emesene with that account.
Yes i created one user but delete it later on and now i only logon as root so it means emesene dont run uder root ??:mad:

---

### Post by ChameleonDave on 2008-05-23
> **Sid1980 said:**
> Yes i created one user but delete it later on and now i only logon as root so it means emesene dont run uder root ??:mad:

Some Linux distributions are a more lax about this than others, but it is generally considered to be a terrible idea to log on to your graphical desktop (KDE, GNOME...) as root.  Ubuntu even disables the root password by default, making it tricky to even do so.  Some apps (and you've just found one) will refuse to run as root.  You really should create a normal user account and use that for everyday tasks.  Otherwise, you will (a) risk damaging your system, and (b) find that many programs refuse to run.

---

### Post by Sid1980 on 2008-05-23
> **ChameleonDave said:**
> Some Linux distributions are a more lax about this than others, but it is generally considered to be a terrible idea to log on to your graphical desktop (KDE, GNOME...) as root.  Ubuntu even disables the root password by default, making it tricky to even do so.  Some apps (and you've just found one) will refuse to run as root.  You really should create a normal user account and use that for everyday tasks.  Otherwise, you will (a) risk damaging your system, and (b) find that many programs refuse to run.

I can understand risk Dave but i cannot do sudo and enter password everyhtime i have to run or install anything :(

---

### Post by ChameleonDave on 2008-05-25
> **Sid1980 said:**
> I can understand risk Dave but i cannot do sudo and enter password everyhtime i have to run or install anything :(
You don't need sudo to run things, only to make changes to the system.  Unless you are an obsessive tinker like myself, you should only need to sudo once in a long while.

---

### Post by karin_2049 on 2008-08-08
I undestand the problem. You have to edit the Controller.py file (is in the emesene root folder).

Find and comment or delete the next lines:

if os.name == 'posix' and os.getuid() == 0:
    print "I refuse to run as root"
return

Save the file. 

Run emesene again =)

---

