---
title: "ubuntu 10.10 &amp;&amp; fwbuilder 4.0 incompatilibity"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by cjejuni on 2011-03-11
i was building box w/ firewall. iptables not so easy. first there is firestarter, ufw, gufw. 20/20 hindsight, stay w/ ufw. 
anyway i went to help.ubuntu.com. suggested all this nice firewall apps. so it pointed to fwbuilder. so i apt-get install fwbuilder, installed fine. first time it ran, said something like 'this version fwbuilder 3.x does  not work with ubuntu 10.10'. i do not know if this was bug or it is actually tested by the ubuntu team. 
so i went downloaded the **fwbuilder.org' fwbuilder4.0 from sourceforge**, followed their install instructions.
i ended up a barely functional machine. no aptitude, apt-get, ubuntu software center, synaptic pkg manage != no update nor upgrade. the aptitude config files were corrupted. i posted here for help but to no avail. tried the aptitude fix but just downloads all pkgs needed (seemed like it downloaded the whole cd) in my local drive.
everytime i try update/upgrade or install, i'm getting this error:

E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 **apt.conf** under **APT::Immediate-Configure** for details. (2)
E: Failed to process build dependencies

then how can i replace the apt-get source list, config files, etc. to rebuild the broken files ie mount, software-center, apache2, ufw, etc?

---

