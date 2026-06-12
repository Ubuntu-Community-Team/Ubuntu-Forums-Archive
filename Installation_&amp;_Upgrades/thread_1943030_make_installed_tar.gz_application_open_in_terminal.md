---
title: "make installed tar.gz application open in terminal"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by siddugan on 2012-03-18
Hello,

I have this quick question regarding installed applications say from tar.gz files. In the termial, everytime I have to navigate to the particular folder to run the application. Is there a way to add this application globally so that I could just run it anywhere using my terminal. I have done this before by adding the application to /etc/something but I do not remember this now. Any help appreciated.

Thanks

---

### Post by Subidubi32 on 2012-03-25
If You install it from the tar.gz fully, I think it is enough to type in it's name.

---

### Post by Subidubi32 on 2012-03-25
Unzip:
$tar -zxvf something.tar.gz 
$tar -zjvf something.tar.bz2 

Open it:
cd /Download/something

./configure
make
sudo make install

---

### Post by Subidubi32 on 2012-03-25
Is there any other readme in the tarball?

---

