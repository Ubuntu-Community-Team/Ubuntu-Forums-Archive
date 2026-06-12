---
title: "cannot upgrade cupsddk package"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-08-26
When I try to upgrade it manually it says

The following packages have unmet dependencies:
  cupsddk: Depends: cups-ppdc but it is not going to be installed
E: Broken packages

And if I try to remove it it is trying to remove more packages

The following packages will be REMOVED:
  cupsddk hpijs hpijs-ppds hplip-cups

Is this package needed ?

---

### Post by timmy334 on 2009-08-26
> **jithin1987 said:**
> When I try to upgrade it manually it says

The following packages have unmet dependencies:
  cupsddk: Depends: cups-ppdc but it is not going to be installed
E: Broken packages

And if I try to remove it it is trying to remove more packages

The following packages will be REMOVED:
  cupsddk hpijs hpijs-ppds hplip-cups

Is this package needed ?

I am having the same issue.

---

### Post by steeleyuk on 2009-08-27
I've removed it with no problems using Synaptic. What I did was remove the cupsddk package and mark hpijs, hpijs-ppds, hplip-cups for reinstallation.

---

### Post by jithin1987 on 2009-08-27
> **steeleyuk said:**
> I've removed it with no problems using Synaptic. What I did was remove the cupsddk package and mark hpijs, hpijs-ppds, hplip-cups for reinstallation.

How is that going to work? hpijs has a dependency on cupsddk.

---

### Post by dino99 on 2009-08-27
yesterday i had this package & cups (if i remember well) that refused to upgrade with BUM.
So, using synaptic, i first tried to install cups &  it deal smootly with dependencies, removing some packages; then i was able to upgrade cupsddk.

---

### Post by jppr on 2009-08-27
in that case yesterday, i doing... sudo aptitude update && sudo aptitude full-upgrade... and that´s it   = )

---

### Post by steeleyuk on 2009-08-27
> **jithin1987 said:**
> How is that going to work? hpijs has a dependency on cupsddk.

Everything is working fine for me without cupsddk. cupsddk is also a transitional package to cups-ppdc, so as long as you have cups-ppdc installed it should be fine.

---

### Post by jithin1987 on 2009-08-27
aptitude full-upgrade did the trick

The following NEW packages will be installed:
  cups-ppdc{a}
The following packages will be REMOVED:
  cupsddk{a}

---

