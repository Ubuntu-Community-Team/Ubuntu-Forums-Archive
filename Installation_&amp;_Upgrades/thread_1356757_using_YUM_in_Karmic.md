---
title: "using YUM in Karmic"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by chuina on 2009-12-16
Hey,

I install **yum** in my Karmic.
installed **alien** to make deb--->rpm.
I can also make a  repo with createrepo.
But **yum** require some dependencies though they r already 
installed !!!

Any idea for using **yum** in Karmic as i used in RHEL/Fedora ???

Thanks

---

### Post by earthpigg on 2009-12-16
> **chuina said:**
> 
Any idea for using **yum** in Karmic as i used in RHEL/Fedora ???

i've never tried it myself, but i suspect it would be less work/time on your end to simply learn to use apt-get...

---

### Post by chuina on 2009-12-16
well etherpigg (senior), thanks,

i install all of my packages with apt-get/aptitude.
But if **yum** is fully functional then we can use it
in any pc whiteout connecting the web.

because i've install Karmic in one of my friends
pc. he can't connect to the web through his eth0.
but can ping his ISP.

also he live in a remote place. and also new in Linux.

so, it will be great if **yum** is workable without connecting the 
net for once !!!

thats why i'm trying to configure **yum**

thanks, waiting for further advise ...:guitar:

---

### Post by earthpigg on 2009-12-16
ah, i think i see the problem now.

you need to get ubuntu packages to your friend's ubuntu machine that doesn't have internet access, while you yourself ***do*** have internet access, but use Fedora/RHEL instead of ubuntu?

maybe this will be useful to you:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

the binary only comes in .deb format, which does you no good being on a Fedora machine, ***but*** you can install ubuntu or debian in [VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox") and use APTonCD to build your custom cd repository for your friend there.

still not a direct answer to your quesion (can't help you there because i've never tried it...), but another option you have.

---

### Post by chuina on 2009-12-16
Sir,

I install the APTonCD. And saw that i'll burn the pckcages
installed in my PC.
After that how shall i be able to use **apt-get** from that CD ? 
i.e. what will be the **/etc/apt/sources.list** entry ?

Also I didn't understand the VirtualBox issue !

thanks again.

---

### Post by earthpigg on 2009-12-16
well, if you got aptoncd working then i guess the virtualbox thing was a non-issue for you. nevermind, i was probably doing to much thinking. :D

in synaptic, settings -> sofware sources -> third party software -> add cdrom

i don't actually remember what the exact entry in /etc/apt/sources.list looks like, but you could certainly take a look after you add the cdrom as a repo.

---

### Post by chuina on 2009-12-16
Thanks a lot Sir.

I hope this will work as a off-line installer perfectly.
It will help to create my private/local Ubuntu community/group.:lolflag:

---

### Post by Cheesemill on 2009-12-16
You could also try [Keryx]("http://keryxproject.org/").

---

### Post by chuina on 2009-12-16
Thanks Cheesemill,

Is **Keryx** related for **KDE** desktop ?

Then i'll have a double problem !!!](*,)
Cause, my **Live Karmic** cd don't have the **KDE** (as far as know).

---

### Post by chuina on 2009-12-16
Ok i got it.
Its not for KDE.
But the version there is for Jaunty.
Though i download it . I'll try with it too.
Thanks for Khelp.

---

### Post by chuina on 2009-12-17
Still i wish to use **yum** (I'm little bit fan of it)(and i have no problem with APTonCD),

I think yum is requiring already installed dependencies in **rpm** format 
just for installing purpose. Like
 sometime **apt-get** use some packages 
during install & then** delete after **the install.

for e.g. 

```
chuina@tamjid-desktop:~$ sudo yum install squid
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package squid.i386 0:2.7.STABLE6-3 set to be updated
--> Processing Dependency: libpthread.so.0(GLIBC_2.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libldap_r-2.4.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.1) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libcrypt.so.1 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libcom_err.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpthread.so.0(GLIBC_2.3.2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpthread.so.0(GLIBC_2.1) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.7) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libcrypt.so.1(GLIBC_2.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libkrb5.so.3 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpam.so.0(LIBPAM_1.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: librt.so.1 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libm.so.6(GLIBC_2.1) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libgssapi_krb5.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpthread.so.0(GLIBC_2.2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libm.so.6(GLIBC_2.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libdb-4.7.so(DB4_7) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: perl(vars) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.1.3) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpam.so.0 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: liblber-2.4.so.2(OPENLDAP_2.4_2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: liblber-2.4.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /bin/sh for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libm.so.6 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libnsl.so.1(GLIBC_2.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: perl(Getopt::Std) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.4) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /usr/bin/perl for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libnsl.so.1 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libgssapi_krb5.so.2(gssapi_krb5_2_MIT) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.3) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.3.2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libdb-4.7.so for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libc.so.6(GLIBC_2.3.4) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libldap_r-2.4.so.2(OPENLDAP_2.4_2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpthread.so.0 for package: squid-2.7.STABLE6-3.i386
--> Running transaction check
---> Package libc6.i386 0:2.10.1-1 set to be updated
---> Package squid.i386 0:2.7.STABLE6-3 set to be updated
--> Processing Dependency: libldap_r-2.4.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libcom_err.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libkrb5.so.3 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpam.so.0(LIBPAM_1.0) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libgssapi_krb5.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libdb-4.7.so(DB4_7) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: perl(vars) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libpam.so.0 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: liblber-2.4.so.2(OPENLDAP_2.4_2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: liblber-2.4.so.2 for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /bin/sh for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: perl(Getopt::Std) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /usr/bin/perl for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libgssapi_krb5.so.2(gssapi_krb5_2_MIT) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libdb-4.7.so for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: libldap_r-2.4.so.2(OPENLDAP_2.4_2) for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /usr/bin/perl for package: squid-2.7.STABLE6-3.i386
--> Processing Dependency: /bin/sh for package: squid-2.7.STABLE6-3.i386
--> Finished Dependency Resolution
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libpam.so.0(LIBPAM_1.0) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libpam.so.0 is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libcom_err.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: perl(vars) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libdb-4.7.so is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: liblber-2.4.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: /usr/bin/perl is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: /bin/sh is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: perl(Getopt::Std) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libldap_r-2.4.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libgssapi_krb5.so.2(gssapi_krb5_2_MIT) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libldap_r-2.4.so.2(OPENLDAP_2.4_2) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libgssapi_krb5.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: liblber-2.4.so.2(OPENLDAP_2.4_2) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libdb-4.7.so(DB4_7) is needed by package squid-2.7.STABLE6-3.i386 (base)
squid-2.7.STABLE6-3.i386 from base has depsolving problems
  --> Missing Dependency: libkrb5.so.3 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: liblber-2.4.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: perl(Getopt::Std) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libgssapi_krb5.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libldap_r-2.4.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libpam.so.0 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: /usr/bin/perl is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libcom_err.so.2 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libkrb5.so.3 is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libgssapi_krb5.so.2(gssapi_krb5_2_MIT) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: /bin/sh is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: perl(vars) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libdb-4.7.so is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libpam.so.0(LIBPAM_1.0) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libdb-4.7.so(DB4_7) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: libldap_r-2.4.so.2(OPENLDAP_2.4_2) is needed by package squid-2.7.STABLE6-3.i386 (base)
Error: Missing Dependency: liblber-2.4.so.2(OPENLDAP_2.4_2) is needed by package squid-2.7.STABLE6-3.i386 (base)
 You could try using --skip-broken to work around the problem
 You could try running: package-cleanup --problems
                        package-cleanup --dupes
                        rpm -Va --nofiles --nodigest
The program package-cleanup is found in the yum-utils package.

```As you can see most of the dependencies missing are already installed by default/Karmic.

Any proper solution to using **yum** will be nice.

---

