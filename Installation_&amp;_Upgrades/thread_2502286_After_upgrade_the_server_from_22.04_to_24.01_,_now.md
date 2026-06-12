---
title: "After upgrade the server from 22.04 to 24.01 , now the python packages are broken"
date: 2024-11-08
forum: Installation &amp; Upgrades
---

### Post by danielchau1 on 2024-11-08
Hello,

After upgrade the server from 22.04 to 24.01

# apt install python3-venv
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 python3.12-venv : Depends: python3.12 (= 3.12.3-1ubuntu0.2) but 3.12.7-1+jammy1 is to be installed
E: Unable to correct problems, you have held broken packages.

Please, would you please let me know how can I solve this?

THanks

---

### Post by ian-weisser on 2024-11-08
Looks like you installed some non-Ubuntu Python 3.12 package(s).
That's why you have an "impossible situation".

Uninstall the non-Ubuntu packages and delete the source they came from.
Restore the original Ubuntu version of Python 3.12.

---

