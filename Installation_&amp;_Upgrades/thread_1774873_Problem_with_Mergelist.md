---
title: "Problem with Mergelist"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by livetobefree on 2011-06-03
Hello,

 I know version 10.04 is no longer supported.  Unfortunately I did not update or upgrade before support for my systems' version ended.  I suspect that is most of the problem.  

When I attempt to update from Update Manager it gives these readings;

[B]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'[/B]


Is this a serious problem?  

Any solutions would be apprecitaed.

thanks

---

### Post by Rubi1200 on 2011-06-04
Hi and welcome to the forums :-)

> I know version 10.04 is no longer supported
This is simply not true; 10.04 is supported on the Desktop until April 2013.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

To fix the problem you have, do this in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by livetobefree on 2011-06-11
Hello, 
  thanks for sending me the suggestion, but it didnt work.  Got any other clues?

---

