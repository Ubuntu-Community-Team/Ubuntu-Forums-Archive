---
title: "PHP5.2.x with php5-imap not working correclty."
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by BlackDex on 2008-06-10
Hello there,

I need to use imap_open() to open an email file (mbox file).
On the live server everything works, same PHP, same imap etc..

On the test server (local) it doens't.
I get the following message: "Warning: imap_open() [function.imap-open]: Couldn't open stream /path/to/file in ..."

The file is fully accessable i can get the contents of the file within php etc..

I use that same file to test on the live server, and then i get a correct resource: resource(42) of type (imap).

Can someone help me to fix this?

Thx in advanced.

---

