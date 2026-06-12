---
title: "Problem installing MPEG::MP3Info"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by rene53 on 2007-12-15
Hello
When i try to install MPEG::MP3info under CPAN in Ubuntu 7.04 than i get the message on the end of the install that it cant install a file. here is the message:

Running make install
Warning: You do not have permissions to install into /usr/local/lib/perl/5.8.8 at /usr/share/perl/5.8/ExtUtils/Install.pm line 114.
mkdir /usr/local/share/perl: Permission denied at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 13
  /usr/bin/make install  -- NOT OK
    You may have to su to root to install the package

Is there a chance i can manuali install what i need, and if so how do i do it ?
I'm a newbee with Ubuntu and still learning.

I have chanched the properties of the map "perl" from only read to read and write, but that was not the solution.

regards, Rene53

---

### Post by llamakc on 2007-12-15
Many Perl modules are already available to you in the repositories, and you can find them in Synaptic or by using `apt-cache search` in the terminal.

For future reference perl modules are named libAAA-BBB-perl, where AAA represents the first part of the module name and BBB the second.

The module you are looking for is now known by the name libmp3-info-perl

And can be installed with

```

sudo apt-get install libmp3-info-perl

```

---

### Post by rene53 on 2007-12-15
I have done that but it dit not solved the problem, i still could not install MPEG::MP3Info in CPAN. I want it for running ( building) jukebox4.1 and when i do so i stil get this message at the moment it must make install:

Running make install
Warning: You do not have permissions to install into /usr/local/lib/perl/5.8.8 at /usr/share/perl/5.8/ExtUtils/Install.pm line 114.
mkdir /usr/local/share/perl: Permission denied at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 13
/usr/bin/make install -- NOT OK
You may have to su to root to install the package

Why do i  ( or the programm ) have no permission?
Can i fix that?

 ( sorry for the faults in my text, but i'm no englischman )

---

### Post by llamakc on 2007-12-15
Enter cpan as root with sudo?

---

### Post by rene53 on 2007-12-15
Tank you, thank you, thank you!!!
That was the solution, now i can go further!

Case closed!
Regards, Rene

---

