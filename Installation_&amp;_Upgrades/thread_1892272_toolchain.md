---
title: "toolchain"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by atpersian on 2011-12-07
Dear Sir Or madam
i install latest ubuntu on my laptop amd 64
i try to install toolcian via   

 sudo dpkg -i toolchain-mips-ls_0.1-1.deb
but after run this command i see error
please somebody help me
One Beginner D:)
Best Regard

---

### Post by matt_symes on 2011-12-07
Hi

Welcome to the forums :D.

Please post the error message you get getting.

Kind regards

---

### Post by bluexrider on 2011-12-07
> **atpersian said:**
> Dear Sir Or madam
i install latest ubuntu on my laptop amd 64
i try to install toolcian via   

 sudo dpkg -i toolchain-mips-ls_0.1-1.deb
but after run this command i see error
please somebody help me
One Beginner D:)
Best Regard

the .DEB file should be able to install by double-clicking no need to dpkg!

---

### Post by atpersian on 2011-12-07
Dear Friend
The error is as below:


dpkg-deb: error: `toolchain-mips-ls_0.1-1.deb' is not a debian format archive
dpkg: error processing toolchain-mips-ls_0.1-1.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 toolchain-mips-ls_0.1-1.deb

---

### Post by matt_symes on 2011-12-07
Hi

Take a look at this....
```

matthew@matthew-Aspire-7540:~$ wget http://www.ubnt.com/downloads/sdk/toolchain-mips-ls_0.1-1.deb 
--2011-12-07 20:37:01--  http://www.ubnt.com/downloads/sdk/toolchain-mips-ls_0.1-1.deb
Resolving www.ubnt.com (www.ubnt.com)... 208.68.95.4
Connecting to www.ubnt.com (www.ubnt.com)|208.68.95.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22761594 (22M) [application/octet-stream]
Saving to: `toolchain-mips-ls_0.1-1.deb'

100%[=======================================================================================================================================>] 22,761,594   151K/s   in 91s     

2011-12-07 20:38:38 (243 KB/s) - `toolchain-mips-ls_0.1-1.deb' saved [22761594/22761594]

matthew@matthew-Aspire-7540:~$ sudo dpkg -i toolchain-mips-ls_0.1-1.deb 
[sudo] password for matthew: 
Selecting previously unselected package toolchain-mips-ls.
(Reading database ... 284509 files and directories currently installed.)
Unpacking toolchain-mips-ls (from toolchain-mips-ls_0.1-1.deb) ...
Setting up toolchain-mips-ls (0.1-1) ...
matthew@matthew-Aspire-7540:~$ 
```

Where did you get the deb file from ?

From a terminal, please post the output of

```
uname -a
```

```
cat /etc/lsb-release
```

into your next post.

Kind regards

---

### Post by bluexrider on 2011-12-07
> **atpersian said:**
> Dear Friend
The error is as below:


dpkg-deb: error: `toolchain-mips-ls_0.1-1.deb' is not a debian format archive
dpkg: error processing toolchain-mips-ls_0.1-1.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 toolchain-mips-ls_0.1-1.deb

You claim its not a .deb file okay

Download and install the toolchain of UBNT needed to run the UBNT SDK:
  # wget [http://www.ubnt.com/downloads/sdk/toolchain-mips-ls_0.1-1.deb](http://www.ubnt.com/downloads/sdk/toolchain-mips-ls_0.1-1.deb)
# sudo dpkg -i toolchain-mips-ls_0.1-1.deb

---

### Post by matt_symes on 2011-12-07
??

I thought that's what i suggested :)

---

### Post by bluexrider on 2011-12-07
> **matt_symes said:**
> ??

I thought that's what i suggested :)

I thought you were giving him the example. I was giving him the web site.

hopefully he pulls it altogether.

still a .deb file mystery to me

---

### Post by atpersian on 2011-12-08
All Dear


the ubnt restrict my country from download .so i download this file manual via vpn
then copy this file in home directory
after type dpkg appear error as below :
-------------------------------------------------------------------
atpersian@atpersian-Inspiron-N5010:~$ sudo dpkg -i toolchain-mips-ls_0.1-1.deb
[sudo] password for atpersian: 
Selecting previously deselected package toolchain-mips-ls:i386.
(Reading database ... 151930 files and directories currently installed.)
Unpacking toolchain-mips-ls:i386 (from toolchain-mips-ls_0.1-1.deb) ...
dpkg: dependency problems prevent configuration of toolchain-mips-ls:i386:
 toolchain-mips-ls:i386 depends on make.
dpkg: error processing toolchain-mips-ls:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 toolchain-mips-ls:i386

--------------------------------------------------
also i try to install it via double click .this is a result

---

### Post by atpersian on 2011-12-08
[[IMG]http://www.image-share.com/upload/1114/5m.png[/IMG]](http://www.image-share.com/ipng-1114-5.html)

---

### Post by atpersian on 2011-12-08
All Friends
Now I know that my Ubuntu is 64bit and this deb file is 32bit
so how can i install it in my OS???
B R

---

### Post by matt_symes on 2011-12-08
Hi

> **atpersian said:**
> All Friends
Now I know that my Ubuntu is 64bit and this deb file is 32bit
so how can i install it in my OS???
B R

From [http://www.ubnt.com/forum/showthread.php?p=89714](http://www.ubnt.com/forum/showthread.php?p=89714)

> We do not have a tookit for 64 bit linux at this time.

You can use a virtual machine; maybe.

Kind regards

---

### Post by atpersian on 2011-12-08
thanks matt
i should do that D:))

---

