---
title: "problem with compiling GROMACS"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by arunbeta on 2007-07-17
i tried installing GROMACS software.. it says to run 
./configure
make
make install

but wen i reun ./configure i get the following message

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for cc... cc

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

it seems like its a pretty easy to correct, but its my 1st week with ubuntu n linux.. so would greatly appreciate any help ..

---

### Post by TBerben on 2007-07-30
Execute:
```
sudo apt-get install g++
```

That should fix it :)

---

