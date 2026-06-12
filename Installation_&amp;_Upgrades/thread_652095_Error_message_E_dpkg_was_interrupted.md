---
title: "Error message: E: dpkg was interrupted"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Digitallook on 2007-12-28
When trying to update my system, I get this error message:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


What does it mean and what should I do?

digitallook

---

### Post by bonzodog on 2007-12-28
Basically, do what it says.

open a terminal, and run 
```
$sudo dpkg --configure -a
```

This will fix a package problem that the upgrade appears to have stumbled into, possibly caused by a broken packge.

---

### Post by forestpixie on 2007-12-28
you must manually run 'dpkg --configure -a' to correct the problem. 

in a terminal

```
sudo dpkg --configure -a
```

edit - bit slow there :)

---

### Post by forestpixie on 2007-12-28
have you tried running gparted in gutsy - see what it thinks the state of the partition is

you won't be able to do anything in there, but you could see

---

### Post by Digitallook on 2007-12-28
THanks guys!
Sorted.

Digitallook

---

### Post by spokulator36 on 2008-01-03
Another newbie here with the same problem as Digitalook.
Running Gutsy.

martin@martin-laptop:~$ sudo dpkg --configure -a
[sudo] password for martin:

That's me martin, but it just won't let me type or paste in my password.

Would be grateful for any assistance with this.

Mart

---

### Post by forestpixie on 2008-01-03
type you're password - it's a security thing it's there but not visible

---

### Post by Perfect Storm on 2008-01-03
You can't see the password when typing it is a security feature.

---

### Post by spokulator36 on 2008-01-03
Thanks chaps!
Ain't Ubuntu wonderful.
Onward to the next learning situation......

Mart

---

### Post by browndruid on 2008-01-06
I'm getting a similar problem, but the solution won't work...

Whenever I run apt-get or aptitude, I get the message, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." I can no longer install or remove anything.

When I use the Add/Remove Applications utility, I get the message,
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

The last operation I did before encountering this problem was run "sudo apt-get install kubuntu-desktop" to install KDE, which worked. The same errors occur in KDE.

Any ideas? Thanks in advance.

---

### Post by Perfect Storm on 2008-01-06
Do a
```
sudo dpkg --configure -a
```
first.

---

### Post by bryncoles on 2008-01-08
hi there. im a rank amature 'n00b' (i gather the term is'. i think i might be having the same problem - sorry of im posting in the wrong place here. 

i get the message 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.'. 

when i try and run this in terminal i an simply told i need to be a super user to do anything. 

this confuses me, as i dont know what it means!

any help would be greatly appreciated, thanks!

*edit* (do i need to type that?)

sorry everyone... i followed the suggestions listed here again and it worked this time. you guys are great - you helped me without even needing to do anything! i think im going to like living in ubuntu.... ;-)

---

