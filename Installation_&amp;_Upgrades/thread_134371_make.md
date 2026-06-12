---
title: "make"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by former86camaro on 2006-02-21
can not locate the make command after the install.  unzipped a program called sleuthkit and susposed to run make, but get an error... Ideas?

---

### Post by gord on 2006-02-21
```
sudo apt-get install build-essential
```

that will install the stuff you need to compile (make and gcc and the like)

---

### Post by former86camaro on 2006-02-21
so open a terminal and type the above?  Remember I am also a newb big time.

---

### Post by taurus on 2006-02-21
[QUOTE=former86camaro]so open a terminal and type the above?  Remember I am also a newb big time.[/QUOTE]
Yes, open a terminal and type in at the prompt,

sudo apt-get update
sudo apt-get install build-essential

---

### Post by public_void on 2006-02-22
I guessing you downloaded the .tar.gz. Did you do the following

tar -xvzf [FileName].tar.gz 
cd [FileName]
./configure
make
sudo make install

Does ./configure finish and create the make files. To check, look at the last couple lines of output which finished. This will say whether its missing any dependenices or it completed. If you not sure post the output of ./configure.

---

