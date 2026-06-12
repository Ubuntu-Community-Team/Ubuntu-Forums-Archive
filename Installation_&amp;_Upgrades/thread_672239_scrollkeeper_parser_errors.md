---
title: "scrollkeeper parser errors"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2008-01-19
Several times while installing aplications I recieve this message in terminal:
/var/lib/scrollkeeper/en_GB/scrollkeeper_extended_cl.xml:2606: parser error : Extra content at the end of the document
        </sect>
        ^
/var/lib/scrollkeeper/ko/scrollkeeper_cl.xml:792: parser error : Extra content at the end of the document

Any ideas on whats wrong and how to fix it?

---

### Post by cmittle on 2008-01-21
I am also having this problem.  When I install programs from the command line I get several (probably 100+) that read something like

```
 /var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:764: parse error : Opening and ending tab mismatch: sect line 512 and doc
</toc></doc><doc docid="241"><doctitle>Problem showing document</doctitle><docom
```

This hasn't seemed to cause any problems with the functionalitly of the system, but seeing this many errors fly by everytime I install something is a little unnerving.

Thanks,
Cory

---

### Post by Meyithi on 2008-01-28
I have this as well (7.10 x86), anyone have any ideas?

EDIT/ No matter I tried:

```
sudo scrollkeeper-rebuilddb
```

and things seem ok now.

---

### Post by arndsen on 2008-03-04
Thank you, that does it...

---

