---
title: "Crypt::RSA Problems with Perl CPAN"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by nodgesoft on 2006-05-30
Hey Guys,
For some reason I have been able to run any perl programs with Crypt::RSA. Whenever I try perl -MCPAN -e 'install Crypt::RSA' i get make errors. From what I can see I think its because it has in issue compiling Pari. I install peri from the repositories but CPAN still doesnt reconise its installs and tries to download and install it as its a dependency.

I have even tried downloading the crypt::rsa tar.gz file to install that but I get more errors.

Please help me! I have been searching the net and trying heaps of various different things to get this working to no avail.

-Matt

---

### Post by nodgesoft on 2006-05-30
forgot to add - couldnt find a libcrypt-rsa package or anything else and I have installed all of the libcrypt* packages.

Can anyone point me in the right direction??

-Matt

---

### Post by ebash on 2006-05-31
[QUOTE=nodgesoft]forgot to add - couldnt find a libcrypt-rsa package or anything else and I have installed all of the libcrypt* packages.

Can anyone point me in the right direction??

-Matt[/QUOTE]

Here is how I managed to install the libraries, although Math::Pari was giving me lots of problems but with this method everything works smoothly. Keep in mind that these instructions will use the previous version of Math::Pari and libpari.

Start by installing the required packages that are available in the repository:
```
sudo apt-get install libcrypt-blowfish-perl libdigest-sha-perl libcrypt-cbc-perl libdigest-md2-perl libsort-versions-perl libcrypt-des-perl
```

Then install Math::Pari manually:

```

wget http://search.cpan.org/CPAN/authors/id/I/IL/ILYAZ/modules/Math-Pari-2.010703.tar.gz

tar zxf Math-Pari-2.010703.tar.gz
cd Math-Pari-2.010703/
wget ftp://megrez.math.u-bordeaux.fr/pub/pari/unix/pari-2.1.7.tgz
tar zxf pari-2.1.7.tgz
perl Makefile.PL
make
make test
sudo make install

```

Once done with the installation of Math::Pari you can remove the folder and continue with the installation of the module Crypt::RSA with all it's dependencies (every time that CPAN asks you to install a dependency answer 'yes')

```
sudo cpan Crypt::RSA
```

That's it.

---

