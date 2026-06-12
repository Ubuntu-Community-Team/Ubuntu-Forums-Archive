---
title: "GTK+ problems"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by ksp1717 on 2012-05-13
Hi 

I am running Ubuntu 10.04 LTS. I have upgraded the gtk+ package to GTK+-3.4.3 inorder to install gimp-2.8. But after the update when I run

```
 dpkg -l libgtk[0-9]* | grep ^i

```

I get the following output. 
> ii  libgtk2-perl                              1:1.221-4ubuntu2                                Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                               2.20.1-0ubuntu2.1                               The GTK+ graphical user interface library
ii  libgtk2.0-bin                             2.20.1-0ubuntu2.1                               The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                             2.12.9-4                                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                          2.20.1-0ubuntu2.1                               Common files for the GTK+ graphical user interface library
ii  libgtk2.0-dev                             2.20.1-0ubuntu2.1                               Development files for the GTK+ library


When I try to configure gimp I get the error saying gtk+ >= 2.24 is needed. 

Can someone help me fix this ?

I have installed all the pre reqs required for gtk+-3.4 and I successfully installed gtk+-3.4 ( I did not get any errors when I run 'sudo make install' for gtk+-3.4).

Thanks

--ksp

---

