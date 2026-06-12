---
title: "Problems installing &quot;socks&quot; program on Ubuntu"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by BTJohn on 2011-10-04
Hello - I am new to Linux and Ubuntu. I just installed Ubuntu on a Win 7 machine. My goal is to install a program originally written by Richard Stevens called sock. This application has been rewritten for Linux and is available at [http://www.icir.org/christian/sock.html](http://www.icir.org/christian/sock.html). I have downloaded the tarball and executed the commands indicated in the instructions

./configure
make
make install

The following messages are received from the make and make install logs and I have attached the config log. Am I missing required files? Is there a different approach I should take to installing?

Any feedback would be most appreciated.

Thanks,

John

$ make 
make  all-recursive
make[1]: Entering directory `/home/john/Downloads/sock-0.3.2'
Making all in src
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2'
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2'
make[1]: Leaving directory `/home/john/Downloads/sock-0.3.2'
$ 


AND

$ make install
Making install in src
make[1]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c sock '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/sock': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make: *** [install-recursive] Error 1
$

---

### Post by matt_symes on 2011-10-04
Hi
> 
/usr/bin/install -c sock '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/sock': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1Try

```
sudo make install
```Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by ~!geek!~ on 2011-10-04
> **BTJohn said:**
> Hello - I am new to Linux and Ubuntu. I just installed Ubuntu on a Win 7 machine. My goal is to install a program originally written by Richard Stevens called sock. This application has been rewritten for Linux and is available at [http://www.icir.org/christian/sock.html](http://www.icir.org/christian/sock.html). I have downloaded the tarball and executed the commands indicated in the instructions

./configure
make
make install

The following messages are received from the make and make install logs and I have attached the config log. Am I missing required files? Is there a different approach I should take to installing?

Any feedback would be most appreciated.

Thanks,

John

$ make 
make  all-recursive
make[1]: Entering directory `/home/john/Downloads/sock-0.3.2'
Making all in src
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2'
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2'
make[1]: Leaving directory `/home/john/Downloads/sock-0.3.2'
$ 


AND

$ make install
Making install in src
make[1]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
make[2]: Entering directory `/home/john/Downloads/sock-0.3.2/src'
test -z &quot;/usr/local/bin&quot; || /bin/mkdir -p &quot;/usr/local/bin&quot;
  /usr/bin/install -c sock '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/sock': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/john/Downloads/sock-0.3.2/src'
make: *** [install-recursive] Error 1
$

 It seems you have re-run make command before posting its output on forums. I assume it ran successfully first time you tried it!  If thats the case, you need to run 'sudo make install' instead of 'make install' as you are not allowed to copy files without being superuser to directories involved!

---

