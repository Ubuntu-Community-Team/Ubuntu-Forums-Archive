---
title: "how to make universe rep dvd?"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by j_goldie on 2005-06-27
hi all,
since i have really crappy internet connection, and really no real place to download packages from universe repository(i have read docs for apt-zip), i was wondering how would it be possible to download universe repository, burn it on DVD and add it to a repository. I'm asking this because only apt-get update lasted for more than 30 minutes!!

---

### Post by jrev on 2005-06-27
could be a good idea to start with...
just find a spot where you can download at high speed and use :
wget -r -np "http or ntp address"
you might need more than one DVD ...

---

### Post by j_goldie on 2005-06-27
[QUOTE=jrev]could be a good idea to start with...
just find a spot where you can download at high speed and use :
wget -r -np "http or ntp address"
you might need more than one DVD ...[/QUOTE]

Ok, i got ya. But... Since there are packages for powerpc, i386 and amd64, would it be ok if i could just download for example i386 packages along with without messing with packages.gz files? I mean, what files should i download? Is it from ../dists/hoary/universe/binary-i386/ to get packages, and then form pool dir? What i'm trying to say, how folders should be organized so that synaptic can accept the repository?

                                 thanx in advance,
                                              j_goldie
p.s.
just a try....
there's a regular expression for testing for downloading all deb files but not amd64 and powerpc files - ((.*(?<!(powerpc|amd64.d)))\.*\.deb) Of course, there are non deb files also in the pool which should be downloaded.

---

### Post by j_goldie on 2005-06-27
[QUOTE=j_goldie]
...there's a regular expression for testing for downloading all deb files but not amd64 and powerpc files - ((.*(?<!(powerpc|amd64.d)))\.*\.deb) ....[/QUOTE]
sorry folks,  :oops: i know that's not the place for the regular expressions, but i hate wrong information ](*,)  laying around. Anyway the proper regular expression is **((.*(?<!(powerpc|..amd64)))\.*\.deb)** :-\"

---

