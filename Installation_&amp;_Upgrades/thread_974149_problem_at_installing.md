---
title: "problem at installing"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2008-11-07
Hi there,

I'm trying to install a USB scanner using [this tutorial]("http://ubuntuguide.org/wiki/Dapper#How_to_install_a_USB_scanner"), but I have the following problem:
```

muc@muc-desktop:~/Desktop$ sudo dpkg -i iscan_2.3.0-2_i386.deb 
(Reading database ... 98039 files and directories currently installed.)
Preparing to replace iscan 2.3.0-2 (using iscan_2.3.0-2_i386.deb) ...
Unpacking replacement iscan ...
Setting up iscan (2.3.0-2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
what's happeing ? why do i have the message "ldconfig deferred processing now taking place"? Hows to solve that problem.

I'm not sure, but I don't have in /etc/udev/rules.d/ the 025-libsane-extras.rules file. That is the cause of this missing file?

How to solve this problem?

Many thanks!

---

### Post by dabl on 2008-11-07
You realize that tutorial is over two years old?  What model scanner, and which version of Ubuntu are you working with?

---

### Post by sandy8925 on 2008-11-07
"ldconfig deferred processing"  isn't a problem. I've noticed it always takes place whenever you install something.

---

### Post by mucmicu on 2008-11-07
I'm trying to install a Epson Perfection V10 USB scanner on a Ubuntu 8.04. I have the same problem with Ubuntu 8.10

Who can help me to install it if that tutorial is too old and bad? Need some help on that. 

1) How can I check that iscan was installed nicely?
2) where is the 025-libsane-extras.rules file?

Many thanks!

---

### Post by mucmicu on 2008-11-07
Now i have both on my machine Ubuntu 8.04 and 8.10 on myu machine, and I have the same problem. Who can help me?

---

