---
title: "gpg: no valid OpenPGP data found"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by prkhr4u on 2013-12-30
I am trying to install gstreamer-sdk for ubuntu 12.04

When i run this command:
```
wget -q -O - http://www.freedesktop.org/software/gstreamer-sdk/sdk.gpg | sudo apt-key add -
```
to install gpg keys,it gives me an error after some time:
```
gpg: no valid OpenPGP data found
```

Don't know what is GPG keys,and how to resolve this issue.

I have checked the proxy settings and both $http_proxy and $https_proxy are correctly set.

---

### Post by Bashing-om on 2014-01-01
prkhr4u; Hi !

Here is one way to get the key, and the explanation of what and why:
 
"Authentication keys" are usually obtained from the maintainer of the software repository. The maintainer will often place a copy of the authentication key on a public key server such as [www.keyserver.net](www.keyserver.net), but you need the "key hash" to find it. For instance, the PPA for Mozilla Team. If you go to its web page ([https://launchpad.net/~mozillateam/+archive/ppa](https://launchpad.net/~mozillateam/+archive/ppa)), you'll find the text snippet "Signing key: 1024R/CE49EC21"; the latter part of this is the key hash (CE49EC21).

Once the key hash is known, the key can then be retrieved using the command:

gpg --keyserver [name of keyserver] --recv-keys [keyhash] 
For instance, you could import the maintainer's authentication key, whose hash is CE49EC21, as follows:
gpg --keyserver subkeys.pgp.net --recv-keys CE49EC21 
Then, add the key to Ubuntu's apt trusted keys database with the following command:
gpg --export --armor CE49EC21 | sudo apt-key add - 
Note there's a dash at the end of the line.

There are other ways to authenticate, but this may be the more direct.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by prkhr4u on 2014-01-23
Thank you very much for the precise and lucid explanation.
I finally got it working this way (for gstreamer sdk)
The key hash I found using
 ```
sudo apt-get update
```
and came out to : 1900C4BE
then I requested the key this way:
```
gpg --keyserver http://www.freedesktop.org/software/gstreamer-sdk/sdk.gpg --recv-keys 1900C4BE
```
and finally added it to Ubuntu's key database:
```
gpg --export --armor 1900C4BE|sudo apt-key add -
```

---

### Post by Bashing-om on 2014-01-23
prkhr4u; You do good work !

Appreciate that you provided your solution.
It corroborates when others seek in a similar situation.

[INDENT]can't keep a good 
[INDENT][INDENT]operating system down
[/INDENT][/INDENT][/INDENT]

---

