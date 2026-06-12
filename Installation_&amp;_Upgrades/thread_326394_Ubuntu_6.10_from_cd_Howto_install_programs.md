---
title: "Ubuntu 6.10 from cd: Howto install programs?"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by mach3 on 2006-12-27
Hi,

I have downloaded Ubuntu 6.10 and it works good booting from cd. 

I do not wish to install it to the harddrive.

I would like to install ethereal (or wireshark) and i tried with the 
sudo apt-get install ethereal
sudo apt-get install wireshark

But none of them worked. It cannot find the files.

I tried with the apt-get update but it did not effect the problem.

Also I tried the apt-get search but there is no ethereal or wireshark.


Do I have to install Ubuntu to the harddrive in order to be able to install ethereal or wireshark?

Best regards

---

### Post by KenSentMe on 2006-12-27
I think ethereal and wireshark are not on the live CD and default the cd is the only repository. Maybe you can add an online repository (both are in Universe) in Synaptic, but i don't know if that works on a liveCD.

---

### Post by tokj on 2006-12-27
Probably you have to activate all the repositories in the sources.list

---

### Post by tokj on 2006-12-27
> **KenSentMe said:**
> I think ethereal and wireshark are not on the live CD and default the cd is the only repository. Maybe you can add an online repository (both are in Universe) in Synaptic, but i don't know if that works on a liveCD.

Yes, it is possible.

---

### Post by mach3 on 2006-12-27
Thanks for the replys.


> **tokj said:**
> Probably you have to activate all the repositories in the sources.list

How to activate all the repositories (I come from Windows XP so very little Ubuntu knowledge)?

---

### Post by tokj on 2006-12-27
> **mach3 said:**
> How to activate all the repositories (I come from Windows XP so very little Ubuntu knowledge)?

You have two ways to do this:

1) Edit the sources.list in /etc/apt/sources.list with:
```
sudo gedit /etc/apt/sources.list
```

and uncomment all archives (remove the #) ;)

save and run in terminal:

```
sudo apt-get update
```

2) Go on system-->administration-->software properties and select all the archives that are listed (universe, main, restricted, multiverse).

(Probably I did some grammar mistakes, in that case I'm sorry :mrgreen: )

---

### Post by mach3 on 2006-12-27
tokj >> Thanks alot. 
I will try that and return with the result tomorrow.

---

### Post by mach3 on 2006-12-28
tokj >> Thanks alot. I did your first suggestion and that did the job. Thanks :D

---

### Post by tokj on 2006-12-29
I'm happy that i was useful :)

---

