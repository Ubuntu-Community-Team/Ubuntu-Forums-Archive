---
title: "Wicd in Intrepid Ibex 8.10"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by joonyah on 2008-10-01
Is it possible to install Wicd in Intrepid Ibex.  I tried adding the hardy repo, and tried changing that to intrepid and each time I get an error when I run apt-get update "W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUKEY FEC820F4B8C0755A"

-- jon

---

### Post by imdano on 2008-10-01
Run this command and it should work. ```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

---

