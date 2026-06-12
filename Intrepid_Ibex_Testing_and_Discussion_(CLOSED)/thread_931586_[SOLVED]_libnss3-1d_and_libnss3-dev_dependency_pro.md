---
title: "[SOLVED] libnss3-1d and libnss3-dev dependency problems"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-09-27
Not even sure what these libraries do (but apparently they're dependencies of xulrunner). Anyway, to the point, they can't be upgraded in the current state because they're relying on packages that are not up yet. It's been like this for the past few days:
```
libnss3-1d:
  Depends: libnspr4-0d (>=4.7.1+1.9-0ubuntu5~) but 4.7.1+1.9-0ubuntu4 is to be installed

libnss3-dev:
  Depends: libnss3-1d (>=3.12.1~rc2) but 3.12.1~rc1-0ubuntu1~fta1 is to be installed
```

[https://bugs.launchpad.net/ubuntu/+source/nss/+bug/275217](https://bugs.launchpad.net/ubuntu/+source/nss/+bug/275217)

---

### Post by plun on 2008-09-27
"Fwiw"....

Within fta:s ppa you have newer versions

[https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)

Also Firefox 3.1....:)

---

### Post by psyke83 on 2008-09-27
> **WindowsSucks said:**
> Not even sure what these libraries do (but apparently they're dependencies of xulrunner). Anyway, to the point, they can't be upgraded in the current state because they're relying on packages that are not up yet. It's been like this for the past few days:
```
libnss3-1d:
  Depends: libnspr4-0d (>=4.7.1+1.9-0ubuntu5~) but 4.7.1+1.9-0ubuntu4 is to be installed

libnss3-dev:
  Depends: libnss3-1d (>=3.12.1~rc2) but 3.12.1~rc1-0ubuntu1~fta1 is to be installed
```

[https://bugs.launchpad.net/ubuntu/+source/nss/+bug/275217](https://bugs.launchpad.net/ubuntu/+source/nss/+bug/275217)

I've marked your bug Invalid, sorry. Bugs should not be filed against PPA packages unless you are specifically requested to do so (e.g. Luke's PulseAudio packages, other preview packages by Ubuntu developers that require extra testing).

You have two choices:
1. Wait for fta to updates his PPA and resolve conflicts, or;
2. Disable fta's repository, update your sources, and manually downgrade packages:

```
$ sudo apt-get install package1/intrepid package2/intrepid ...
```

You can probably find the packages that required downgrading by checking Synaptic's listing of "Status/Installed (Local or obsolete)" packages.

---

### Post by klange on 2008-09-27
I had synaptic set to prefer the Intrepid packages, which seems to have caused the problem.

Sorry about that ;)

---

