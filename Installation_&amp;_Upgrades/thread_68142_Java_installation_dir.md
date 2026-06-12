---
title: "Java installation dir"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by powerrangers009 on 2005-09-22
hallo
i have been trying since two days to install java's new version on my ubuntu system.
It get to start mean that im able to install it but probelm seems to be that when i start firefox and go to the website where java applet exits. what i see is that it asks me to install plugins.
what should i do?
in /usr/java/ i have a directory named "jdk1.5.0_05" and "jre1.5.0_04"
my browser still dont detect any damn java...
anybody that gives me more information about?
thanx

---

### Post by ngms27 on 2005-09-22
Yep I had the same problem.

You have to put a link in the firefox plugin directory to the plugin in the JRE or JDK then restart Firefox. The file is called libjavaplugin_oji.so and this has to be a symbolic link using ln -s

Heres mine I use the JDK

ngms27@ubuntu:/usr/lib/mozilla-firefox/plugins$ ls -l
lrwxrwxrwx  1 root root 65 2005-09-20 18:12 libjavaplugin_oji.so -> /home/ngms27/jdk1.5.0_04/jre/plugin/i386/ns7/libjavaplugin_oji.so

HTH

JonnyT

---

### Post by powerrangers009 on 2005-09-23
but i dont know how tp put a symbolic link to firefox plugin directory
can u show me how to do this ?
thanx a lot

---

### Post by ngms27 on 2005-09-23
the syntax is:

Assuming you are in the Firefox Plugins directory eg /usr/bin/mozilla-firefox/plugins

ln -s  ibjavaplugin_oji.so /home/ngms27/jdk1.5.0_04/jre/plugin/i386/ns7/libjavaplugin_oji.so

Just change the bit where your java files are located.

JonnyT

---

### Post by powerrangers009 on 2005-09-24
Thanx it helped me ! and it works now
btw the order of the command was not correct so i just turn it and executed it !!!
thanx again !

---

