---
title: "php ldap_search problems"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by g0dbrz on 2007-10-29
After upgrade my ubuntu from 7.04 to 7.10 my php scripts that do ldap_search are very slow.

I made some debuging but could'nt find the solution.

the file ldap.php just do echo $ldap->getName($id);

the awnser is ok but 5 sec to show is too much.

```

# time php ldap.php 
real    0m5.964s
user    0m0.040s
sys     0m0.032s

```

thanks for any help

---

### Post by g0dbrz on 2007-10-31
i found out the problem is ldap bind not an php problem

---

