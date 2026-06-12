---
title: "Installing wireless drive and error"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by shadihariri on 2010-12-20
Hi All
I recently buy a Asus Eee1015pem. and it doesn't recognize wireless.I search a bit and find out that I have to update my drive to broadcom STA wireless drive.But when I want to activate it, this error is shown
```
/var/cache/apt/archives/
```
There is no synaptic open and I do try this two command in terminal
```

sudo aptitude update
sudo aptitude upgrade

```
but it doesn't work.

---

### Post by slooow on 2010-12-20
If you want help you need to be more specific. The first code bit is not an error, just a path. > It doesn't work is the most useless description, tell us what the terminal returns when you issue those commands.

---

### Post by shadihariri on 2010-12-20
Sorry I was so confused because of the error :(
The error message was this :
```
unaible to lock /var/cache/apt/archives/lock
```
and the terminal returns the same error

---

### Post by slooow on 2010-12-21
Well, then you need to find what locks it. Try 
```
lsof | grep apt
```
You might then be able to see the program which locks it and kill it.

---

