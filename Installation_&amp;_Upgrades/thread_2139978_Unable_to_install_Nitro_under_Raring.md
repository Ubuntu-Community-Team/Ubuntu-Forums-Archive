---
title: "Unable to install Nitro under Raring"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by bugbugbugb on 2013-04-28
Hi,

I'm using Ubuntu 13.04 and trying to find a good application for taking notes. I see Nitro could meet some of my needs, but I'm unable to install it from Ubuntu Software Center. I get the "Package dependencies could not be resolved" error.

"
The following packages have unmet dependencies:
nitro: Depends: python (>= 2.7.1-0ubuntu2) but 2.7.4-0ubuntu1 is to be installed
Depends: gsettings-backend but it is a virtual package
Depends: gir1.2-launchpad-integration-3.0 but it is not going to be installed
"

I would appreciate any suggestion,
Thanks

---

### Post by darek1176 on 2013-04-28
I have the same issue. Problem with dependencies

---

### Post by darek1176 on 2013-04-28
Just found this information and tried the solution and worked for me. Nitro is on my Ubuntu 13.04
[http://askubuntu.com/questions/287360/how-to-solve-unmet-dependencies](http://askubuntu.com/questions/287360/how-to-solve-unmet-dependencies)

---

### Post by bugbugbugb on 2013-04-28
Thank you, it worked for me too.

Also, a new version of [Nitro]("https://launchpad.net/nitrotasks/trunk/1.5.1") seems to address this dependency [issue]("https://github.com/stayradiated/Nitro/issues/216"). Hope we get the update soon in Ubuntu's Software Center.

---

