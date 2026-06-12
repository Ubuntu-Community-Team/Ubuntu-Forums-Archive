---
title: "sudo segfaults"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by surfed on 2008-10-02
Now here is something i have not seen before. Since last night after I solved this problem: 
[http://ubuntuforums.org/showthread.php?p=5893011]("http://http://ubuntuforums.org/showthread.php?p=5893011") 

I now cant sudo anymore. When i do sudo su I get this:

```
$ sudo su
[sudo] password for alex: 
Segmentation fault
```

and /var/log/syslog has this to say:

```
Oct  2 09:33:53 xeon kernel: [  103.388015] sudo[7086]: segfault at 0 ip 00007fa04465ad6c sp 00007fff4e5944e0 error 4 in pam_smbpass.so[7fa0445f3000+149000
```]

Please Help.....

---

### Post by surfed on 2008-10-02
[https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/260687](https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/260687)

---

