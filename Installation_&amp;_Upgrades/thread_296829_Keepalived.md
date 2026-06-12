---
title: "Keepalived"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Remie on 2006-11-10
Hallo;

I'd like to test keepalived-1.1.13 on ubuntu dapper.
when i do apt-get keepalived, i am told that i already have the newest version.

but, when i lookup the version it gives me 1.1.1O

i downloaded 1.1.13.  how do i install this version?

thanx

Remie

---

### Post by adwait on 2006-11-10
This is probably because the Ubuntu repos are not yet updated to have the lastest  version. Anyway, what is the extension of the file you have downloaded? If it is *.deb, you can use
```
sudo dpkg -i <filename>
```

If its *.rpm use,
```
sudo alien <filename>
```
It will tell you the name of the *.deb file generated, then use that filename and follow step 1.

If its *.tar.gz, extract the file by right clicking on it and then clicking on extract. Then run
```

./configure
make install

```

---

### Post by Remie on 2006-11-10
after typing ./configure

i get an error : openSSL is not properly installed on your system

when i type "make install" i get the following : no rule to make target 'install'. stop.

any idea

---

### Post by twsnnva on 2006-11-10
You need to install the libssl-dev package, as it is a dependency of keepalived. You can run the command "apt-get build-dep keepalived", which should download and install all of the dependencies required for keepalived. Afterwards, "./configure" should complete successfully, then you can "make && make install".

EDIT: You should keep the source code around. If you want to remove the software later, you can "make uninstall" to remove the software from your system.

---

### Post by Remie on 2006-11-10
./configure worked fine thank you 

but when i type make i get the following output


root@laptop1:/tmp/keepalived-1.1.13# make
make -C lib || exit 1;
make[1]: Entering directory `/tmp/keepalived-1.1.13/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/keepalived-1.1.13/lib'
make -C keepalived
make[1]: Entering directory `/tmp/keepalived-1.1.13/keepalived'
make[2]: Entering directory `/tmp/keepalived-1.1.13/keepalived/core'
gcc -g -O2  -I/usr/src/linux/include -I../include -I../../lib -Wall -Wunused -Wstrict-prototypes -D_KRNL_2_6_ -D_WITHOUT_LVS_ -D_WITH_VRRP_  -c main.c
make[2]: Leaving directory `/tmp/keepalived-1.1.13/keepalived/core'
make[2]: Entering directory `/tmp/keepalived-1.1.13/keepalived/vrrp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/keepalived-1.1.13/keepalived/vrrp'
Building ../bin/keepalived
/usr/bin/ld: cannot open output file ../bin/keepalived: No such file or directory
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/tmp/keepalived-1.1.13/keepalived'
make: *** [all] Error 2
root@laptop1:/tmp/keepalived-1.1.13# sudo make && make install
make -C lib || exit 1;
make[1]: Entering directory `/tmp/keepalived-1.1.13/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/keepalived-1.1.13/lib'
make -C keepalived
make[1]: Entering directory `/tmp/keepalived-1.1.13/keepalived'
make[2]: Entering directory `/tmp/keepalived-1.1.13/keepalived/core'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/keepalived-1.1.13/keepalived/core'
make[2]: Entering directory `/tmp/keepalived-1.1.13/keepalived/vrrp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/keepalived-1.1.13/keepalived/vrrp'
Building ../bin/keepalived
/usr/bin/ld: cannot open output file ../bin/keepalived: No such file or directory
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/tmp/keepalived-1.1.13/keepalived'
make: *** [all] Error 2


what went wrong?

---

### Post by twsnnva on 2006-11-10
Does the file /tmp/keepalived-1.1.13/bin/keepalived exist?

It looks like it's having a problem creating that file from the current directory. You may want to try "make mrproper", then "./configure" and "make" again.

---

