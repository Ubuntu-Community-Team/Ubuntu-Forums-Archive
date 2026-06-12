---
title: "sudo apt-get update/install error"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Namana on 2012-01-12
Heyy,

While running sudo apt-get install in ubuntu 11.04, I have started getting the following error::

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

Can anyone please guide me through the solution of the above problem??
Thanks in advance..

Thank You,
Naman

---

### Post by RedSingularity on 2012-01-12
Run this command:
 
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-amd64_Packages

---

### Post by Namana on 2012-01-12
Thanks RedSingularity for such a quick reply.

I ran your command..and got the following output=

rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina': No such file or directory
rm: cannot remove `ry-amd64_Packages': No such file or directory

It didnt solve the problem..

---

### Post by RedSingularity on 2012-01-12
> **Namana said:**
> Thanks RedSingularity for such a quick reply.
 
I ran your command..and got the following output=
 
rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina': No such file or directory
rm: cannot remove `ry-amd64_Packages': No such file or directory
 
It didnt solve the problem..
 
Run it as one line

---

### Post by RedSingularity on 2012-01-12
```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-amd64_Packages

```

---

### Post by drmrgd on 2012-01-12
There is a typo in the line.  Looks like an extra space in the word "binary".  Try this instead:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by RedSingularity on 2012-01-12
> **drmrgd said:**
> There is a typo in the line. Looks like an extra space in the word "binary". Try this instead:
 
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```
 
Yes there was a typo. Sorry.

---

### Post by Namana on 2012-01-12
It worked...

Thanks a lot guys.....

---

