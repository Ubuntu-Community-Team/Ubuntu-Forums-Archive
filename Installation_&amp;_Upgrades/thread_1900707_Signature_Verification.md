---
title: "Signature Verification"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by mobyah on 2011-12-27
When I try to update Ubuntu 11.10 I get an error of bad or invalid signature with the following GPG error BADSIG 16126D3A3E5C1192 and BADSIG 40976EAF437D05B5
I have failed to install many software for the same reasons, sometimes it says unauthenticated sources, which I don't know what to do. Someone please help

---

### Post by raja.genupula on 2011-12-27
HI man do this 

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

EDIT: Execute all the commands one by one in your termainl 

all the best

---

### Post by mobyah on 2011-12-29
Thanx Raja, now solved


> **raja.genupula said:**
> HI man do this 

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

EDIT: Execute all the commands one by one in your termainl 

all the best

---

