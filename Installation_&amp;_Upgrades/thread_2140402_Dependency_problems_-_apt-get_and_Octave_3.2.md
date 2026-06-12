---
title: "Dependency problems - apt-get and Octave 3.2"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by Ocifer on 2013-04-29
Hello, 

I am trying to install Octave 3.2, a program for mathematics, similar to matlab. 

My apt-cache searches reveal there are a number of Octave 3.2 packages, but upon trying to install them with the following command:

```

sudo apt-get install octave

```

I get the following error message:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 octave : Depends: libarpack2 (>= 2.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Is there any way to deal with these dependency problems?

---

### Post by Ocifer on 2013-05-05
Bump. Sorry for the bump, but it's been a few days.

---

### Post by ibjsb4 on 2013-05-05
You do have your universe sources checked.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Get the same results when just installing libarpack2?

---

### Post by steeldriver on 2013-05-05
what version of ubuntu are you trying to install this in? do you have a previous version of octave or any of the arpack packages installed?

```
apt-cache policy arpack*
```

---

