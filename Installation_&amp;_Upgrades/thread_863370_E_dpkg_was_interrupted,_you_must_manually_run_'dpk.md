---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by meskalinn on 2008-07-18
Hi, I hope someone could help me. 
what should I do? I cannot install anything


nedime@meskalin:~$ sudo apt-get install mplayer
[sudo] password for nedime: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
nedime@meskalin:~$

---

### Post by avtolle on 2008-07-18
From the command line```
sudo dpkg --configure -a
```

---

### Post by Pumalite on 2008-07-18
sudo dpkg --configure -a

---

### Post by meskalinn on 2008-07-18
thank you so much, I am a new user as you see. thanks again

---

### Post by Pumalite on 2008-07-18
Welcome and good luck!

---

### Post by sid2.0 on 2008-07-23
> **Pumalite said:**
> sudo dpkg --configure -a

Hi all, I am new to Ubuntu as well and I had the same problem. I used this code and it worked for me as well so thanks..But I find my self asking Why? What dose this code do or fix? I have three units running Ubuntu and this was the fourth I have not run in to this before so just looking for the cause of this problem and what the code fixes.. Thanks 

Sid~:)

---

### Post by lisati on 2008-07-23
> **sid2.0 said:**
> Hi all, I am new to Ubuntu as well and I had the same problem. I used this code and it worked for me as well so thanks..But I find my self asking Why? What dose this code do or fix? I have three units running Ubuntu and this was the fourth I have not run in to this before so just looking for the cause of this problem and what the code fixes.. Thanks 

Sid~:)
The command does some housework on the files used by apt-get (and other processes used to install stuff).

---

### Post by iaculallad on 2008-07-23
> **sid2.0 said:**
> Hi all, I am new to Ubuntu as well and I had the same problem. I used this code and it worked for me as well so thanks..But I find my self asking Why? What dose this code do or fix? I have three units running Ubuntu and this was the fourth I have not run in to this before so just looking for the cause of this problem and what the code fixes.. Thanks 

Sid~:)

For detailed explanation on what those options do with dpkg (--configure -a, and the dpkg utility as well), try to read the manual page of that command using the terminal:

```
man dpkg
```

---

### Post by sid2.0 on 2008-07-23
> **lisati said:**
> The command does some housework on the files used by apt-get (and other processes used to install stuff).

Thanks lisati, I feel better now..:biggrin:

---

