---
title: "Could not initialize the package information"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by dheevatsa on 2008-09-10
I am gettign the following problem with my synaptics package manager whenever i try to start it up...can anyone please help me resolve this...i need to install some packages in a hurry...thanks

problem:

A unresolvable problem occurred while initializing the pac****kage information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 58 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

---

### Post by iaculallad on 2008-09-10
Post the content of your sources.list file:

```
cat /etc/apt/sources.list
```

Or you could manually check it yourself as it points out that line 58 has the error.

---

