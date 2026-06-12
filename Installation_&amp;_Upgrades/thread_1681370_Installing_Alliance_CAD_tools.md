---
title: "Installing Alliance CAD tools"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by lee-anna-loo on 2011-02-04
Hello I have problem installing the Alliance CAD tools.

I have Ubuntu 10.04.

I can't find the alc_env.sh file in the source files, so I wanted to install it from the binary, but when I run ./configure i get the following:

> configure: error: The Motif library '-lXm' could not be found.
                  Please use the configure options '--with-motif-includes=DIR'
                  and '--with-motif-libraries=DIR' to specify the Xm location.
                  See the files 'config.log'
                  for further diagnostics.

any ideas how can I solve this problem?

Thank you in advance :)

---

### Post by sharat.kashimath on 2011-02-09
try installing libmotif3 and libmotif-dev from your synaptic and then  configure alliance

---

### Post by lee-anna-loo on 2011-02-09
I had libmotif3, what I was missing was libmotif-dev..

After installing it I succeeded to configure alliance, but now the installing is falling (I'm using "make install"):

> ./bvl_bcomp_y.y: In function 'chkdcl':
./bvl_bcomp_y.y:258: error: 'BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:258: error: (Each undeclared identifier is reported only once
./bvl_bcomp_y.y:258: error: for each function it appears in.)
./bvl_bcomp_y.y:263: error: '_IN' undeclared (first use in this function)
./bvl_bcomp_y.y:265: error: '_OUT' undeclared (first use in this function)
./bvl_bcomp_y.y:267: error: '_INOUT' undeclared (first use in this function)
./bvl_bcomp_y.y:269: error: '_LINKAGE' undeclared (first use in this function)
./bvl_bcomp_y.y:277: error: 'MUX_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:291: error: 'BUS' undeclared (first use in this function)
./bvl_bcomp_y.y:295: error: 'WOR_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:313: error: 'REG_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:314: error: 'NATURAL' undeclared (first use in this function)
./bvl_bcomp_y.y:365: error: 'REGISTER' undeclared (first use in this function)
./bvl_bcomp_y.y: In function 'addstr':
./bvl_bcomp_y.y:440: error: '_IN' undeclared (first use in this function)
./bvl_bcomp_y.y:442: error: '_OUT' undeclared (first use in this function)
./bvl_bcomp_y.y:445: error: 'BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:447: error: 'MUX_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:449: error: 'WOR_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y:453: error: '_INOUT' undeclared (first use in this function)
./bvl_bcomp_y.y:478: error: 'REG_BIT' undeclared (first use in this function)
./bvl_bcomp_y.y: In function 'addgen':
./bvl_bcomp_y.y:613: warning: format '%d' expects type 'int', but argument 4 has type 'long int'
./bvl_bcomp_y.y: In function 'bvl_select':
./bvl_bcomp_y.y:1277: warning: format '%d' expects type 'int', but argument 3 has type 'long int'
./bvl_bcomp_y.y:1333: warning: format '%i' expects type 'int', but argument 3 has type 'long int'
make[2]: *** [bvl_bcomp_y.lo] Error 1
make[2]: Leaving directory `/home/ana/Downloads/alliance/alliance-5.0/bvl/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ana/Downloads/alliance/alliance-5.0/bvl'
make: *** [install-recursive] Error 1



However I solved my problem for now, because I just needed the alc_env.sh file which is missing in the binary version (which is working fine).

---

### Post by lee-anna-loo on 2011-02-09
actually this is all I had to do to make it work (under Ubuntu 10.04):

1. download the latest binary and source archives from their [official site]("http://www-asim.lip6.fr/pub/alliance/distribution/5.0/")
(I got alliance-5.0-20090901-i386-sl5soc.i386.tar.gz and alliance-5.0-20090901.tar.gz)

2. install libmotif3 and libmotif-dev:
```
sudo apt-get install libmotif3
sudo apt-get install libmotif-dev
```

3. extract the source version:
```
tar xzf alliance-5.0-20090901.tar.gz
```

4. position in the alliance folder and "configure" the source version
```
cd alliance-5.0
export ALLIANCE_TOP=/opt/alliance-5.0
./configure --prefix=$ALLIANCE_TOP
```

5. extract the binary version in your root directory
```
sudo tar xzf alliance-5.0-20090901-i386-sl5soc.i386.tar.gz -C /
```

6. copy the alc_env.sh (or alc_env.csh) file from the source to the binary version (if you are positioned in the alliance-5.0 folder from the source version:)
```
sudo cp distrib/etc/alc_env.sh /opt/alliance-5.0/etc/
sudo cp distrib/etc/alc_env.csh /opt/alliance-5.0/etc/
```

7. each user has to source alc_env.[c]sh to set Alliance environment variables to be able to run the Alliance tools
```
cd
. /opt/alliance-5.0/etc/alc_env.sh
```

8. if you are a system admin, you should consider linking these scripts in the system's profile so that configuration would be done at user login
```
sudo ln -s /opt/alliance-5.0/etc/alc_env.csh /etc/profile.d/
sudo ln -s /opt/alliance-5.0/etc/alc_env.sh /etc/profile.d/
```

9. also in order to run the cougar and druc tool I had to copy the techno-035.rds and techno-symb.rds
```
sudo mkdir -p /usr/share/doc/alliance-doc-5.0/alliance-examples/etc/
sudo cp /opt/alliance-5.0/examples/alliance-examples/etc/techno-035.rds /usr/share/doc/alliance-doc-5.0/alliance-examples/etc/
sudo cp /opt/alliance-5.0/examples/alliance-examples/etc/techno-symb.rds /usr/share/doc/alliance-doc-5.0/alliance-examples/etc/
```


10. make sure everything is ok - for that I used [this guide]("https://fedorahosted.org/fedora-electronic-lab/wiki/HowTo/Alliance")

---

### Post by zebedar on 2012-05-27
The above issue is due to some missing include statements in the raw source.  

You need to add '#include "string.h"' to ocp/src/placer/Ocp.cpp and ocp/src/placer/PPlacement.h

You also need to add '#include "bvl_bcomp_y.h" to bvl/src/bvl_bcomp_y.y

This gets you further down the compile process...

make sure you chmod +x ./install-sh in the root directory of the raw source you're working with

Also, you need to comment out the definition of value for yylineno on line 21 of DEF_grammar_lex.l

---

