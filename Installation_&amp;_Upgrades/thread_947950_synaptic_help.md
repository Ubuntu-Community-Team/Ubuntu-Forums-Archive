---
title: "synaptic help"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by mickeyholm on 2008-10-14
hey i'm pretty new to ubuntu and im having a problem with synaptic

E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

i found a few others having a similar issue but difference was their error said 

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

can you please help me?

THANKS

---

### Post by oldos2er on 2008-10-14
How exactly are you starting the program? Are you asked for your password?

---

### Post by mickeyholm on 2008-10-15
> **oldos2er said:**
> How exactly are you starting the program? Are you asked for your password?
ive started it through system>administration>synaptic package manager and through terminal and both ways i still get the message.

---

### Post by ronnielsen1 on 2008-10-15
[http://ubuntuforums.org/showthread.php?t=699130](http://ubuntuforums.org/showthread.php?t=699130)
This post seems similar. Try to open a terminal and type 

sudo usermod -d /root root

---

### Post by mickeyholm on 2008-10-15
> **ronnielsen1 said:**
> [http://ubuntuforums.org/showthread.php?t=699130](http://ubuntuforums.org/showthread.php?t=699130)
This post seems similar. Try to open a terminal and type 

sudo usermod -d /root root
same error but you're right it is similar the only difference is that one is /home/root and mine is just /root

---

### Post by patrickballeux on 2008-10-15
> **mickeyholm said:**
> same error but you're right it is similar the only difference is that one is /home/root and mine is just /root

Can you try this:

```
sudo bash
```
Enter your password then...
```
synaptic
```

And see what happen...

In the worst case:

```
sudo mkdir /root/.synaptic
```

And see what happens...

Good luck!

---

### Post by mickeyholm on 2008-10-18
i tried sudo bash before and synaptic before and it doesn't work. 

root@ubuntu:~# sudo mkdir /root/.synaptic
mkdir: cannot create directory `/root/.synaptic': No such file or directory

---

