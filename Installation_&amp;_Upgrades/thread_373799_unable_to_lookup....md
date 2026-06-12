---
title: "unable to lookup..."
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-03-01
I cannot configure my Ubuntu 6.06 Server. If always give me unable to lookup (as seen below:)

```

myaccount@mypc:~$ sudo vi /etc/network/interfaces
sudo: unable to lookup mypc.com /bin/hostname -F /etc/hostname via gethostbyname()

```


Need help on this.:confused:

---

### Post by taurus on 2007-03-01
Did you happen to change the name of your computer or modify anything in /etc/hostname and/or /etc/hosts?  Can you paste those two files here?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by textguru on 2007-03-01
Additional sample commands that made this error:

> myaccount@mypc:/home/share$ sudo mkdir intranet
sudo: unable to lookup mypc /bin/hostname -F /etc/hostname via gethostbyname()


---

### Post by textguru on 2007-03-01
> **taurus said:**
> Did you happen to change the name of your computer or modify anything in /etc/hostname and/or /etc/hosts?  Can you paste those two files here?

```
cat /etc/hostname
cat /etc/hosts
```
here it is:

> myaccount@mypc:/home/share$ cat /etc/hostname
mypc.com /bin/hostname -F /etc/hostname
myaccount@mypc:/home/share$ cat /etc/hosts
127.0.0.1       localhost
10.63.0.195     mypc mypc.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
myaccount@mypc:/home/share$


Hope you might help.

---

### Post by taurus on 2007-03-01
```
**mypc.com /bin/hostname -F /etc/hostname**
```
Is that your /etc/hostname?

---

### Post by textguru on 2007-03-01
my PC name is "mypc". I do not know why hostname in the /etc/hostname indicated that way. How can I change it?

---

### Post by taurus on 2007-03-01
Boot into recovery mode from GRUB menu and remove everything in /etc/hostname except the name of your machine, **mypc**.

```
nano /etc/hostname
```
Save and exit with <Ctrl>o & <Ctrl>x.

Then reboot it with 

```
shutdown -r now
```
and see if you can run sudo again.

---

### Post by textguru on 2007-03-01
its working now. thanks a lot. :KS

---

