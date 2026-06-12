---
title: "fail to install under vbox"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by Echoes88 on 2012-04-10
HI!

I have got  a problem with my laptop. It's a lenovo n200 with 2 ghz c2d  and 2 gb ram. I have native windows vista on that. and tried to install  ubuntu 11.10 within virtualbox, and it stops in a certain point during  the installation. I tried it for a few times, no succes.

It used to work with older version (8.10), so i dont know why it is.

Thanks for the help.
Echoes88

---

### Post by josephmills on 2012-04-10
I there is this ubuntu server ? 
have you checked the md5sums of the iso ? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
download a new one and try that one. 
oh did you add yourself as a user to vbox ?

---

### Post by Echoes88 on 2012-04-10
i didnt even know such program exists:roll: 
im checking it right now

It's a desktop version.

oh did you add yourself as a user to vbox ? 	

what do u mean by that?

---

### Post by roelforg on 2012-04-10
> **Echoes88 said:**
> i didnt even know such program exists:roll: 
im checking it right now

It's a desktop version.

oh did you add yourself as a user to vbox ?     

what do u mean by that?

Note: It's a lot easier to read your posts if you use the [ quote ] (no spaces but else they hide) tag.

I think he meant if your user has permission to run vbox because.

And yes, it should work, did it a few times myself on windows before installing ubuntu, other then that i forgot to make the hd big enough the first time (i advise like 8 gb as minimum size), no problem.

---

### Post by josephmills on 2012-04-10
you can find out all sorts of things about groups and users permissions at these links 

Permissions 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To add a user to a group: 

This can be done many ways but here is one. 

open terminal (ctrl+alt+t)

We can see who you are by entering in the command 
```
whoami
```

We can now add who you are into the vbox **group**
By Enter in: 
```
gksudo gedit /etc/group & 
```

We then go down to the line that looks like this 
```
vboxusers:x:###:
```

### should be a Number. 

We add are name to it so it looks like this 
```
vboxusers:x:125:joseph
```

you replace joseph with your name the one that you got from **whoami**

save the file and close. 

Congrats you are now in the vbox users **group**

I hope that this helps :)

---

