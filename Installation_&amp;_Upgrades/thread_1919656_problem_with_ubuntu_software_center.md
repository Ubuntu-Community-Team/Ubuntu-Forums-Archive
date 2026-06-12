---
title: "problem with ubuntu software center"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by iamnoob on 2012-02-03
i am using ubuntu 11.04. it is showing some error while updating or installing any app from ubuntu software center. error msg is 
"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"
i am a starter plz help.

---

### Post by Bucky Ball on 2012-02-03
Welcome. You don't have any other package managers open at the same time? Update manager or anything like that?

---

### Post by iamnoob on 2012-02-03
> **Bucky Ball said:**
> Welcome. You don't have any other package managers open at the same time? Update manager or anything like that?
thank you! well no i have face almost same problem before but that time update-manager was unaffected from it. now if i go to ubuntu software center to download any app it does not go further if i click any of application type icon. i changed server but condtion was the same. no i dont open any of 2 package manager same time.

---

### Post by raja.genupula on 2012-02-03
Hi open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and let us know what you got.
All the best man.

---

### Post by iamnoob on 2012-02-03
i was experimenting and i again changed preferences of update manager to main server now its downloading package information lets what happens after downloading then i'll run the command. i'll update you soon

---

### Post by iamnoob on 2012-02-03
> **iamnoob said:**
> i was experimenting and i again changed preferences of update manager to main server now its downloading package information lets what happens after downloading then i'll run the command. i'll update you soon
after downloading now this error occured

"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

"

---

### Post by iamnoob on 2012-02-03
> **raja.genupula said:**
> Hi open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and let us know what you got.
All the best man.
thanks a lot Sir . it worked. no probs anymore with any package manager.

---

### Post by raja.genupula on 2012-02-03
Hi you welcome , please mark the thread as solved from thread tools.

Thank you .

---

### Post by iamnoob on 2012-02-04
> **raja.genupula said:**
> Hi you welcome , please mark the thread as solved from thread tools.

Thank you .
marked.. thanks. :)

---

