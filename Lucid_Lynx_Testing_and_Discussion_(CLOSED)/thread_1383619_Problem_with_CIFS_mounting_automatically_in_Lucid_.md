---
title: "Problem with CIFS mounting automatically in Lucid Apha 2"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Alabamaschalk on 2010-01-17
Hi!

I made a fresh install of Lucid Alpha 2 and had some troubles with the automatic mount with fstab.
I use this to mount my windows shares and after I edited fstab, the laptop (Dell Inspiron mini 10) shuts down immediately after log in. 
After deleting the lines in fstab it worked fine. (without mounting the shares of course.)
I updated mountall like this:


```
sudo apt-get install mountall
```


After that I could edit fstab like I wanted, like this:


```
//windowspc/share /home/user/share cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
```


I do not know exactly what went wrong, but may be this is improtant for someone
BTW, it worked fine with alpha 1.


Regards

---

### Post by cariboo on 2010-01-17
Do you have smbfs installed?

---

### Post by Alabamaschalk on 2010-01-17
Yes, I folliowed the instructions on:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

It usually worked without a flaw. 

Thanks

---

### Post by cariboo on 2010-01-17
I see you marked the thread solved, what did you do to solve the problem?

---

### Post by Alabamaschalk on 2010-01-17
Hi there!

I solved the issue before I started the thread by reinstalling mountall like this:
```
sudo apt-get install mountall
```
I just thougt that may be helpful for other people running in the same issue.
Sorry for the confusion!

---

