---
title: "GCC &amp; similar tools: problem with strings in error messages after upgrade"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Dan Lyke on 2006-07-27
I just let my system upgrade to Dapper Drake, and after a number of purges and reinstalls of packages like CUPS it's mostly back to normal.

However, if I try to do anything with GCC or G++ I'm getting error messages like:

test.c: In function â:
test.c:5: error: â undeclared (first use in this function)
test.c:5: error: (Each undeclared identifier is reported only once
test.c:5: error: for each function it appears in.)
test.c:5: error: syntax error before â

It looks like any place that GCC is calling some printf() variant with a "%s" argument, that the following pointer is being interpreted wrong.

I've tried purging and re-installing everything I could relating to GCC without getting into dependency hells like removing libc or X, but I can't get this one to resolve itself.

Any suggestions?

---

### Post by Dan Lyke on 2006-12-15
For anyone coming along behind me who happens to stumble across this, the answer is that I don't have UTF-8 character set enabled in my terminal. Right now I'm accessing an Ubuntu box from a Mac, and, oddly, "-u8" when I invoke XTerm doesn 't seem to turn it on, but if I run the compiler from the standard terminal and an SSH server it appears to work.

---

