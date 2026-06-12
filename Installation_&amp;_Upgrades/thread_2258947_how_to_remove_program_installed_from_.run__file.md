---
title: "how to remove program installed from .run  file"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by mahmodifard on 2014-12-31
hello . how to unstall program installed from .run  file  such as salome for example .

---

### Post by schragge on 2014-12-31
Good question. Unfortunately, there is no universal answer. It depends on the program you installed. Programs installed like this usually put their files into directories not controlled by distibution package management software, most likely under either /usr/local or /opt file hierarchy. But ultimatively, you should consult documentation coming with the program in question.

---

### Post by MAFoElffen on 2014-12-31
A universal explanation to this is that a .run file is an install script. It's really up to the creator of that script if they want to include help or uninstall logic in that script. If they did, then hopefully they used a somewhat compliant Linux method for that.

So the two things to try would be to say:
```

sh fileName.run --help  # which might show help hints
sh fileName.run --unistall # which might be a compliant way to start any uninstall logic if it were included in that script.

```
But like I said, that would be up to the creator of that script.

---

