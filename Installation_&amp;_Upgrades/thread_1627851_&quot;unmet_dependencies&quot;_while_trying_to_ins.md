---
title: "&quot;unmet dependencies&quot; while trying to install VBOX"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by OxentroT on 2010-11-21
I have just newly installed Ubuntu10.10 on my laptop and am attempting to install VirtualBox 3.2.10. Everything has been going fine until I run the apt-get install command. The results are as follows: 

```

bn0@n0v0n:~$ sudo apt-get install virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.4 is to be installed
E: Broken packages

```

Thank You to anyone who may have any sort of advise on this issue.

:guitar:

---

### Post by lmarmisa on 2010-11-21
This link could help you:

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by OxentroT on 2010-12-20
[QUOTE imarmisa]
This link could help you:

[https://help.ubuntu.com/community/Sy...ken%20packages](https://help.ubuntu.com/community/Sy...ken%20packages)
[/QUOTE]

Thank You!

Happy Holidays!

---

