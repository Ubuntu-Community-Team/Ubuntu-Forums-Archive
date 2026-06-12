---
title: "what is commandline of synaptic"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by willemijns on 2006-12-27
hi,

i want to install with a commandline some packages i have drag & drop from a web page to my desktop... i have tried a lot of commands line with apt-get but only synaptic can well
install my packahes :-(

what is the commandline used by this software to (force to) install packages in a hard disk ? 

ps: do not answer me "sudo su + apt-get install" it does not works !!! only synaptic 
can well install my package because i think they are an version error dependencies
in "ubuntu apt-get" master listfiles...

---

### Post by s6dalane on 2006-12-27
If those files you downloaded are *.deb's*, then you can install them via this command:

> sudo dpkg -i package_name

Also, [THIS]("http://monkeyblog.org/ubuntu/installing/") page may have an answer to your problem, if the above does not work.

---

