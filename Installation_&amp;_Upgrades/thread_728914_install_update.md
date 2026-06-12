---
title: "install update"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by zorro6500 on 2008-03-19
hi iam a new user and when i make update  after downloading it ( the update is documentation ) can't install  and give an error message so what the problem :lolflag:

---

### Post by zorro6500 on 2008-03-19
the mwssage is 

E: /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb: unable to stat `./usr/share/doc/ubuntu-docs/README' (which I was about to install)

---

### Post by zorro6500 on 2008-03-19
> **zorro6500 said:**
> the mwssage is 

E: /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb: unable to stat `./usr/share/doc/ubuntu-docs/README' (which I was about to install)


IAM FROM EGYPT

---

### Post by Pumalite on 2008-03-19
Post the output of:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by zorro6500 on 2008-03-19
the output:

Unpacking replacement ubuntu-docs ...
dpkg: error processing /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb (--unpack):
 unable to stat `./usr/share/doc/ubuntu-docs/README' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-03-19
Run:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
Post the output.

---

### Post by zorro6500 on 2008-03-20
the out puts:
Unpacking replacement ubuntu-docs ...
dpkg: error processing /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb (--unpack):
 unable to stat `./usr/share/doc/ubuntu-docs/README' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zorro6500 on 2008-03-20
any body help

---

### Post by zorro6500 on 2008-03-21
i wanna help please

---

### Post by zorro6500 on 2008-03-21
where r u   Pumalite???

---

### Post by Pumalite on 2008-03-21
Go to:
/var/cache/apt/archives and see if you find:
ubuntu-docs_7.10.5_all.deb

---

### Post by zorro6500 on 2008-03-22
yes i found it !

---

### Post by Pumalite on 2008-03-22
Delete it. Then do:
sudo apt-get update
sudo apt-get upgrade

---

### Post by zorro6500 on 2008-03-23
how i can delelt ot because i do that fromterminal and told me that  i don't have permission to delet it  and the file it protected

---

### Post by PmDematagoda on 2008-03-23
You will need root privileges to remove the file, just execute:-
```
sudo rm /var/cache/apt/archives/ubuntu-docs_7.10.5_all.deb
```

After that is done, execute the commands provided by Pumalite.

---

### Post by zorro6500 on 2008-03-23
still have the last error message

---

### Post by Pumalite on 2008-03-23
I would clean 'archives' and try again.
You can use:
gksudo nautilus

---

### Post by PmDematagoda on 2008-03-23
You can clean the archives more easily using:-
```
sudo apt-get clean
```

---

### Post by Pumalite on 2008-03-23
Good to know!

---

### Post by zorro6500 on 2008-03-25
thanx  . but i still have the problem

---

