---
title: "How To Install Vsftpd ?"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by KlMASDO444 on 2010-10-02
Hi Guys i was download the package vsftpd-2.0.2.tar.gz
i want to install this package with wget and all myself without apt-get or yum

Help Please!:guitar:

---

### Post by lisati on 2010-10-02
[This]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html") might be easier.

---

### Post by KlMASDO444 on 2010-10-02
> **lisati said:**
> [This]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html") might be easier.
i did not [COLOR=#000000]request apt-get command

give me Commands with wget to install vsftpd
[/COLOR]

---

### Post by lisati on 2010-10-02
> **KlMASDO444 said:**
> i did not [COLOR=#000000]request apt-get command

give me Commands with wget to install vsftpd
[/COLOR]

I don't have them. And using "please" would be nice.

You need to extract the files into their own directory from the file you downloaded. Then look for a "readme" file which should have instructions.

---

### Post by KlMASDO444 on 2010-10-02
> **lisati said:**
> I don't have them. And using "please" would be nice.

You need to extract the files into their own directory from the file you downloaded. Then look for a "readme" file which should have instructions.

sorry man i was dont want to harm you

Help Please :)

---

### Post by lisati on 2010-10-02
There are installation instructions at [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.3.2/INSTALL](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.3.2/INSTALL)

If you need any further help, feel free to ask.

---

### Post by KlMASDO444 on 2010-10-02
> **lisati said:**
> There are installation instructions at [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.3.2/INSTALL](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.3.2/INSTALL)

If you need any further help, feel free to ask.

Thanks Man But Help Please:
yair@ubuntu:/opt/vsftpd-2.0.2$ make install
if [ -x /usr/local/sbin ]; then \
        install -m 755 vsftpd /usr/local/sbin/vsftpd; \
    else \
        install -m 755 vsftpd /usr/sbin/vsftpd; fi
install: cannot stat `vsftpd': No such file or directory
make: *** [install] Error 1

cp vsftpd /usr/local/sbin/vsftpd
cp: cannot stat `vsftpd': No such file or directory
:guitar:

---

### Post by KlMASDO444 on 2010-10-02
help Please:confused:

---

### Post by lisati on 2010-10-02
Like I said before, you will have to extract the files in the tarball first. From the command line, this is usually done with something like this:
```
tar xzfv TarBallName.tar.gz
```
For the file you have downloaded, the appropriate command would be something like:
```
tar xzfv vsftpd-2.0.2.tar.gz
```
Then navigate to the folder with the extracted files, using something like:
```
cd vsftpd-2.0.2
```
Have a look for a file with a name like "readme": if you're lucky there will be one it *might* contain useful instructions that will help you figure out how to install your program.

**Note:** if you're not running a server, something like Samba or NFS might be a better choice of file sharing programs.

---

