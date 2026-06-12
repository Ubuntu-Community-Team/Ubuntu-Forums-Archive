---
title: "php5-dbg installed, no debug symbols found"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Johnco on 2010-11-14
I am attempting to debug a php SIGSEGV on my Ubuntu 9.10, and therefore have installed php5-dbg.

However, once I start php on gdb I get the following output:

```
Reading symbols from /usr/bin/php...Reading symbols from /usr/lib/debug/usr/bin/php5...done.
(no debugging symbols found)...done.
```

Of course no debugging symbols are available, and debugging is impossible.

Can anybody help me?

---

### Post by lucidmyth on 2010-12-07
Hi Johnco, were you able to create a backtrace ?
I have the same problem. There seems to be little info on how to proceed. The only thing I found was this post of someone with a similar problem:
> I have installed php5-dbg. In the package list is: /usr/lib/debug/usr/lib/apache2/modules/libphp5.so

So I edited my /etc/apache2/mods-eanbled/php5.load to use this file:
LoadModule php5_module /usr/lib/debug/usr/lib/apache2/modules/libphp5.so
And then did a /etc/init.d/apache2 restart and apache just seg-faults on startup. I went ahead and disabled all dynamically loaded libraries for php, and apache still seg-faults.

How do I use this debug build of the package?

I tried this, the new libphp5.so has debug symbols but it segfaults now on startup just as the guy in this post.

---

