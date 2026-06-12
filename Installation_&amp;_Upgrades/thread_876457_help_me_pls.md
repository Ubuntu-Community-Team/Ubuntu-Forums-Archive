---
title: "help me pls"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by lh595 on 2008-07-31
i am a new user and i just jumped out of windows and i need help installing ubunto i get a error 5 message when it starts up off the hard drive but the cd will load every time pls help im starting to get second thoughts i don't want to go back but running it off the cd is for the birds 
thank you for your help

---

### Post by nbayiha on 2008-07-31
Which Error are u getting , and which cd are trying to install.
Maybe you need the alternate ubuntu cd .
Anyway which kind of computer do you have , specification and all the rest.
And which error are u recieving ?

---

### Post by lh595 on 2008-08-01
yea i have a amd sempron 2200 
the Ubuntu ver. of 8,04  April 08
 nome v 2.22.1 4/15/08 
Linux 2.6.24-16 generic 
is this what you need

---

### Post by overdrank on 2008-08-01
> **lh595 said:**
> yea i have a amd sempron 2200 
the Ubuntu ver. of 8,04  April 08
 nome v 2.22.1 4/15/08 
Linux 2.6.24-16 generic 
is this what you need

Hi and welcome,
Are you saying grub error 5?
Did you check the cd for errors before installing?

---

### Post by lh595 on 2008-08-01
yea it is saying grub loading and then it sayes error 5

---

### Post by Pumalite on 2008-08-01
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)
If your Partition Table is indeed corrupted; you will need TesDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by lh595 on 2008-08-02
ok i tried the gparted on the cd and i made the /dev/sda1 the boot partion and the same thing happen what do i do now

---

### Post by Pumalite on 2008-08-02
Returning your PM. Read post # 6

---

### Post by lh595 on 2008-08-05
ok i tried the partition editor to find the partition and rest them and i reinstalled the ubuntu and the same error 5 came right back 

then i tried to use the testdisk program and i cant find the application all the extinctions say unknown i don't know what to do next what do i do now

---

### Post by Pumalite on 2008-08-05
Read well the Documentation for TestDisk

---

### Post by lh595 on 2008-08-07
ok when i tried that i got i was not authorized to intall the taskdisk the sudo taskdisk yada yada didn't work what do i have to do to get the rights to install the window #12 is what i got when i tried

---

### Post by lh595 on 2008-08-07
ubuntu@ubuntu:~$ sudo ./testdisk_static, sudo ./photorec_static
sudo: ./testdisk_static,: [COLOR="Red"]command not found[/COLOR]
ubuntu@ubuntu:~$ su -c ./testdisk_static, su -c ./photorec_static
Unknown id: su
ubuntu@ubuntu:~$ -c ./testdisk_static, su -c ./photorec_static
bash: -c: [COLOR="Red"]command not found[/COLOR]
ubuntu@ubuntu:~$ sudo ./testdisk_static, sudo ./photorec_static
sudo: ./testdisk_static,: [COLOR="Red"]command not found[/COLOR]
ubuntu@ubuntu:~$

---

