---
title: "Installing libsdl1.2-dev fails"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by dom96 on 2011-08-04
Hello. I am trying to install libsdl1.2-dev. When I try to do this by typing ```
sudo apt-get install libsdl1.2-dev
``` I get the following output:
```
dominik@ubuntu:~$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed
E: Broken packages
```

How can I fix this?

---

### Post by dom96 on 2011-08-04
I believe I have found a solution. All I had to do is use `aptitude` instead of `apt-get`. Silly me.

---

