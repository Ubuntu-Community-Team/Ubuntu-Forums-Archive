---
title: "[Hoary] FreeNX Unmet dependancies"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by -DomiNator- on 2005-06-03
Ellow peepz,

when i try to use to install the freenx server using kanotix depository's, it says my dependencies don't meet. I Use a fresh installed Hoary box with all updates en upgrades.

So... Here's what i did:

* Installed Hoary
* apt-get update / upgrade
*added deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./ to my /etc/apt/sources.list
* apt-get update
* apt-get install freenx / nxserver, i get the following message:
```
root@headquarters:~ # apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: nxagent (>= 1.4.0.2) but it is not going to be installed
          Depends: nxproxy (>= 1.4.0.2) but it is not going to be installed
E: Broken packages
root@headquarters:~ #
```

So, after that i did a apt-get install nxagent, and what i got was:

```
The following packages have unmet dependencies:
  nxagent: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
           Depends: libnxcomp0 but it is not going to be installed
           Depends: libnxcompext0 but it is not going to be installed
           Depends: nxlibs but it is not going to be installed
E: Broken packages
root@headquarters:~ #
```

So.. I'm stuck and can use a little help here :) I know for sure that this worked for me the last time i installed hoary  ](*,) 

Thanx in advance :)

---

### Post by BeeZ on 2005-06-03
[QUOTE=-DomiNator-]Ellow peepz,

when i try to use to install the freenx server using kanotix depository's, it says my dependencies don't meet. I Use a fresh installed Hoary box with all updates en upgrades.

So... Here's what i did:

* Installed Hoary
* apt-get update / upgrade
*added deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./ to my /etc/apt/sources.list
* apt-get update
* apt-get install freenx / nxserver, i get the following message:
```
root@headquarters:~ # apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: nxagent (>= 1.4.0.2) but it is not going to be installed
          Depends: nxproxy (>= 1.4.0.2) but it is not going to be installed
E: Broken packages
root@headquarters:~ #
```

So, after that i did a apt-get install nxagent, and what i got was:

```
The following packages have unmet dependencies:
  nxagent: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
           Depends: libnxcomp0 but it is not going to be installed
           Depends: libnxcompext0 but it is not going to be installed
           Depends: nxlibs but it is not going to be installed
E: Broken packages
root@headquarters:~ #
```

So.. I'm stuck and can use a little help here :) I know for sure that this worked for me the last time i installed hoary  ](*,) 

Thanx in advance :)[/QUOTE]
 euh try again later? reboot ur pc, use the "sudo " command?

---

### Post by -DomiNator- on 2005-06-03
I'm upgrading to breezy now, don't know whether its a good idea or not, we'll see, i've got nothing to lose so :)

---

### Post by BeeZ on 2005-06-03
:)

---

### Post by Leif on 2005-06-03
Use the one in the backports instead of kanotix, it works fine.

---

### Post by -DomiNator- on 2005-06-03
Thanx :D Works like a charm :)

---

