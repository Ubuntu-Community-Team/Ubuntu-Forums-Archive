---
title: "Synaptic corruption"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by banyuken on 2005-06-09
Hi, I tried to install Eclipse from two repositories from the internet, and I couldn't get it, so I opened Synaptic for removing them, and when I mark them and clic on Apply changes, the operation never ends without errors. The matter is that when I open Synaptic again the packages from Eclipse are still marked, and it's impossible for me to deselect them. And if I try to install another packages, different of them, Synaptic always crash, for Eclipse corrupt packages, and it does impossible for any other package to be installed. So my question is: how can I clear the list of packages that Synaptic has marked? I can't do it by the interface, I find that you can see in tha attached file.
Thanks,
Banyu.

---

### Post by defkewl on 2005-06-09
Have you tried uninstalling it via command line?

---

### Post by banyuken on 2005-06-09
I put here some examples of what I'm doing. It is always failing:

dpkg -ra eclipse-source
dpkg --pending eclipse-source
dpkg -a eclipse-source
dpkg --force-remove-reinstreq eclipse-source
dpkg --remove eclipse-source
dpkg --purge eclipse-source
...

And when I don't get a syntax error  ](*,)  I get the same message that Synaptic gives me, this is  [-X 

Thanks,
Banyu.

---

### Post by zAo on 2005-06-09
Edit => unmark all marked packages.

---

### Post by banyuken on 2005-06-09
Sorry zAo but it wasn't so easy... I had to enter "/var/lib/dpkg/info" and do "ls -la ec*", then I got:

-rw-r--r--  1 root root     0 2005-06-09 13:20 eclipse-jdt.list
-rw-r--r--  1 root root 77511 2005-06-03 04:32 eclipse-jdt.md5sums
-rwxr-xr-x  1 root root    96 2005-06-03 04:32 eclipse-jdt.postinst
-rwxr-xr-x  1 root root    93 2005-06-03 04:32 eclipse-jdt.postrm
-rw-r--r--  1 root root     0 2005-06-07 23:20 eclipse-platform.list
-rwxr-xr-x  1 root root   111 2005-06-03 04:32 eclipse-platform.postrm
-rw-r--r--  1 root root     0 2005-06-09 13:20 eclipse-source.list
-rw-r--r--  1 root root 52485 2005-06-03 04:32 eclipse-source.md5sums
-rwxr-xr-x  1 root root    96 2005-06-03 04:32 eclipse-source.postinst
-rwxr-xr-x  1 root root    93 2005-06-03 04:32 eclipse-source.postrm

So I did: "rm -rf ecli*". And voilà, I opened Synaptic and they had gone  \\:D/ 

Thanks anyway...

Banyu.

---

