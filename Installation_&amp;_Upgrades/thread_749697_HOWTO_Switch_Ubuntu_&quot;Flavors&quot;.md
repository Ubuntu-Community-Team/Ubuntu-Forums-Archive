---
title: "HOWTO: Switch Ubuntu &quot;Flavors&quot;"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Toadinator on 2008-04-08
I've just figured out how to do this and I'd like to share the info for people who need the help.

You may have been wondering how to switch to another Ubuntu 'flavor' (example: Xubuntu is a 'flavor' of Ubuntu). The good news is that you *don't* need to re-install to do this. You may need to do this if you installed Ubuntu Studio but want to upgrade to Ubuntu 8.04 instead of Ubuntu Studio 8.04.

Here's two easy and simple ways to do it:

*Note* You will be asked to remove packages when doing this. Remove them ONLY if you are installing other packages that look similar.

_POWER USER_:

If you like typing via the terminal to get work done then you can do the following:

```
$ sudo apt-get (favor in lower case)-desktop
```

There may be more packages such as (flavor)-artwork or (flavor)-sound or even (flavor)-theme and you can try to install those seperately but to find out which ones are available then see the following step.

_AVERAGE USER_:

If you know squat about the terminal or just like to use the GUI better then you should use this way. Click System-->Administration-->Synaptic Package Manager and look for your 'flavor' in lowercase. download the package with a suffix of '-desktop'. There may be ones like '-sound' or '-themes' that won't get installed with that package, so if you want to install those then go ahead.

I hope this helped and if you have any questions then feel free to post. Can someone sticky this?

---

