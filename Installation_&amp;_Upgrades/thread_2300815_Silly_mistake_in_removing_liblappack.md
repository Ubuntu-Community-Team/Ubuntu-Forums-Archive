---
title: "Silly mistake in removing liblappack"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by greenawy on 2015-10-28
I was trying to remove libblas and liblapack, but I removed the binary!!
Now when I try to install it again or even install any related package gives me the same error.
I tried to look this problem up but I found out that the errors are diverging..

the output of sudo apt-get install liblapack-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libblas-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python-pkg-resources : Depends: python_any (>= 2.7) but it is not installable
                        Depends: python_any (< 2.8) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So I tried apt-get -f install and the output is 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-pkg-resources
Suggested packages:
  python-distribute python-distribute-doc
The following packages will be upgraded:
  python-pkg-resources
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0 B/61.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 115 package 'python3-aptdaemon.pkcompat':
 `Depends' field, invalid package name `python3:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

How can I fix this up without reinstalling?

here is the output of dpkg -l 'libblas*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iF  libblas-dev    1.2.20110419 i386         Basic Linear Algebra Subroutines 
un  libblas.so     <none>       <none>       (no description available)
un  libblas.so.3   <none>       <none>       (no description available)
un  libblas.so.3gf <none>       <none>       (no description available)
ii  libblas3       1.2.20110419 i386         Basic Linear Algebra Reference im
un  libblas3gf     <none>       <none>       (no description available)

and the output of dpkg -l 'liblapack*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  liblapack-dev  3.5.0-2ubunt i386         Library of linear algebra routine
ii  liblapack-doc- 3.5.0-2ubunt all          Library of linear algebra routine
ii  liblapack-pic  3.5.0-2ubunt i386         Library of linear algebra routine
ii  liblapack-test 3.5.0-2ubunt i386         Library of linear algebra routine
un  liblapack.so   <none>       <none>       (no description available)
un  liblapack.so.3 <none>       <none>       (no description available)
un  liblapack.so.3 <none>       <none>       (no description available)
ii  liblapack3     3.5.0-2ubunt i386         Library of linear algebra routine
un  liblapack3gf   <none>       <none>       (no description available)
ii  liblapacke     3.5.0-2ubunt i386         Library of linear algebra routine
un  liblapacke.so. <none>       <none>       (no description available)

Thank you for any help

---

