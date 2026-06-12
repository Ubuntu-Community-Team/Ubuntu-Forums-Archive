---
title: "Oracle Universal Installer not working On 9.10"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by badguyanil on 2010-04-25
Hello every body,

I have been trying to install Oracle 11g on Ubuntu 9.10. I failed pretty badly. Now i need to uninstall 11g and the scrren does not come up. please check the screen shot attached.. any clues will be helpful.

Also for 11g installation there are a set of libs mentioned. Can someone guide me as to where can i find these?

--regards

-- the above problem oocurs if you have the visual effects on!!!! strange by turning it off atleast gives me the window controls :)

---

### Post by terri1 on 2010-04-25
Hi I was able to install 10g and 11g on the Hardy Heron, but I am having problems with trying the install on 9.10.

I am getting the following problem :-

After running ./runInstaller -ignoreprereq in an xterm window I get

./runInstaller: 63  /home/oracle/database/install/.oui: not found

but this does exist when I do an ils -lart

Did you have this problem ?

Thanks

Terri

---

### Post by badguyanil on 2010-04-26
Hi Terry,

I am not sure why are you getting that error. I followed this blog to install Oracle 11g.
<code>http://en.kioskea.net/faq/4405-linux-installing-oracle-11g-on-ubuntu</code>

Although i have not had great sucess. The pre-requsite check while istallation fails with these missing libraries.
make-3.80
binutils-2.15.92.0.2
gcc-3.4.6
libaio-0.3.105
glibc-2.3.4-2.41
compat-libstdc++-33-3.2.
elfutils-libelf-0.97
elfutils-libelf-devel-0.97
glibc-common-2.3.4
glibc-devel-2.3.4
glibc-headers-2.3.4
gcc-c++-3.4.6
libaio-devel-0.3.105
libgcc-3.4.6
libstdc++-3.4.6
libstdc++-devel-3.4.6
sysstat-5.0.5
unixODBC-2.2.11
unixODBC-devel-2.2.11
pdksh-5.2.14

Any idea how to go abt installing these libs. Since you have already done it on prev version you must have the way :)

...reagards badguyanil

---

### Post by terri1 on 2010-04-26
Hi [FONT=Times New Roman]Badguyanil,
Thanks for the link.
I ran the installer with no pre-checks as follows :-
 
[/FONT][SIZE=3]./runInstaller -ignoreprereq
 
The command is sudo apt-get  (then library name required)
 
to get the libraries I used the following commands :-
 
sudo apt-get install gcc make binutils lesstif2 libc6 libc6-dev rpm libmotif3 libaio libstdc++5 gawk alien libg++2.8.1.3-glibc2.2 ksh gcc-3.3 g++-3.3 libstdc++5
 
This resulted in the following
 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
gcc is already the newest version.
make is already the newest version.
binutils is already the newest version.
lesstif2 is already the newest version.
libc6 is already the newest version.
libc6-dev is already the newest version.
libc6-dev set to manually installed.
rpm is already the newest version.
libmotif3 is already the newest version.
Package libaio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
libaio1
E: Package libaio has no installation candidate
 
Hope this helps.
Cheers,
Terri1
[/SIZE]

---

### Post by badguyanil on 2010-04-26
Thanks Terry,

I did that and this is the output i get when trying to install the packages:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
binutils is already the newest version.
libc6 is already the newest version.
libc6-dev is already the newest version.
rpm is already the newest version.
rpm set to manually installed.
libmotif3 is already the newest version.
Note, selecting libaio1 instead of libaio
libaio1 is already the newest version.
gawk is already the newest version.
E: Couldn't find package libg++2.8.1.3-glibc2.2

so all seems good and happy. But when i install Oracle DB the prerequisite check reports a lot of failures as in the attached screenshot. Did I miss something.

...Regards

---

