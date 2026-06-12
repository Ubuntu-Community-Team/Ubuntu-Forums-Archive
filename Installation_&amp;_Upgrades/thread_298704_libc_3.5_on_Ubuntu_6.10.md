---
title: "libc 3.5 on Ubuntu 6.10 ??"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Hubert Gosselmeyer on 2006-11-13
Heyho, 
I am having a big problem, since I upgraded to Ubuntu 6.10. Some software, which is quite important for me, seems to have a problem with libc 4.0. It crashes when it begins to start lwps! ](*,) 

So I would like to install the old libc 3.5.x or maybe 3.6. But I have no idea how to manage it. I downloaded the old debs from dapper and tried it with dpkg -i xxx.deb, but I received an error message because there was no linux-kernel-headers-package installed. Then I changed everything in apt/sources to dapper. Now I've got manage to install that nice linux-kernel-headers-package, but he says "hey, buddy, libc 4 is installed - and it's much newer than 3.5...". Wonderful... I like it... :D 

Please, what can I do, to downgrade to 3.5?

Thanks in advance. 
Hubi

---

