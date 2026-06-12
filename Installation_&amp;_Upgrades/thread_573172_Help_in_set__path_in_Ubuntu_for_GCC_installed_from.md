---
title: "Help in set  path in Ubuntu for GCC installed from GNU"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by ahjiefreak on 2007-10-11
Hi,

I am actually quite new to Linux and currently installed Ubuntu 6.06. And I downloaded GCC-source code from the GNU webpage.

And, I managed to unpack them. In Ubuntu 6.06 which I installed, I unchecked the built-in GCC package as well as the base.

Then, I set my own path in the below command:-

echo $PATH
and followed by EXPORT PATH=/local/gcc/gcc-4.2.1/bin/:$PATH

It returns me "undeclared identifier" .

And, I have no idea where did I do wrong. Since I removed the built in gcc package in Synaptics, when i query gcc -v it returns me "bash:command not found"

Finally, I have to re installed back the packages, and then when I run the PATH it doesnt return me the "undeclared" error. However, when I executed gcc -v it returns me to the default gcc that come with ubuntu instead the one I installed from GNU.

Please help as I do not know where to set the path correctly to point to the exact point of GCC I am installing.

Appreciate alot. Thanks.


Rgrds,
Jason

---

### Post by taurus on 2007-10-11
Did you unpack the new GCC binary or source?  What's the output of this command from a terminal?

```
ls -la /local/gcc/gcc-4.2.1/bin
```

---

