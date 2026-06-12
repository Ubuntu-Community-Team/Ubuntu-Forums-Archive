---
title: "Evolution won't start after upgrade"
date: 2016-10-19
forum: Installation &amp; Upgrades
---

### Post by sccjono on 2016-10-19
Hello all,

Since upgrading to 16.10 from 16.04 the Evolution email client will not start on my laptop. I use Evolution to connect to my work Exchange server. If I try and start from the terminal I get the following. Can anyone please help?

```
jono@ubuntu:~$ evolution
[libprotobuf FATAL google/protobuf/stubs/common.cc:61] This program requires version 3.0.0 of the Protocol Buffer runtime library, but the installed version is 2.6.1.  Please update your library.  If you compiled the program yourself, make sure that your headers are from the same version of Protocol Buffers as your link-time library.  (Version verification failed in "/build/libphonenumber-ClRhsc/libphonenumber-7.1.0/cpp/src/phonenumbers/phonemetadata.pb.cc".)
terminate called after throwing an instance of 'google::protobuf::FatalException'
  what():  This program requires version 3.0.0 of the Protocol Buffer runtime library, but the installed version is 2.6.1.  Please update your library.  If you compiled the program yourself, make sure that your headers are from the same version of Protocol Buffers as your link-time library.  (Version verification failed in "/build/libphonenumber-ClRhsc/libphonenumber-7.1.0/cpp/src/phonenumbers/phonemetadata.pb.cc".)
Aborted (core dumped)
jono@ubuntu:~$
```

---

### Post by sccjono on 2016-10-21
I got an update to Evolution earlier and hoped that would fix it but sadly not. Has anyone any thoughts?

jono

---

### Post by howefield on 2016-10-22
Long time since I used Evolution, but in the absence of any other reply what is the output of..

```
apt-cache policy protobuf-compiler
```

---

### Post by sccjono on 2016-10-24
Hi howefield. I appreciate your effort. I get ...

```
jono@ubuntu:~$ apt-cache policy protobuf-compiler
protobuf-compiler:
  Installed: (none)
  Candidate: 3.0.0-7ubuntu3
  Version table:
     3.0.0-7ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
jono@ubuntu:~$
```

---

### Post by sccjono on 2016-10-24
As it said it wasn't installed, I tried installing the package, but Evolution still will not run. :(

---

### Post by sccjono on 2016-10-26
Still not working. Has anyone any thoughts?

---

### Post by balloonbending on 2016-11-23
I've got the same issue - did you have any luck?  I was thinking of removing the older 2.6.1. from Synaptic but I don't know what else uses it (if anything)  ...?

---

