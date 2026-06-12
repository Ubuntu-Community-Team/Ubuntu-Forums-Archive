---
title: "swftools problems"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by joecomstock on 2010-03-20
tried to install the swftools first from the instructions on the website using

sudo python setup.py build
sudo python setup.py install

and when that did not work

LDFLAGS=-1stdc++ ./configure
make
make install

both methods failed

then i installed from the repos, and it installed fine.

however, the reason that i was installing this software was for the python gfx module.

when i went to the command line and checked using
sudo python -c 'import gfx'

i got a importError: no module named gfx

has anyone else had these problems and found a solution yet?

---

