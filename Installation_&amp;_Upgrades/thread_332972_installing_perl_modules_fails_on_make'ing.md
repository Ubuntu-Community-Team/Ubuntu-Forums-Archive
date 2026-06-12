---
title: "installing perl modules fails on make'ing"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by moepstar on 2007-01-06
Hi guys,

on my ubunut edgy server - which is sort of freshly installed - i got problems installing a few perl-modules that are not available with aptitude..

for example, the module POE::Component::RSSAggregator..

> 
  CPAN.pm: Going to build J/JB/JBISBEE/POE-Component-RSSAggregator-1.022.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


make is installed and i've also installed gcc but still no go - i wonder if anyone might have a clue what still could be wrong - thx :)

---

### Post by taurus on 2007-01-06
How did you install make & gcc?  Have you tried this command?

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by moepstar on 2007-01-06
> How did you install make & gcc?

I've installed them seperately.

>  Have you tried this command?

well, havent before but now i've installed build-essential but it still errors in the same way as before :(

---

### Post by moepstar on 2007-01-07
since i love to answer my own questions and fix my own problems i "just did it myself" ;)

what was wrong?

well, the perl shell has been configured first and then make, gcc and the build-essential package have been installed.

therefore, none of the newly added packages (mainly make) have been configured that they actually are there and useable.

to see if your perl-shell even is configured right you can do the following (in a shell):

> 
perl -MCPAN -e shell

o conf


and within the output from "o conf" you should see the path to the executable from make - if your line is blank or contains a wrong path it just won't work (tm)...


to make it work you need to reconfigure the perl-shell and to do so you can either open the config-file and add the path to make yourself or delete the configuration and re-run the configuration process..

> 
rm /etc/perl/CPAN/Config.pm


then just go back into the perl shell (perl -MCPAN -e shell) and configure it again and then stuff should be working :)

---

