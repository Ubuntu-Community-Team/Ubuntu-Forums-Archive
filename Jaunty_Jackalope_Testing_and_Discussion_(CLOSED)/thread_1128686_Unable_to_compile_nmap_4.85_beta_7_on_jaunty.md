---
title: "Unable to compile nmap 4.85 beta 7 on jaunty"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sefs on 2009-04-17
Hey there I was able to compile the beta on intrepid, but on jaunty I am getting these errors...am I missing a package or something?

```

.
.
.
ence to `ERR_error_string'
/home/pingpong/Desktop/nmap-4.85BETA7/nsock/src/nsock_ssl.c:95: undefined reference to `ERR_get_error'
/home/pingpong/Desktop/nmap-4.85BETA7/nsock/src/nsock_ssl.c:95: undefined reference to `ERR_error_string'
collect2: ld returned 1 exit status
make[1]: *** [ncat] Error 1
make[1]: Leaving directory `/home/pingpong/hd2/Internet_Downloads/nmap-4.85beta/nmap-4.85BETA7/ncat'
make: *** [ncat_build] Error 2

```

---

### Post by sefs on 2009-04-18
Ok, I had to install libssl-dev.

---

