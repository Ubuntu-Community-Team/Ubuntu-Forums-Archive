---
title: "debsig-verify failing post upgrade of Ubuntu OS to 18.04"
date: 2019-01-22
forum: Installation &amp; Upgrades
---

### Post by veeruself on 2019-01-22
I have upgraded Ubuntu OS to 18.04, then debsig-veify is not working and saying below error , when I run with debug mode. 

root@VRM-VNEx5:/tmp# debsig-verify -v -d vne-upgrade.Ji1Xd8EcMj
debsig: Starting verification for: vne-upgrade.Ji1Xd8EcMj
debsig:         getSigKeyID: got 77D769012BE9A47B for origin key
debsig: Using policy directory: /etc/debsig/policies/77D769012BE9A47B
debsig:   Parsing policy file: /etc/debsig/policies/77D769012BE9A47B/vne-updates.pol
debsig:     parsePolicyFile: parsing '/etc/debsig/policies/77D769012BE9A47B/vne-updates.pol'
debsig: 3: policy name space != [https://www.debian.org/debsig/1.0/](https://www.debian.org/debsig/1.0/)
debsig:     parsePolicyFile: completed
debsig:     parsePolicyFile: 1 errors during parsing, failed
debsig: No applicable policy found.

if I remove the xmlns from the policy file (i.e *.pol) then it is started working.

---

