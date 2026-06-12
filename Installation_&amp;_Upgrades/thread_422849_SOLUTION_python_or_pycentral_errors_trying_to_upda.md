---
title: "SOLUTION: python or pycentral errors trying to update/upgrade (k3d)"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2007-04-25
I ahve found 2 solutions that have been working for everyone. They are as follows:

```
sudo mv /usr/bin/pycentral /tmp/
```

```
sudo apt-get -f update
```

```
sudo apt-get -f upgrade
```

```
sudo mv /tmp/pycentral /usr/bin/
```

OR

Edit /usr/bin/pycentral, added a line : 

```
       if not self.version_field:
            self.version_field = "current"
#            raise PyCentralError, "package has no field Python-Version"
```


```
sudo aptitude install k3d
```

---

### Post by durand on 2007-06-30
thanks, this really helps a lot of people

---

