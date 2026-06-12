---
title: "E: Unmet dependencies. Try using -f error?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by tripz0r on 2011-01-18
Hello,

I was use Synaptic Package Manager to install some backtrack tools on my Ubuntu.
I have latest updated version .

And i got some errors while i use to installing all of that tools.

Now in my bar there is one red sign where write this:

```
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.The error message was: 'Error: BrokenCount > 0'This is usually means that your installed package have unmet dependencies
```When i click on that i got Update Manager, and there is checked "Libssh2-1 (New Install) Description: SSH2 client-side library (size: 108 KB)"
When i click on install updates that finish but still stay there...

I go in terminal, and write "apt-get install" then i got this :

```
root@tripz0r-Laptop:/home/tripz0r# apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  medusa: Depends: libssh2-1 but it is not installed
E: Unmet dependencies. Try using -f.
```And i can't open Synaptic Package Manager, and i can't go in my root user, when i logout from my user to log in root, i log in and then I get a background, without icons, bars and the cursor that loads.And can't do anything ...

Can some one help me .

Thanks!

---

### Post by zvacet on 2011-01-22
```
sudo apt-get -f install
```

---

### Post by Rubi1200 on 2011-01-22
You can also try this in the terminal:

```
sudo dpkg --configure -a
```

Post back with the exact errors, if any.

---

### Post by RestingRhino on 2011-03-17
can you quickly cover what this does after you enter it into a terminal

---

