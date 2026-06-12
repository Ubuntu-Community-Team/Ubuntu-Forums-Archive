---
title: "Two upgrade issues(one biggie)"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by hampton275 on 2006-06-03
I am up and running after the upgrade, with two issues;
1/ When I exit enlightenment the terminal is black. I can type commands(like startx) and it starts, so it sounds like just a display issue, but no ide where to go with that one.
2/ tetex-extra is causing me some big headaches. I am received 6 package errors at the end of the upgrade. I uninstalled/reinstalled all but one. I am unable to do a thing with tetex-extra. I tried unistalling tex-common, as listed in the forums, but it says fix tetex-extra. It will not uninstall or re-install, which also won't let me properly re-install any of the tetex* packages. I tried unistalling using the 'broken' function in Synaptic, which sees it is broken, but fails to fix it
Here is what I get when  I try;

 $ sudo apt-get remove tex-common tetex-extra
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  texinfo: Depends: tex-common but it is not going to be installed or
                    tetex-bin (< 3.0) but it is not going to be installed
E: Broken packages

---

### Post by CompShrink on 2006-06-06
Note texinfo is also complaining, try:

$ sudo apt-get remove tex-common tetex-extra **texinfo**

and see if you can go from there.

---

