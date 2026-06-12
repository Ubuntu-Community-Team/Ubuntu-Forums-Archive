---
title: "libsmbclient-dev dependency issues, already tried apt-get update,"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by hexag on 2011-03-24
Hey,

I'm trying to install libsmbclient-dev, and I get this messahe...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libsmbclient-dev : Depends: libsmbclient (= 2:3.5.4~dfsg-1ubuntu8.3) but 2:3.5.4~dfsg-1ubuntu8.4 is to be installed
E: Broken packages

```

I have already run (multiple times!)...

```
sudo apt-get update
```

if i run uname -r i get...

```
2.6.37.4-candela
```

as this is a new kernel compilation, using kernelcheck, as suggested to support my XBMC setup.

I get the same error if I try installing through GUI, Synaptic Package Manager.

We're Ubuntu Ultimate Edition, 10.10, i386, nothing else complains, any ideas guys?

Thanks,
hx

---

### Post by andrewthomas on 2011-03-24
Downgrade libsmbclient to [SIZE=1]3.5.4~dfsg-1ubuntu8.3[/SIZE]

[http://packages.ubuntu.com/maverick/libsmbclient](http://packages.ubuntu.com/maverick/libsmbclient)

Then you should be able to install the package.

---

### Post by hexag on 2011-03-24
Thanks for the quick reply! Looks like it did the trick, I had just read a few places of being wary of downgrading anything, I used this command, if anyone comes here looking for a solution...

```
sudo dpkg -i --force-all {path to...}libsmbclient{version}.deb
```

Updating to solved :)

---

