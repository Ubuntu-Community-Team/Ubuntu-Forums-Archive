---
title: "export path doesn't work on ubuntu 12.04"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by miousername on 2013-02-14
Hi at all,

I'm trying to launch a binary file form shell in this way:

#/opt/some/binary/file/binaryfile

but shell answer:

#/opt/some/binary/file/binaryfile
/opt/some/binary/file/binaryfile : no such file o directory

but the path is ok and the binary file is in that path.

I'm tried also:

chmod 777 -R /opt/

without success.

Where is my mistake?

---

### Post by schragge on 2013-02-14
Are you trying this as root? Why? Is it what you're typing on the command line?
```

[color=green]# [/color]/opt/some/binary/file/binaryfile

```

Anyway, what are the file permissions (*ls -l /opt/some/binary/file/binaryfile*)?

---

### Post by miousername on 2013-02-17
Found the solution:

#apt-get install ia32-libs

My application didn't find 32 bit libs in my 64 bit pc!

Thank you for your reply!

---

