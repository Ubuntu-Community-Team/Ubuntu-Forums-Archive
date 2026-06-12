---
title: "kernel upgrade problem"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by jalrnc on 2005-02-15
Following today's kernel security update notice:

[http://www.ubuntuforums.org/showthread.php?p=70770#post70770](http://) 

I used apt-get to upgrade my kernel:

```
apt-get update
apt-get upgrade
```

Two packages were kept back... so I did:

```
apt-get dist-upgrade
```

But I still get 1 package kept back...

```
The following packages have been kept back:
  linux-restricted-modules-2.6-686
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

And if I do the following:

```
apt-get install linux-restricted-modules-2.6-686
```

I get:

```
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-restricted-modules-2.6-686: Depends: linux-restricted-modules-2.6.8.1-5-686 but it is not installable
E: Broken packages
```

Is this something I should be concerned about?

Thanks,
João

---

### Post by s.deleeuw on 2005-02-15
Same problem here. The linux-restricted-modules-2.6-686 linux meta package is broken. It depends on the non-existing package linux-restricted-modules-2.6.8.1-5-686.

So people, don't upgrade until this is fixed!

---

