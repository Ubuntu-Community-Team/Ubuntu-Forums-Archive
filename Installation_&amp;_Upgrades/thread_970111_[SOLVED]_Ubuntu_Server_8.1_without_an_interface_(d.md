---
title: "[SOLVED] Ubuntu Server 8.1 without an interface (desktop)"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by rothdavid on 2008-11-03
Hi, Seasoned/spoiled Microsoft IT person trying to make the switch.  DL and installed Ubuntu Server 8.1, post install, GRUB error sent me to google and find super_grub_disk_0.9766 which I booted with, then ran to fix a boot error.  

Seemed to work like a charm, its booting directly to the drive but alas, its all in text mode, (dos mode) It boots, loads all of the services, and sits at the web login.  My credentials work fine but I want to get the desktop GUI that came with the install?  

Can someone assist me in fixing it so it boots into a desktop environment?

I would be greatful... I can tell, this is going to be "all uphill" for me..

Thank you

David in Florida

---

### Post by Partyboi2 on 2008-11-03
The server version of ubuntu does not install a desktop gui, if you are wanting a gui infterface you can install the ubuntu desktop from the terminal 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by cariboo on 2008-11-03
To help yourself learn, you are better off editing the configuration files by hand rather then using the few gui setup tools availabe. Most configuration files are pretty well commented, and I know they have helped me quite a bit when setting up services.

Might as well learn how to use the command line as I see it is coming in more and more MS products.

Jim

---

### Post by rothdavid on 2008-11-04
Thanks for the input Jim.  I came from dos days myself so I'm not unfamiliar with command line editing.  Any good references online to learn linux commands?  Books? etc... 

thanks

---

### Post by Partyboi2 on 2008-11-04
Here are a couple of links
[http://www.linuxtopia.org/online_books/bash_guide_for_beginners/index.html](http://www.linuxtopia.org/online_books/bash_guide_for_beginners/index.html)
[http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/index.html](http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/index.html)

---

