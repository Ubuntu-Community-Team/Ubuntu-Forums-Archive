---
title: "Package dependencies cannot be resolved error"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bpcrshooter15 on 2010-03-31
I have now been getting this error when trying to install the diagram editor, Dia, and Empathy in Lucid.  Can anyone help resolve this issue?  Ubuntu doesn't give any further info to really help solve the situation either.

---

### Post by s.fox on 2010-03-31
Hello,

Could you please try this command in terminal?

```
sudo apt-get install dia
```

Please post back the output.

-Silver Fox

---

### Post by jeffus_il on 2010-03-31
> **bpcrshooter15 said:**
> I have now been getting this error when trying to install the diagram editor, Dia, and Empathy in Lucid.  Can anyone help resolve this issue?  Ubuntu doesn't give any further info to really help solve the situation either.

There are dependency problems in the repository. The empathy problem was solved today in the repository (Main Server). It was a mismatch between versions of empathy and empathy-common. A quick solution other than waiting for the repository to be fixed is to google for the correct version in the package database. You often have to take them out of Karmic... Otherwise they come right with time, Lucid is still in Beta.

Dia is OK now!

---

### Post by bpcrshooter15 on 2010-03-31
> **jeffus_il said:**
> There are dependency problems in the repository. The empathy problem was solved today in the repository (Main Server). It was a mismatch between versions of empathy and empathy-common. A quick solution other than waiting for the repository to be fixed is to google for the correct version in the package database. You often have to take them out of Karmic... Otherwise they come right with time, Lucid is still in Beta.

Dia is OK now!

Thanks!  I've got them both up and running now.

---

### Post by libervisco on 2010-04-11
Same is happening with Mediatomb on Lucid.

```

sudo apt-get install mediatomb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mediatomb: Depends: mediatomb-daemon (>= 0.12.0~svn2018-6ubuntu1) but it is not going to be installed
E: Broken packages


```

---

