---
title: "Downgrades from hardy to intrepid"
date: 2008-06-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-06-06
Hi all, 
 Look at the downgrades which happened at full-upgrade

shirish@Mugglewille:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  aptitude kcontrol kdebase-bin-kde4 kdebase-kde4 kdebase-runtime-data kicker kpat-kde4 libapt-pkg-perl 
  libept0 libffi4 python-apt synaptic 
The following packages will be REMOVED:
  kdebase-data-kde4{a} 
The following packages will be upgraded:
  apt apt-utils cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base kdebase-data libgfortran2 libstdc++6-4.2-dev 
9 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 10.3MB of archives. After unpacking 15.9MB will be freed.
The following packages have unmet dependencies:
  kcontrol: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu1 is to be installed.
  kpat-kde4: Depends: kdebase-data-kde4 but it is not installable
  kdebase-bin-kde4: Depends: kdebase-data-kde4 (= 4:4.0.4-0ubuntu1~hardy3) but it is not installable
  aptitude: Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  python-apt: Depends: libapt-inst-libc6.7-6-1.1 which is a virtual package.
              Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  kicker: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu1 is to be installed.
  libapt-pkg-perl: Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  libffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-0ubuntu2 is to be installed.
  libept0: Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  kdebase-kde4: Depends: kdebase-data-kde4 (>= 4:4.0.4-0ubuntu1~hardy3) but it is not installable
  synaptic: Depends: libapt-inst-libc6.7-6-1.1 which is a virtual package.
            Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  kdebase-runtime-data: Depends: kdebase-runtime-data-common (>= 4:4.0.80-1ubuntu1) but it is not installable or
                                 kdebase-data (< 4:4.0.0-1) but 4:4.0.80-1ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
apt [0.7.14ubuntu2 (now)]
apt-utils [0.7.14ubuntu2 (now)]
cpp-4.2 [4.2.3-2ubuntu7 (now)]
g++-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2-base [4.2.3-2ubuntu7 (now)]
kdebase-data [4:3.5.9-0ubuntu7.2 (now)]
libgfortran2 [4.2.3-2ubuntu7 (now)]
libstdc++6-4.2-dev [4.2.3-2ubuntu7 (now)]

Downgrade the following packages:
kdebase-bin-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-data-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]

Score is 294

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  kdebase-bin-kde4 kdebase-data-kde4 kdebase-kde4 
0 packages upgraded, 0 newly installed, 3 downgraded, 0 to remove and 9 not upgraded.
Need to get 839kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe kdebase-kde4 4:4.0.3-0ubuntu2 [12.7kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe kdebase-bin-kde4 4:4.0.3-0ubuntu2 [82.0kB]                     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe kdebase-data-kde4 4:4.0.3-0ubuntu2 [744kB]                     
Fetched 837kB in 46s (17.8kB/s)                                                                                  
dpkg - warning: downgrading kdebase-kde4 from 4:4.0.4-0ubuntu1~hardy3 to 4:4.0.3-0ubuntu2.
(Reading database ... 358996 files and directories currently installed.)
Preparing to replace kdebase-kde4 4:4.0.4-0ubuntu1~hardy3 (using .../kdebase-kde4_4%3a4.0.3-0ubuntu2_all.deb) ...
Unpacking replacement kdebase-kde4 ...
dpkg - warning: downgrading kdebase-bin-kde4 from 4:4.0.4-0ubuntu1~hardy3 to 4:4.0.3-0ubuntu2.
Preparing to replace kdebase-bin-kde4 4:4.0.4-0ubuntu1~hardy3 (using .../kdebase-bin-kde4_4%3a4.0.3-0ubuntu2_i386.deb) ...
Unpacking replacement kdebase-bin-kde4 ...
dpkg - warning: downgrading kdebase-data-kde4 from 4:4.0.4-0ubuntu1~hardy3 to 4:4.0.3-0ubuntu2.
Preparing to replace kdebase-data-kde4 4:4.0.4-0ubuntu1~hardy3 (using .../kdebase-data-kde4_4%3a4.0.3-0ubuntu2_all.deb) ...
Unpacking replacement kdebase-data-kde4 ...
Setting up kdebase-data-kde4 (4:4.0.3-0ubuntu2) ...
Setting up kdebase-bin-kde4 (4:4.0.3-0ubuntu2) ...
Setting up kdebase-kde4 (4:4.0.3-0ubuntu2) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


Comments and suggestions all welcome.

---

### Post by aamukahvi on 2008-06-06
> **ShirishAg75 said:**
> Downgrade the following packages:
kdebase-bin-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-data-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
hardy package versions were replaced with intrepid versions.

---

### Post by ShirishAg75 on 2008-06-06
right, that is what i am trying to get attention of people.

---

### Post by ShirishAg75 on 2008-06-06
Does anybody how to know a status of a package whether it is hardy version or intrepid version like shown above. 

> 
Downgrade the following packages:
kdebase-bin-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-data-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]
kdebase-kde4 [4:4.0.4-0ubuntu1~hardy3 (now) -> 4:4.0.3-0ubuntu2 (intrepid)]


I tried couple of commands but neither of them give this information 

aptitude show packagename 
apt-cache show packagename 

While both of these commands are same/similar they don't provide the info. I'm looking for. Any help/guidance for the same would be appreciated.

---

### Post by 23meg on 2008-06-06
```
apt-cache policy packagename
```

If you want the same thing but cross-release, look into [madison-lite]("apt:madison-lite").

---

