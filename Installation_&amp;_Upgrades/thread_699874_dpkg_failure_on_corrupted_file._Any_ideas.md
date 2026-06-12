---
title: "dpkg failure on corrupted file. Any ideas?"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by bturrie on 2008-02-17
so, I just installed xubuntu feisty on an old machine. When I went to upgrade using synaptic, I got this

"E: /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb: corrupted filesystem tarfile - corrupted package archive"

Not sure at all what it is, or what it means but I'm thinking I got a corrupted file from the mirror. I have a freshly updated apt-mirror on another box and I get the same error when I point sources.list there.

---

### Post by bbl232 on 2008-02-17
hey, i was having the same problem and found an easy as HELL! solution.  go to Synaptic package manager and completely remove the open office suite, this solved it 4 me.

---

### Post by bturrie on 2008-03-04
I recieved the following email from Aaron Albright

Try running:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install hplip
(assuming you where trying to install hplip via this way)

It looks like your cache might be corrupt, or incomplete.

Hope this helps.


It worked. Thanks Aaron

---

